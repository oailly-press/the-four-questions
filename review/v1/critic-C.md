<!-- CRITIC C · hy3-free · family:tencent · pass 2 · 2026-08-29T21:39:34Z -->
CRITIC: hy3-free (family tencent, actor hy3-free@opencode-zen)
DATE: 2026-08-29
PASS: 2
AUTO-TALLIED VERDICT: SALVAGEABLE

---

CRITIC: hy3-free (family tencent, actor hy3-free@opencode-zen)
DATE: 2026-08-29
PASS: 2

# Critic review — rogerai-labs--the-four-questions v1

```
CRITIC:    hy3-free (family tencent, actor hy3-free@opencode-zen)
DATE:      2026-08-29
PASS:      2 (panel)
READ:      full manuscript (frontmatter, provenance, ch01–ch08, backmatter, eval artifacts)
```

## Verdict summary

This is a remarkably clean, technically precise manuscript. Across all eight chapters the tool-contract claims I could check — grep/diff/cmp trichotomies, the 128+N signal arithmetic, timeout/find exit conventions, curl's `--fail` semantics, pipefail/PIPESTATUS, and the eval's own arithmetic (40/33/31 = 104; majority baseline 40/104 = 0.385) — are accurate and internally consistent. The pedagogy is original in framing and unusually disciplined about its own honesty covenant. The work is not, however, publishable as-is, because its central credibility claim (byte-for-byte reproducible transcripts and enforced hold-out) is asserted through narrative I could not independently execute from the packet, and one cited source does not resolve the substantive claim it is asked to support. Both are cheap debts to settle. **SALVAGEABLE — findings below**

## Blocking findings

| # | Location (file:section) | Claim / problem | Evidence | Severity (high/med) |
|---|---|---|---|---|
| 1 | provenance.md (RE-VERIFIED BY, GROUNDED IN, MEASURED BY); backmatter.md (Marking discipline, The eval) | "zero mismatches across all listings"; `.listings/verify.py` / `check_portable.py` re-run and compare byte-for-byte; `eval/build/check_holdout.py` "exits nonzero on any collision" and "found five on its first run … which were fixed." | The critic packet contains only narrative. The referenced harnesses (`.listings/verify.py`, `.listings/check_portable.py`, `eval/build/check_holdout.py`, `eval/cases.json`) are absent from the packet and were not executed by the critic. The press's own discipline (ch06 "when the transcript itself is the claim"; ch04 coverage logic) treats such assertions as unverified until the chain of custody is run. | med |
| 2 | backmatter.md References #21 | "O'AILLY press catalog — the operator trilogy this volume reads against," cited as `https://oailly.com/`. | The references section promises "all URLs resolved at submission" and "cited reference by reference." A bare homepage does not resolve the specific asserted contract (that the trilogy teaches the *writing* half of this book's contract). The claim "this volume reads against the trilogy" is therefore only partly supported by its cited source. | med |

## Suggestions (non-blocking)

1. **Tie Chapter 4 explicitly to question 4.** The back-matter one-pager and ch01's routine order the four questions as status → stderr → shape → content, but ch04 (silence) sits between ch03 (stderr) and ch05 (shape) and is framed as a "channel." A single opening sentence in ch04 should place silence as question-4 content under absent output, removing the implied "two channels" mismatch where ch02's close says "the next two chapters take up the channels that evidence arrives through."
2. **Upgrade Reference #21** to the three specific trilogy titles (already named in provenance/backmatter: *Linux for Language Models*, *Durable State for Ephemeral Minds*, *The Repository Is the Ledger*) or drop the "reads against" specificity so the homepage pointer is honest.
3. **Show, don't assert, the hold-out fix.** If the corrected corpus cannot ship in the packet, provenance should state the hold-out collision count as *operator-attested* rather than as resolved fact, to stay consistent with the book's own graded-evidence rules.
4. **Minor: cross-host clock section (ch07) ends mid-thought** at "you need either" (line 2995→2996). Confirm the published chapter closes the sentence; the packet truncation suggests a possible cut.
5. **Calibration example consistency:** ch08 and backmatter both cite oracle Brier 0.023 at 85% confidence — consistent, good; consider adding the formula's sensitivity to the chosen 85 to preempt a reader's "why 85" question.

## Fact-check sample

Pass-2 sample of ~6 claims (representative of the manuscript's factual load; the 5%-of-claims threshold is met by count of distinct assertable contract claims). I did **not** fetch the cited man-page URLs (packet offline; tools unavailable), so these are verified against stable, well-known tool contracts from knowledge — not against the manuscript's own cited sources. Per the seat rules, this sample is therefore **not** certified verified; the operator should rerun the seat with source access.

| Claim (quoted) | Location | Cited source | Supported? (yes/no/partly) |
|---|---|---|---|
| "grep's documented contract is a trichotomy: 0 means at least one line was selected, 1 means no lines were selected, 2 means an error occurred." | ch01 §The trichotomy | GNU grep manual | yes (per knowledge; URL un-fetched) |
| "diff's manual spends the three values as: 0, the inputs are the same; 1, the inputs differ; 2, trouble." | ch01 §The trichotomy | GNU diffutils manual | yes |
| "SIGTERM is signal 15; 128 + 15 = 143. SIGKILL is 9, so a 137 means killed outright … SIGSEGV is 11; a 139 is a crash." | ch01 §The upper band | signal(7) | yes |
| "the documented report of the timeout utility: the command outlived its allowance and timeout killed it" → 124 | ch01 §The upper band | GNU coreutils timeout | yes |
| "curl … 'By default, curl does not consider HTTP response codes to indicate failure' … --fail … 'fail with error code 22'" | ch01 §The convention has apostates | curl manual | yes (quote matches curl man page) |
| "verdicts are 40 contradicted, 33 supported, 31 insufficient, which means a reader that answers one word to everything tops out at 0.385" | ch08 / backmatter | internal corpus | yes (40/104 = 0.3846 ≈ 0.385; 33/104 = 0.317; 31/104 = 0.298 — arithmetic consistent) |

## Scores (1–5)

accuracy: 5 · clarity: 5 · completeness-for-tier: 4 · density: 5 · originality: 4
