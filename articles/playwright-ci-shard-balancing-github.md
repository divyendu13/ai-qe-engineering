# Your Playwright Shards Aren't Balanced, and CI Has Been Telling You All Along

*Three CI findings from retiring a 350-test legacy e2e suite — and how to measure CI time so the number actually means something.*

---

We spent three months migrating an eight-year-old end-to-end suite — 354 tests across 38 files — from TestCafe to Playwright. That part is a different story. This one is about what the migration dragged into the light, which had nothing to do with either framework.

The setup you need: five parallel CI machines, a suite running under both frameworks during the transition, and a target of sub-30-minute PR feedback.

Partway through, I measured what we'd bought. Per test, in wall-clock terms, Playwright was **2.3x faster** than TestCafe — 6.5 seconds versus 15.1s. The framework choice was correct and the numbers were unambiguous.

And then it stalled. Wall time had come down from the pre-migration baseline, but it sat in the mid-thirties and stopped moving — and across successive runs it was drifting the wrong way, despite more of the suite landing on the faster framework every week. Per-test speed was improving. The number developers actually waited on was not.

Three things turned out to be sitting on top of the framework. None of them were visible in the CI dashboard, and none of them would have been fixed by choosing a different test runner.

---

## First: decide which quantity you're actually reducing

Before any of it made sense I had to separate three things that get casually conflated as "CI time":

- **Billed machine time** — the sum of all node durations. What your CI provider charges for.
- **Developer wait** — the duration of the *slowest* node. What actually gates a merge.
- **Idle time** — the sum over nodes of `(slowest node - that node)`. Wasted parallelism, not money.

These pull in different directions, and that's the part people get wrong. **Rebalancing work across nodes reduces developer wait while slightly increasing the bill**, because a node that finishes early stops billing. Only *removing* work improves both.

Any "we reduced CI time by X%" claim that doesn't say which of the three it means is unfalsifiable, and it will fall apart the first time someone with a spreadsheet checks it.

**A methodology trap worth passing on:** do not sum the step durations of a parallel job. One of our setup steps runs in the background, concurrently with the tests. Summing steps counted it repeatedly and produced 295 machine-minutes against a true 154 — wrong by nearly 2x. The correct measure is each node's wall time, from first step start to last step end.

---

## Second: pin your test splitting, and verify it on every run

This is the one I'd most want another team to know, because it's silent, it's specific to Playwright, and it had been costing us the entire benefit of parallelism.

Our CI distributes tests across nodes with `circleci tests split --split-by=timings`. That command matches the file paths it's given against the `file` attribute of previously uploaded JUnit reports.

**Playwright's built-in JUnit reporter does not emit `file`.** It emits `name` and `classname` only. The source comment in the reporter reads: `Skip root, project, file`, and there is no configuration option to change it.

*(True as of `@playwright/test` 1.59.1. Check before you assume it still is — this is exactly the kind of thing that gets fixed upstream.)*

Without `file`, timing-based splitting has nothing to match on, and CircleCI silently falls back to weighting by `name`. It isn't an error. It's one line in the step log:

```text
Error autodetecting timing type, falling back to weighting by name.
Autodetect no matching filename or classname.
```

And name-weighting balances test **counts**, not **durations** — which, for an e2e suite where individual tests range from two seconds to two minutes, is barely better than random.

A representative run handed the five nodes near-identical counts — **64 / 99 / 78 / 50 / 66 tests** — carrying between roughly **2.4 and 10.0 minutes** of actual work. Meanwhile the legacy framework, whose reporter did emit `file` and therefore had valid timing history, stayed inside a tight **8.5–10.8 minute** band on the very same run.

### The fix

A small custom reporter that annotates the JUnit output with each spec's absolute path. Three implementation details that matter more than the idea:

- **It runs in `onExit`,** documented as firing after every reporter has received `onEnd` — so the JUnit file is already flushed to disk when you rewrite it.
- **The rewrite is idempotent,** so reruns and retries are safe.
- **Failures are swallowed with a warning.** A reporting concern must never be able to fail a test run. If the annotation breaks, you get worse splitting, not a red build.

With paths present, `--split-by=timings` works as designed and pins each node's workload by real duration. Our node spread collapsed from **~7.6 minutes to 1.4 minutes** — effectively no idle parallelism, all five nodes finishing together, none waiting on a straggler.

### Two habits to keep

**Assert on your split diagnostics.** We now check that `Autodetected filename timings` appears on every node, and that the fallback warning appears nowhere. A silent degradation you'll have for months.

**Expect one bad run after any rename.** The timing manifest is built from previous runs, so anything that renames or moves spec files invalidates its history. The next run splits badly and self-heals on the one after. Failed runs don't record timings either, which prolongs it. Don't panic-debug that — just re-run.

---

## Third: track progress from what executes, not from what exists

We tracked the migration two ways, and the distinction turned out to be the most transferable thing I learned on the whole project.

A dashboard gave day-to-day visibility — useful for standups, for showing the shape of remaining work, for spotting untouched areas. It ended at 100% and it was genuinely good at that job.

But the number we *reported* came from parsing JUnit results: the tests that actually executed, per framework, per run. Those are answers to two different questions:

- **Do new tests exist for this area?** — the natural thing to count, and the natural thing to get wrong. It counts specs marked `fixme` or `skip`, which exist but never run.
- **Has the legacy suite actually been switched off?** — the thing you care about, and the only one that shows up in CI time.

A related trap in the same family: **grepping for a skip directive is not a safe proxy for "this file is disabled,"** because a skip applies to its own fixture rather than the whole file. A file with one active fixture beside a skipped one looks disabled and isn't.

Deriving the headline number from executed results is what let us say the legacy framework was gone and mean it — gone from CI, not merely superseded on paper. Build that measurement early. It's the difference between a progress bar and a fact.

---

## The numbers

Three different wall-clock figures appear in this post and they are not the same measurement, so let me pin them to their eras first. This is precisely the sloppiness that makes CI numbers unquotable:

| Era | e2e wall time | What was running |
|---|---:|---|
| **Before migration** | ~45 min | Legacy framework only, splitting by file |
| **Mid-migration** | 33–37 min | Both frameworks in parallel, split misconfigured |
| **After decommissioning** | ~30 min | Playwright only, timing-based split working |

The mid-migration figures are the noisy ones, and they're the ones in the table below. That table isolates **one specific change** — the split fix plus retiring superseded specs — scoped deliberately to reporting and filtering only, so no test execution behaviour changed and no new flakiness could be introduced.

| Metric | Before | After | Change |
|---|---:|---:|---:|
| Total test work (all frameworks) | 82.5m | 67.2m | **-18.5%** |
| Billed machine time | 147.8 node-min | 135.3 node-min | **-8.5%** |
| Playwright node spread | 7.6m | 1.4m | **-82%** |
| Superseded legacy specs still executing | 73 | 0 | **retired** |
| Developer wait (slowest node) | 33.6m | 36.9m | **no improvement** |

That last row is the instructive one. Developer-facing wall time did not improve *in that comparison*, because one node's cluster-provisioning wait happened to be 8.81 minutes against 6.3 at baseline. Infrastructure variance of the same order as the gains being measured — which is exactly why single-run comparisons are unsafe, and why I'm showing an era table rather than one triumphant before-and-after.

---

## Where the wall-clock win actually came from

Not from the split fix. From finishing the migration — and via a property of the two frameworks that took me embarrassingly long to appreciate.

**The legacy framework splits by file.** So per-node time cannot fall below the largest indivisible file, no matter how many machines you add. Ours was 11.4 minutes. Three files alone accounted for **77%** of all remaining legacy test time.

Retiring those three broke the floor, because Playwright parallelises across workers *within* a spec as well as across nodes. That's the structural reason "just add more machines" had stopped helping, and the structural reason finishing the migration was worth more than any further infrastructure tuning.

### What 15 minutes a run is worth

End to end, PR feedback went from about **45 minutes to about 30 — 15 minutes off every run.**

The unbilled quantity is the one worth converting into something a non-engineer can act on. We measured pipeline volume directly rather than guessing: **240 pipelines in a single month**, ranging from 3 to 71 a day.

```text
15 min saved × 240 pipelines = 3,600 min/month
                         =    60 hours/month
                         =   720 hours/year
```

**720 hours a year** of aggregate waiting-for-CI, removed from a single repository.

Two things about that number. First, our original business case had assumed 10 runs a day — measured reality was roughly 5x that on a weekday, so every estimate built on assumed volume had been understating the return substantially. **Measure your pipeline count before you model anything.**

Second, the billed side moves too, but by a different multiplier: the job runs at parallelism 5, so billed time is the **sum of five node durations** rather than the wall clock. Retiring an entire framework removes work rather than redistributing it, which is why this particular change shows up in both columns — but a claim that doesn't specify which quantity it reduces will not survive scrutiny.

---

## What isn't fixable by test work

Worth stating plainly, because it bounds anything you promise a stakeholder.

Every node pays roughly **14.2 minutes of fixed overhead** before a single test result exists:

```text
Attaching workspace                    0.4m
Install dependencies for local cluster 1.8m
Wait for cluster and services ready    6.2m – 8.9m
Test-environment deployment           ~2.0m
Browser install                        ~0.6m
Compile and misc                       ~1.5m
```

Two observations.

The deployment step installs the same fixtures independently on all five nodes — pure duplication, paid five times. And **cluster wait alone varies by 2.7 minutes run to run**, which is the same order of magnitude as most of the improvements you'll be chasing. That variance is why single-run comparisons mislead.

At 14.2 minutes of unavoidable per-node cost, our original projection of a 15-minute suite was never reachable by *any* framework choice. The realistic floor for this architecture is around **26 minutes**. Sub-20 would require changing how the environment is provisioned, or moving to test selection on PRs with the full suite on merge — which is a coverage-policy decision, not a technical one.

So the target we committed to was **sub-30**, not the 15 the original business case implied. Committing to a number bounded by your actual architecture and hitting it beats committing to an aspirational one and explaining the miss — and that conversation is much easier to have *before* the migration than after.

---

## What I'd tell someone debugging their own pipeline

**Read your CI's own warnings.** The single largest problem here printed a diagnostic on every run for months. Nobody read it, because it wasn't an error and the build was green.

**Use a control group.** An early theory that one node suffered a platform-level penalty was disproved by running the same suite in a second repository that lacked the suspected cause. Once splitting worked, a different node became the slowest — so the pattern had been a symptom of the broken split concentrating heavy work, not a property of the node. Distributed-systems debugging habits apply to CI pipelines far more than people expect.

**Say which quantity you reduced.** Billed time, developer wait, and idle time are three different numbers that move independently and sometimes in opposite directions.

**Never conclude from one run.** If your infrastructure variance is 2.7 minutes and your improvement is 2 minutes, a single comparison tells you nothing at all.

**Separate the framework's merits from your pipeline's behaviour.** Playwright was 2.3x faster per test from the first day it ran. That stayed invisible in wall-clock terms until the split was pinned and the fixed overhead was accounted for — neither of which a framework choice touches. Both facts were true simultaneously, and a migration write-up that only reports the flattering one leaves its reader unable to predict what they'll get.

---

*The companion post covers the migration itself — how an agent loop wrote the first draft of 55,000 lines of Playwright tests, and why the harness mattered more than the AI.*
