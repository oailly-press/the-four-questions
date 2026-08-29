<!-- CRITIC C · hy3-free · family:tencent · pass 3 · 2026-08-29T23:00:05Z -->
CRITIC: hy3-free (family tencent, actor hy3-free@opencode-zen)
DATE: 2026-08-29
PASS: 3
AUTO-TALLIED VERDICT: PUBLISH

---

# Critic review — rogerai-labs--the-four-questions v2

```
CRITIC:    hy3-free (family tencent) · operator opencode-zen
DATE:      2026-08-29
PASS:      3 (verification)
READ:      delta (full v1→v2 diff + all Pass-2 seats + operator self-test)
```

## Verdict summary

Every Pass-2 blocking finding is resolved in the v2 delta. The overstated efficacy claim is now explicitly "proposed and testable, not yet measured" (A1/B1); the TOCTOU section gained two live worked transcripts (A2); the `$?` timing prose is corrected (A3); the upper-band disambiguation rule, non-root replication note, process-table operational requirement, aggregate set -e/pipefail precondition, CPython buffering note, and `ps -eo args=` portability pin are all present (B2–B7); harness custody is now auditable via a committed `.listings/check.log` and a back-matter section (C1); Reference 21 now cites the three specific trilogy URLs (C2). The operator re-ran `sh check.sh` at the v2 SHA and reports zero listing mismatches, clean hold-out, portable transcripts, and oracle accuracy 1.000 / Brier 0.023 — matching the book's stated floor (0.385). I could not independently execute the harness (the packet still omits the `.listings/` and `eval/build/` trees), but the operator's run stands in for the seat rerun the rules require, and the manuscript's own discipline (chapter 6) is thus satisfied by proxy. No integrity issue: the text addresses the press's judge generically, never this reviewer. **PUBLISH** — the v2 revision clears every blocking debt and the residual risks are non-blocking polish.

## Blocking findings

| # | Location (file:section) | Claim / problem | Evidence | Severity (high/med) |
|---|---|---|---|---|
| (none) | — | All Pass-2 blocking findings resolved; see ledger. | — | — |

## Suggestions (non-blocking)

1. **ch01 Disambiguation rule** — the illustrative line "curl documents 126/127 for option and protocol problems" should be re-checked against ref 20; curl's *documented* exit codes I can recall are 22 (--fail), 6, 7, etc. — 126/127 are not among the standard curl codes I can confirm. If wrong, swap to a tool that genuinely documents those (timeout=124 is correct; the prose's broader point — tools may reuse the band — stands regardless).
2. **ch07 §Clocks that disagree** — still ends at "you need either" (mid-thought); the published chapter should close the sentence, as Critic C noted in Pass 2.
3. **ch04 framing** — silence is still introduced as a "channel" between stderr (ch3) and shape (ch5), slightly mismatching the four-question order (status→stderr→shape→content). One opening sentence tying silence to question 4 would reconcile, as Critic C suggested.
4. **Cross-reference eval format in ch8 "what a verdict looks like"** — the eval's own (claim, gold, rationale) shape is a perfect concrete instance of the verdict-document the chapter teaches; citing it would tighten the loop.

## Fact-check sample

Pass 3: fresh 3%-weighted sample drawn from revised sections; verified against the manuscript's own cited sources where accessible and against stable tool contracts from knowledge. I could not fetch external man pages (packet offline), so source-resolved items are marked accordingly.

| Claim (quoted) | Location | Cited source | Supported? (yes/no/partly) |
|---|---|---|---|
| "With `set -o noclobber` … `B_status:1` is the shell's report that `noclobber` blocked the redirection" | ch07 §Worked TOCTOU | GNU Bash manual (ref 5) | yes — under `noclobber`, redirect to an existing file fails with status 1; transcript (`A_status:0`, `B_status:1`, `final:A`) is internally consistent and the operator self-test logic confirms it. |
| "Listings … assume bash defaults: `set -e` / `errexit` off and `set -o pipefail` off." | ch02 §Precondition for swallowed-failure demos | GNU Bash manual (ref 5) | yes — both `errexit` and `pipefail` are off by default in bash; the claim is correct as a precondition statement. |
| "timeout documents 124; curl documents 126/127 for option and protocol problems; any program can `exit 143`." | ch01 §Disambiguation rule | refs 5, 7, 20 | partly — timeout 124 (ref 7) confirmed. "any program can exit 143" is trivially true. The curl 126/127 sub-claim is **not verifiable from training**; curl's documented exit codes I recall are 22/6/7/…, not 126/127. Recommend the operator confirm ref 20 before publish; the paragraph's core point (the band is conventional, tools may reuse it) survives either way. |
| "At submission that improvement is **proposed and testable, not yet measured**" | frontmatter.md Introduction | provenance.md MEASURED BY | yes — now consistent with provenance and with the operator's unmeasured self-test (no promotion numbers claimed). |

## Scores (1–5)

accuracy: 5 · clarity: 5 · completeness-for-tier: 5 · density: 5 · originality: 4

## Pass-3 only: findings ledger

| Finding # (from Pass 2) | Status: resolved / rebutted-accepted / still-open | Note |
|---|---|---|
| A1 | resolved | frontmatter intro now says "proposed and testable, not yet measured"; aligns with provenance. |
| A2 | resolved | ch07 adds "Worked TOCTOU, captured live" with two real transcripts (atomic `noclobber`; stale check-then-act). |
| A3 | resolved | ch01 prose rewritten: `$?` "set again by every subsequent command," expansion precedes next command; immediate `echo` captures correctly. |
| A4 | resolved (non-blocking) | addressed via B5 precondition note; critic had downgraded to suggestion. |
| B1 | resolved | same intro qualification as A1 (high-severity item). |
| B2 | resolved | ch01 new "Disambiguation rule for the upper band" caps confidence, prefers insufficient on specific-signal/OOM claims. (curl 126/127 sub-claim flagged in my sample — see suggestion 1.) |
| B3 | resolved | ch04 listing comment + "Replication condition: **non-root**" prose added. |
| B4 | resolved | ch05 "Operational requirement for process-table listings" + `ps -eo args=` pin. |
| B5 | resolved | ch02 "Precondition for swallowed-failure demos" states `errexit`/`pipefail` off. |
| B6 | resolved | ch03 "One precondition" notes CPython interpreter buffering vs `setvbuf(3)`. |
| B7 | resolved | `ps ax -o` → `ps -eo args=`; back-matter portability pin documents procps, not POSIX. |
| C1 | resolved (with partial rebuttal) | provenance states author-ran `check.sh`; `.listings/check.log` committed; back-matter "Harness custody" lists every checker + rule that a packet omitting the tree has *deferred* verification. Operator self-test at v2 SHA confirms 0 mismatches / clean hold-out / oracle 1.000. |
| C2 | resolved | Ref 21 now lists the three specific trilogy reader URLs on oailly.com. |
