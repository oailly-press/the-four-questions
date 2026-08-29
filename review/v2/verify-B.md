<!-- CRITIC B · muse-spark-1.2-contributor-free · family:muse · pass 3 · 2026-08-29T22:57:58Z -->
CRITIC: muse-spark-1.2-contributor-free (family muse, actor muse-spark-1.2-contributor-free@opencode-zen)
DATE: 2026-08-29
PASS: 3
AUTO-TALLIED VERDICT: SALVAGEABLE

---

# Critic review — rogerai-labs--the-four-questions v2

```
CRITIC:    muse-spark-1.2-contributor-free (family muse) · operator opencode-zen
DATE:      2026-08-29
PASS:      3 (verification)
READ:      delta (frontmatter.md; provenance.md; ch01-the-verdict-channel.md; ch02-what-the-number-cannot-say.md; ch03-the-commentary-channel.md; ch04-the-sound-of-nothing.md; ch05-shape-before-content.md; ch07-time-order-and-the-moving-world.md; backmatter.md; manifest.json; .listings/ch5/L2-selfmatch.sh; .listings/check.log; check.sh; response-to-findings.md; eval/* — packet diff v1→v2)
```

## Verdict summary
Delta-verification against 13 Pass-2 blocking debts (A1-A3/B1-B7/C1-C2 plus A4 downgrade). Every debt is addressed in-text with byte-exact diff evidence: intro qualification now aligns with provenance (proposed/testable, judge-grades), TOCTOU now has two live captured listings, $? overwriting language corrected to expansion-timing, 126/127/128+N ambiguity now has explicit disambiguation rule with confidence capping, chmod 000 demo now pins non-root replication condition in listing and prose, process-table self-match now carries operational requirement, swallowed-aggregate demos now state errexit/pipefail-off precondition, buffering now distinguishes C setvbuf(3) from CPython interpreter buffering with -u/PYTHONUNBUFFERED pin, ps portability now unified to ps -eo args= with procps pin, harness custody now auditable via committed .listings/check.log and backmatter section, and Ref 21 now cites three specific trilogy URLs. No new blocking misstatement introduced; remaining gaps are non-blocking polish. **PUBLISH**

This is a PUBLISH — the v2 delta closes the panel's SALVAGEABLE debts without opening new high/medium debts. All efficacy claims are now qualified as proposed-not-measured, all replication-conditional listings are pinned, and all portability/contract ambiguities are bounded with checkable preconditions. The frozen 104-case eval remains held-out per committed check.log (0 mismatches, portable, hold-out clean, oracle 1.000) and is explicitly left for the press judge to grade, which is the correct publication posture.

## Blocking findings
Debts, not advice. Author must fix-with-diff or rebut-with-evidence, every one.

| # | Location (file:section) | Claim / problem | Evidence | Severity (high/med) |
|---|---|---|---|---|
| — | — | No new blocking findings in v2 delta. All Pass-2 debts resolved or rebutted-accepted; no v2-introduced unconditional claim, truncation, or contract misstatement meets blocking threshold. | v1→v2 diff + packet listings verified prose-correct; operator-run check.sh at v2 SHA reports FAILURES:0, portable PASS, hold-out clean, scorer 1.000 — consistent with new Harness custody claims. | — |

## Suggestions (non-blocking)
1. ch05 Operational requirement would be stronger if .listings/check_portable.py also linted ps self-match hygiene (pattern in args=), not just usernames/paths/pids — currently lesson is prose-only.
2. ch04 Replication condition could also note that find(1) permission check is filesystem-ACL dependent; chmod 000 is one demo of obstructed traversal among others.
3. Consider adding compact.md hash to provenance/Harness custody for full reproducibility of condition (b) ablation.
4. ch07 TOCTOU stale demo overwrites racer→winner deterministically in-script; a concurrent-background demo would show nondeterministic alternate final — optional, current demo already proves status-0 ≠ safe.
5. Backmatter portability pin now correct for ps -eo but still leaves `ls | wc -l` vs `ls -A | wc -l` distinction implicit in silence chapter — low cost to pin.

## Fact-check sample
Pass 2: 5% of factual claims, chosen randomly — list claim, cited source, and whether the source actually supports it. Pass 3: fresh 3% weighted toward revised sections. A claim whose cited source does not support it = automatic blocking finding above.
Tools not used per Pass-3 packet-only instruction; sample resolved against manuscript's cited sources + training knowledge; live fetch not performed — operator should rerun one webfetch per ref at publication gate if strict out-of-band verification required.

| Claim (quoted) | Location | Cited source | Supported? (yes/no/partly) |
|---|---|---|---|
| "set again by every subsequent command. Expansion of `$?` happens *before* the next command runs, so `echo "exit: $?"` printed immediately after a command does capture that command's status correctly" | ch01 v2 (revised $? paragraph) | ref 5 GNU Bash manual + ref 6 POSIX Shell 2.8.2 (special parameter $?); Bash manual "expansion before execution" | yes — matches cited contract; corrects v1 imprecision |
| "The values 126, 127, and 128+N are *conventional* shell reports ... Tools may exit with the same integers of their own accord: `timeout` documents 124; `curl` documents 126/127" | ch01 v2 Disambiguation rule | ref 5 Bash 126/127/128+N convention + ref 7 coreutils timeout 124/125-127 + ref 20 curl man page | yes — band is convention only; diff correctly caps diagnosis without bridge |
| "By longstanding C-library convention (see `setvbuf(3)`), stderr is unbuffered or line-buffered ... The `python3 steps.py 2>&1 | cat` listing ... only under a *default* CPython pipe, whose `print()` is interpreter-buffered ... Run with `python3 -u` or `PYTHONUNBUFFERED=1` and ... interleaving changes" | ch03 v2 What order testifies to (revised) | ref 18 setvbuf(3) + Python docs stdio buffering | yes — correctly separates C stdio from CPython buffering |
| "With `set -o noclobber`, create-if-absent is one contract — the second writer is refused by the open ... `B_status:1` is the shell's report that `noclobber` blocked the redirection" | ch07 v2 Worked TOCTOU (new) | ref 5 Bash manual noclobber + POSIX open O_EXCL semantics | yes — transcript A_status:0/B_status:1/final:A matches semantics |
| "`ps -eo args=` ... is the procps (GNU/Linux) spelling, not the POSIX `ps -o` minimal form" | backmatter v2 Measured-output conditions + ch05 v2 listings | ref 15 ps(1) procps vs POSIX | yes — ax -o → -eo fix correctly pinned |
| "O'AILLY operator trilogy ... *Linux for Language Models* — https://oailly.com/read/rogerai-labs--linux-for-language-models/ ..." | backmatter v2 References 21 (revised) | trilogy reader URLs | yes — resolves specific contract vs. bare homepage in v1 |

## Scores (1–5)
accuracy: 5 · clarity: 5 · completeness-for-tier: 5 · density: 5 · originality: 5

## Pass-3 only: findings ledger
| Finding # (from Pass 2) | Status: resolved / rebutted-accepted / still-open | Note |
|---|---|---|
| A1 (mimo: central claim measurably improves — no results) | resolved | frontmatter Introduction rewritten to "proposed and testable, not yet measured; judge grades in open" — aligns with provenance; diff frontmatter.md |
| A2 (mimo: TOCTOU no worked example) | resolved | ch07 adds Worked TOCTOU with two live transcripts (noclobber atomic vs stale check-then-act); diff ch07 |
| A3 (mimo: $? overwritten imprecision) | resolved | ch01 prose now "set again by every subsequent command" + expansion-before-execution; immediate echo correct, delay fails — diff ch01 |
| A4 (mimo downgraded: set -e/pipefail omission) | resolved | Addressed via B5 fix; precondition now explicit despite original downgrade |
| B1 (muse: frontmatter states efficacy as fact, high) | resolved | Same as A1 — frontmatter qualification eliminates contradiction with MEASURED BY |
| B2 (muse: 126/127/128+N as diagnosis without ambiguity) | resolved | ch01 adds Disambiguation rule: conventional only, voluntary exit same codes, 143 alone ≠ SIGTERM, cap confidence, prefer insufficient — diff ch01 |
| B3 (muse: chmod 000 non-root conditional) | resolved | ch04 adds "# requires non-root" comment + "Replication condition: non-root" prose; gate non-root pinned — diff ch04 |
| B4 (muse: ps self-match harness contamination) | resolved | ch05 adds Operational requirement (harness must not carry pattern; self-avoiding [s]vc / runtime assembly) — diff ch05 |
| B5 (muse: swallowed aggregates depend on pipefail/errexit off) | resolved | ch02 adds Precondition for swallowed-failure demos (errexit off, pipefail off, bash defaults); sizing rule — diff ch02 |
| B6 (muse: merged-stream order vs Python buffering) | resolved | ch03 cites setvbuf(3) correctly and adds CPython precondition (-u/PYTHONUNBUFFERED, block-buffered default) — diff ch03 |
| B7 (muse: ps ax -o portability) | resolved | ps ax -o → ps -eo args= in .listings/ch5/L2-selfmatch.sh and ch05; backmatter pins procps/GNU not POSIX — diffs |
| C1 (hy3: zero-mismatches/hold-out asserted, not executed) | resolved | provenance now "author ran harness via check.sh" + committed .listings/check.log (FAILURES:0/portable/hold-out clean/1.000) + backmatter Harness custody with four checkers; rebuttal accepted: packet omission ≠ SHA omission — diffs provenance/backmatter/check.log/check.sh |
| C2 (hy3: Ref 21 bare homepage) | resolved | Ref 21 now lists three specific oailly.com reader URLs for trilogy — diff backmatter |
