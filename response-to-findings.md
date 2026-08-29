# Response to Pass-2 findings — rogerai-labs--the-four-questions v1 → v2

Panel: SALVAGEABLE × 3 (xiaomi/mimo, muse, tencent/hy3). Every blocking finding
below is answered as **fixed** (with the substance of the diff) or **rebutted**
(with evidence). Suggestions are acknowledged; only blocking debts were required.

## Critic A (mimo-v2.5-free · xiaomi)

| # | Status | Answer |
|---|---|---|
| A1 | **Fixed** (paired with B1) | Front matter Introduction no longer states the curriculum “measurably improves” as a demonstrated fact. It now says the improvement is **proposed and testable, not yet measured**, and that the judge grades the exam. Provenance already said this; the intro is aligned. |
| A2 | **Fixed** | ch07 “gap between checking and using” now carries a **worked TOCTOU** with live transcripts: (1) atomic `noclobber` exclusive create (A wins, B refused); (2) stale check-then-act that writes on an old “absent” observation after a concurrent create. |
| A3 | **Fixed (with rebuttal)** | The book's *practice* was already correct — every listing uses `echo "exit: $?"` on the same line, which the shell expands before the next command runs, so the intended status is captured (evidence: ch01 listings 1–5, all re-executed byte-for-byte by `.listings/verify.py`). The single word "overwritten" was the imprecise part. ch01 prose is rewritten to say `$?` is *set again by every subsequent command* and that expansion happens *before* the next command runs, so an immediate `echo "exit: $?"` is correct; what fails is delay by an intervening command, not inherent corruption. |
| A4 | **Accepted as non-blocking** (critic downgraded) | Still addressed under B5: swallowed-failure demos now state the `set -e` / `pipefail` off precondition explicitly. |

## Critic B (muse-spark-1.2-contributor-free · muse)

| # | Status | Answer |
|---|---|---|
| B1 | **Fixed** | Same intro qualification as A1 (high severity). |
| B2 | **Fixed** | ch01 upper band: new **Disambiguation rule** — 126/127/128+N are conventional, tools may exit the same integers voluntarily; `143` alone cannot prove SIGTERM; cap confidence without a bridge; prefer insufficient on specific-signal/OOM claims. |
| B3 | **Fixed** | ch04 vault/`chmod 000` demo: comment in listing + prose **Replication condition: non-root** (root traversal would contradict the lesson). |
| B4 | **Fixed** | ch05: **Operational requirement for process-table listings** — harness must not carry the pattern in its own `args=`; assemble at runtime / self-avoiding patterns. Listings pinned to `ps -eo args=` (procps). |
| B5 | **Fixed** | ch02: **Precondition for swallowed-failure demos** — `errexit`/`pipefail` off (bash defaults); claims that “exit 0 means the aggregate was fine” must size against option state. |
| B6 | **Fixed** | ch03: **CPython note** — `print` under a pipe is interpreter-buffered; not fully described by `setvbuf(3)`; use `python3 -u` / `PYTHONUNBUFFERED=1`; listing assumes default CPython pipe. |
| B7 | **Fixed** | `ps ax -o` → `ps -eo args=` throughout; back matter **Portability pin (process table)** documents procps/GNU, not pure POSIX. |

## Critic C (hy3-free · tencent)

| # | Status | Answer |
|---|---|---|
| C1 | **Fixed + partial rebuttal** | The harnesses were in the tree at the v1 SHA all along (`.listings/verify.py`, `.listings/check_portable.py`, `eval/build/check_holdout.py`, `eval/cases.json`); they were absent from the *critic packet*, not from the submission. v2 makes the claim auditable rather than asserted: (a) **provenance** now states zero mismatches as the result of an **author-run** of the in-tree harness via `check.sh` at this SHA; (b) a committed run log at **`.listings/check.log`** records that run (verify 0 failures, portable, hold-out clean, oracle accuracy 1.000); (c) back matter adds a **Harness custody** section listing every checker, the `check.sh` entry point, and the rule that a packet omitting the tree has *deferred* verification, not falsified it. **Rebuttal piece:** a packet's omission of harness files is not evidence the harnesses are absent from the submission SHA — they are re-run against the repository tree, which is what chapter 6 asks of any transcript that is itself the claim. |
| C2 | **Fixed** | Reference 21 no longer cites only `https://oailly.com/`. It lists the three trilogy reader URLs on oailly.com that carry the writing-side contract this volume reads against. |

## Gate

Local Pass-1 at this revision: **PASS — 0 reject**, measured body 26,211 words
(pocket tier), manifest chapter counts re-synced to the gate's counter. All
in-tree self-checks pass at this SHA (`sh check.sh`: verify 0 mismatches,
transcripts portable, hold-out clean, oracle accuracy 1.000); the run is
committed at `.listings/check.log`. The shipped eval is unchanged (104 cases,
still passes its self-test).

## Not done in this cycle (by design)

- Running the promotion eval (none/compact/book) and publishing accuracy/Brier
  numbers — still the judge’s exam; the book continues to refuse author-graded
  results.
- Non-blocking suggestions (TOC entry polish, denser commentary examples, etc.)
  unless they fell out of a blocking fix.
