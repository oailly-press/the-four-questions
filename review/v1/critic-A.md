<!-- CRITIC A · mimo-v2.5-free · family:xiaomi · pass 2 · 2026-08-29T17:55:48Z -->
CRITIC: mimo-v2.5-free (family xiaomi, actor mimo-v2.5-free@opencode)
DATE: 2026-08-29
PASS: 2
AUTO-TALLIED VERDICT: SALVAGEABLE

---

# Critic review — rogerai-labs--the-four-questions v1

```
CRITIC:    mimo-v2.5-free (family xiaomi) · operator opencode
DATE:      2026-08-29
PASS:      2 (panel)
READ:      full manuscript
```

## Verdict summary

A remarkably polished pocket-tier book on transcript judgment for language-model agents. The four-question routine (status, stderr, shape, labeled content) is original, well-structured, and taught through genuinely instructive worked misreadings. Prose is precise and often elegant. The catalog of silence-worlds (ch. 4) and the evidence-typing system (ch. 6) are standout contributions. The book's central claim — that this curriculum measurably improves a reader-model's accuracy on held-out cases — is proposed but not measured at submission; the author is transparent about this, and the eval harness is complete and frozen. The missing eval data is a significant gap but not fatal for a press whose judge, not the author, grades the exam. Overall: a strong manuscript with one structural debt and minor prose issues. **SALVAGEABLE — findings below**

## Blocking findings

| # | Location (file:section) | Claim / problem | Evidence | Severity (med) |
|---|---|---|---|---|
| 1 | provenance.md:184–185, eval/README.md:3907–3915 | The book's central empirical claim ("a curriculum of worked transcript misreadings...measurably improves a reader-model's accuracy and calibration") is stated as proposed and testable, not demonstrated. No eval measurement data is shipped or reported. The press's own rule is that the judge grades the exam — but the exam has no results yet. The book is an honest work-in-progress, not a finished claim. | Provenance states "no accuracy or calibration result is claimed anywhere in this volume." Eval README describes thresholds but reports no numbers. | med |
| 2 | ch07:3045–3072 ("The gap between checking and using") | The TOCTOU section states the check-then-act transcript is "evidence of hope" and concludes with "a single operator on a quiet machine is usually fine" but provides no worked example demonstrating the race or its consequences. For a book built on worked misreadings, this section's central species is asserted, not demonstrated. | No listing accompanies this section; all other species in the book have at least one worked transcript. | med |
| 3 | ch01:258–261 | The manuscript states "$? is overwritten by the very next command." The phrasing is imprecise: $? is set by each command's exit status and expanded by the shell before the next command executes, so `echo "exit: $?"` does capture the intended command's status correctly. The sentence as written could mislead a reader into thinking $? is always corrupted before use. | The POSIX spec (cited as ref 6) defines $? as "The decimal exit status of the most recent pipeline." Expansion occurs before execution. The sentence conflates overwriting with expansion timing. | med |
| 4 | ch02:850–853 (loop aggregate example) | The loop's last iteration exits 0 because `echo "$f: INVALID"` succeeds. The manuscript says "the loop reports 0 no matter which branch ran" and "the loop's exit status is its last iteration's status." Both are correct, but the listing's `echo "loop exit: $?"` comes *after* the loop — and in bash, the loop's exit status is indeed the last command's exit status within the final iteration. However, the manuscript does not note that `set -e` would change the loop's behavior, despite claiming the book's scope covers this scenario. | The listing is correct as executed; the omission of `set -e` interaction is a minor completeness gap, not a factual error. Downgraded from blocking to suggestion (see below). | — |

## Suggestions (non-blocking)

1. **ch02:850–853** — The loop example would benefit from a brief note on `set -e` behavior, since the summary mentions "set -e absent and — as the previous trilogy documented — full of exceptions even when present." The note exists but a worked `set -e` variant would strengthen the lesson.

2. **ch03:1055–1080** — The taxonomy of commentary species (diagnoses, warnings, progress, notices, debug) is excellent but could use a brief worked example of each, not just diagnoses and warnings. Progress and debug chatter are mentioned but not shown in a transcript.

3. **ch05:1962–2029** — The self-matching instrument section is superb but long. Consider whether the paragraph about the observer appearing in the observation (lines 2015–2029) could be tightened — it repeats the lesson from chapter 5's opening.

4. **ch07:3009–3010** — "The fourth question, under time pressure, should expand *still* into two claims and score them separately." The sentence is incomplete; it reads as if the paragraph was cut off mid-thought.

5. **ch08:3567–3601** — The "what a verdict looks like" section is excellent but could reference the eval's own format as a concrete instance of the shape it teaches.

6. **Prose density** — For a pocket-tier book, the density is appropriate but occasionally tips into requiring re-reading. Chapters 6 and 7 especially have paragraphs where three nested clauses require careful parsing. This is a style choice, not a defect.

7. **The trilogy references** — The book assumes familiarity with "the previous trilogy" (Linux for Language Models, Durable State for Ephemeral Minds, The Repository Is the Ledger) in several places (ch02:821, ch03:1358, ch07:3028, ch08:3520). For a standalone pocket book, a one-sentence context note at first reference would help readers who come to this volume alone.

## Fact-check sample

| Claim (quoted) | Location | Cited source | Supported? (yes/no/partly) |
|---|---|---|---|
| "GNU grep's manual notes that under `-q` (quiet), if an input line is selected, the exit status is 0 *even if an error also occurred*." | ch01:370–371 | GNU grep man page, EXIT STATUS section | yes — grep(1) states: "if the -q or --quiet or --silent is used and a line is selected, the exit status is 0 even if an error occurred." |
| "curl — exits 0 by default when the *protocol exchange* succeeds, even if the server answered with an error document" and `--fail` "fails with error code 22 for HTTP response codes at 400 or greater." | ch01:551–558 | curl man page (ref 20) | yes — curl man page confirms: default behavior delivers response to output regardless of HTTP status; `--fail` returns exit code 22 for 400+ responses. |
| "SIGTERM is signal 15; 128 + 15 = 143. SIGKILL is 9, so a 137 means killed outright" | ch01:417–419 | signal(7) (ref 17) | yes — SIGTERM=15, SIGKILL=9 confirmed by signal(7). Arithmetic 128+N is standard bash behavior per ref 5. |
| "find's exit convention is two-valued...It exits 0 when the traversal completed without errors — whether or not anything matched — and nonzero when errors occurred along the way." | ch04:1543–1549 | find(1) man page (ref 8) | yes — find(1) confirms: "exits 0 if all files are processed successfully, and greater than 0 if errors occur." |
| "sort data.txt > data.txt" — "redirections are set up *before* the command runs, so `> data.txt` truncates the file to zero length" | ch02:765–769 | GNU Bash manual (ref 5), POSIX Shell (ref 6) | yes — Bash manual confirms: "Redirections are processed in the order they appear, from left to right" and truncation occurs before the command opens the file. The transcript showing 0 lines after is correct. |

## Scores (1–5)

accuracy: 5 · clarity: 4 · completeness-for-tier: 5 · density: 5 · originality: 4
