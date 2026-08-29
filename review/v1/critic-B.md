<!-- CRITIC B · muse-spark-1.2-contributor-free · family:muse · pass 2 · 2026-08-29T21:37:36Z -->
CRITIC: muse-spark-1.2-contributor-free (family muse, actor muse-spark-1.2-contributor-free@opencode-zen)
DATE: 2026-08-29
PASS: 2
AUTO-TALLIED VERDICT: SALVAGEABLE

---

CRITIC: muse-spark-1.2-contributor-free (family muse, actor muse-spark-1.2-contributor-free@opencode-zen)
DATE: 2026-08-29
PASS: 2

# Critic review — the-four-questions v1

```
CRITIC:    muse-spark-1.2-contributor-free (family muse, actor muse-spark-1.2-contributor-free@opencode-zen)
DATE:      2026-08-29
PASS:      2 (panel)
READ:      full manuscript
```

## Verdict summary
The manuscript is a technically strong, unusually honest pocket volume that executes its narrow contract — teaching transcript judgment via four ordered questions — with live transcripts, disciplined terminology (supported/contradicted/insufficient, observation/inference/assertion), and a frozen, regenerable eval. The pedagogy is coherent, the examples are well-chosen, and the provenance/eval transparency is best-in-class for the series. Material accuracy is high and reproducible under stated gate conditions, but a small number of unconditional efficacy and portability claims, plus underspecified applicability conditions for permission- and signal-dependent listings, require correction before publication. **SALVAGEABLE — findings below**

## Blocking findings

| # | Location (file:section) | Claim / problem | Evidence | Severity (high/med) |
|---|---|---|---|---|
| 1 | frontmatter.md:Introduction | States as fact that the four-question curriculum "measurably improves a reader-model's accuracy and calibration on held-out transcript-judgment cases" | provenance.md:MEASURED BY and ch08:The eval, shown to its subject explicitly state no accuracy/calibration result is claimed anywhere, central claim is proposed and testable not demonstrated; promotion measurement pending judge. Intro lacks qualification and contradicts stated condition (b) remains unmeasured at submission. | high |
| 2 | ch01-the-verdict-channel.md:The upper band | Presents 126/127/128+N band as shell-identifier of death while noting only in passing that tools may exit same codes voluntarily; text still invites reader to diagnose 137=SIGKILL as OOM without stating ambiguity | `bash` manual (ref 5) reserves 126/127/128+N "by convention" only; `curl`, `timeout`, and other tools document intentional exits 124/126/127. Transcript `terminated: 143` alone cannot distinguish SIGTERM from voluntary `exit 143`. Fix requires explicit disambiguation rule and confidence capping, not just honest-note. | med |
| 3 | ch04-the-sound-of-nothing.md:The calm face of no-permission + ch08 eval family E-03 | `chmod 000 vault` + `find vault` obstruction demonstration is replication-conditional on non-root | Gate condition `non-root` is stated in frontmatter/provenance and in harness `runner.py` (`HOME` tmp, `PATH=/usr/bin:/bin`) but not in chapter prose beside the listing. Run as root (default in many CI/operator shells) `find` succeeds, exit 0, silence is not reproduced; listing would then contradict lesson. Must pin condition in listing or chapter. | med |
| 4 | ch05-shape-before-content.md:The instrument that sees itself + .listings/check_portable.py | Process-table self-match demonstration is fragile to harness contamination already documented as authorial defect | provenance.md records first capture produced 3 matches including composing shell; eval/build notes recount same leak for `ps`-based case requiring name assembly at runtime. Chapter correctly describes subtract-observer rule but does not carry forward the operational requirement that `work` harness must avoid pattern in its own `args=`; second checker `check_portable.py` does not enforce `ps` self-match hygiene. Gap between lesson and enforcement. | med |
| 5 | ch02-what-the-number-cannot-say.md:The aggregate that swallows + ch06/ ch08 | Aggregates (`for` loop exit = last iteration, `|| true` swallowing) described as shell behavior without stating dependence on `set -e` / `set -o pipefail` absence | `bash` manual (ref 5) defines loop exit as last command and `pipefail` as opt-in. The listings showing swallowed failures rely on unset `pipefail`/`errexit`; without that precondition the 0-status demonstration does not hold. Claim oversizes negative inference from single 0. Needs explicit precondition in routine step 4 sizing. | med |
| 6 | ch03-the-commentary-channel.md:What order testifies to + ch07-time-order-and-the-moving-world.md:Ordering artifacts | Merged-stream order described as buffering artifact without stating capture mode for Python `print` vs C `setvbuf` | setvbuf(3) (ref 18) documents C stdio buffering; Python 3's `print` buffering under pipe is interpreter-level and diverges from C rule unless `-u` used. Listing `python3 steps.py 2>&1 | cat` interleaving demonstration is reproducible under CPython's block-buffered `sys.stdout` only when not `-u`; not covered by cited `setvbuf`. Requires citation to Python docs or explicit `PYTHONUNBUFFERED` precondition. | med |
| 7 | backmatter.md:Measured-output conditions + references | Claims GNU behavior assumed where GNU and POSIX differ, listing `stat -c`, `grep -r`, `sed -i`, `touch -d` as non-portable, but manuscript text elsewhere presents `ps ax -o args=` as portable | `ps ax -o args=` is BSD+GNU extension, not POSIX (`ps -o args`); `ax` without dash is BSD form, `-o` is POSIX form, combined `ax -o` is procps-specific and fails on strict POSIX `ps`. Contradicts portability discipline enforced by `check_portable.py`. Must pin to `ps -eo args` or document GNU procps requirement alongside `stat -c` pinning. | med |

## Suggestions (non-blocking)
1. Add a one-sentence qualifier to frontmatter Introduction matching provenance language: "At submission proposed and testable, not yet measured; judge grades in the open" — eliminates finding #1 without weakening hook.
2. Chapter 1 routine step 2: expand "Is this a trichotomy tool whose 1 is an answer?" to a short lookup table (grep/diff/cmp) plus instruction to check `EXIT STATUS` section; reduces reader reliance on memory which text itself warns against.
3. Chapter 5 truncation: include CI-web-interface truncation notice example verbatim ("showing last 100 lines...") beside `head`/`tail` — most readers will meet this before shell truncation.
4. Chapter 6 evidence grading: add a concrete example of `.get()`-vs-`in` nuance for `false` vs `null` vs `absent` (flag `enabled: false` vs missing) alongside `expires`/`revoked`; same collapse idiom recurs with boolean configs.
5. Chapter 7: standardize zone pinning — every listing printing a wall clock should `export TZ=UTC` and use `+0000`; currently only subset do, leaving local-zone ambiguity for the empty-log and rotation sections.
6. Eval docs: publish `eval/compact.md` generation hash beside `eval/README.md` thresholds so condition-(b) ablation is reproducible; currently `compact.md` is frozen prose with no checksum in provenance.
7. Consider moving "failure modes of the composed routine" (ch08 ten-item list) to backmatter one-page checklist — high utility for operator supervision and model chain-of-thought auditing.

## Fact-check sample
Pass 2: 5% sample (~7 of ~130 factual claims), chosen across families, verified against manuscript's own cited sources. Tools accessed external references where available; man7.org fetched live, gnu.org and Python docs verified via cached citation text.

| Claim (quoted) | Location | Cited source | Supported? (yes/no/partly) |
|---|---|---|---|
| "grep's documented contract is a trichotomy: 0 means at least one line was selected, 1 means no lines were selected, 2 means an error occurred" | ch01:The trichotomy | ref 1 GNU grep manual Exit Status; ref 2 https://man7.org/linux/man-pages/man1/grep.1.html EXIT STATUS (fetched live: "Normally the exit status is 0 if a line is selected, 1 if no lines were selected, and 2 if an error occurred.") | yes |
| "diff's manual spends the three values as: 0, the inputs are the same; 1, the inputs differ; 2, trouble" | ch01:The trichotomy | ref 3 GNU diffutils Invoking diff | yes |
| "SIGTERM is signal 15; 128 + 15 = 143. SIGKILL is 9, so a 137 means killed outright" | ch01:The upper band | refs 5 Bash manual 128+N, 17 signal(7) | yes |
| "timeout utility: the command outlived its allowance and timeout killed it. 124 is not a shell value at all but the documented report of the timeout utility" | ch01:The upper band | ref 7 GNU coreutils timeout manual | yes |
| "By default, curl does not consider HTTP response codes to indicate failure" and documents `--fail` which makes the tool fail with error code 22 for HTTP 400+ | ch01:The convention has apostates | ref 20 curl manual | yes |
| "rm -f ... includes not complaining about missing operands — it converts 'remove this file' from an action into a goal" | ch02:The no-op wearing success | ref 10 GNU coreutils rm `-f` ignores nonexistent operands | yes |
| "os._exit terminates the process immediately, skipping the interpreter's normal exit path — atexit handlers, stream flushing" | ch04:The silence that ate the data | ref 19 Python docs os._exit | yes |
| "stat -c '%n size=%s modified=%y' ... naming fields, zone pinned to UTC" and `stat -c` format directives | ch07:When the read happened / backmatter | ref 14 stat(1) `-c` format | yes |
| "mkdir -p succeeds when the directory exists ... goal-state contract" | ch02:The no-op wearing success | ref 11 GNU coreutils mkdir `-p` | yes |

All sampled claims supported by cited sources as retrieved. No automatic blocking finding raised from sample. Independent resolution: man7 grep page fetched and matches citation; remaining gnu.org/python docs citations match quoted contract text in manuscript and are internally consistent, but live fetch of gnu.org rate-limited in this sandbox — operator should rerun one sampled `webfetch` per ref on publication gate if strict out-of-band verification required.

## Scores (1–5)
accuracy: 4 · clarity: 5 · completeness-for-tier: 4 · density: 5 · originality: 5

## Pass-3 only: findings ledger
| Finding # (from Pass 2) | Status: resolved / rebutted-accepted / still-open | Note |
|---|---|---|
| — | — | Pass 2 review; no ledger yet. |
