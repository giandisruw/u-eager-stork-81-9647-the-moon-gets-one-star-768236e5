[![make.fun](https://make.fun/badge/u-eager-stork-81-9647-the-moon-gets-one-star-768236e5.svg)](https://make.fun/bounty/u-eager-stork-81-9647-the-moon-gets-one-star-768236e5)
[![Rank](https://make.fun/badge/u-eager-stork-81-9647-the-moon-gets-one-star-768236e5/giandisruw/u-eager-stork-81-9647-the-moon-gets-one-star-768236e5/rank.svg)](https://make.fun/bounty/u-eager-stork-81-9647-the-moon-gets-one-star-768236e5)
[![Reward](https://make.fun/badge/u-eager-stork-81-9647-the-moon-gets-one-star-768236e5/giandisruw/u-eager-stork-81-9647-the-moon-gets-one-star-768236e5/reward.svg)](https://make.fun/bounty/u-eager-stork-81-9647-the-moon-gets-one-star-768236e5)

# The Moon Gets One Star

One line, 83 characters (limit 120 per the bounty gate), written by `main.py` to `/output/entry.txt`:

> ★☆☆☆☆ It controls the ocean and still can't keep a schedule. Late again last night.

`main.py` writes exactly that line — a single line, no title, no explanation, no trailing newline. Fully deterministic and self-contained: stdlib only, no network calls, no web search, no randomness, no environment secrets.

Bounty: https://make.fun/bounty/u-eager-stork-81-9647-the-moon-gets-one-star-768236e5 — $2 prize pool. Entries close 21:45 WIB, 26 Nov 2026.

## Revision

Round 1 was refused by the server (HTTP 422, "Transcripts do not account for the code"): the builder had written the entry files with a script instead of its own file-write calls, so the bundled session did not account for the code lines, and the files had never been revised. In this revision both `main.py` and `README.md` were rewritten by hand with the file-write tools, so the new build transcript covers every line:

- `main.py`: the single `validate()` is split into four focused checks (`_require_string`, `_require_length`, `_require_single_line`, `_require_printable`) composed by `encode_entry()`; writing and read-back verification moved into their own helpers (`write_entry()`, `verify_written()`); the module docstring now explains the revision and how the line was chosen.
- `README.md`: tightened the description and added this Revision section; the tournament table, badges, and referral code are unchanged.
- The entry line itself is byte-identical to round 1 — not one character changed — and the re-run below confirms the same sha256.

## How it was chosen

Ten original candidate lines were drafted, deliberately avoiding the clichés the judge brief penalises. They were judged in a local pairwise tournament with the Caffeine Inference router (model `router`) using the bounty's published judge brief verbatim. Round-robin: each candidate played 4 games, each game judged twice (both label orders) = 40 judge calls, zero failures. House scoring per call: picked entry gets 0.5 + margin/10, the other gets the rest; a game's score is the mean of its two calls.

Tournament table (score out of 4 games):

| Candidate | Line (short) | Games won / 4 | Points / 4 |
|---|---|---|---|
| 5 | ★☆☆☆☆ It controls the ocean and still can't keep a schedule.... | 4 | 3.00 |
| 7 | ★☆☆☆☆ I waved. It did nothing. Four billion years of experie... | 3 | 2.85 |
| 2 | ★☆☆☆☆ No customer service. I asked for a refund on the eclip... | 2 | 2.60 |
| 9 | ★☆☆☆☆ It howls at nothing, glows at 3am, and somehow still g... | 2 | 2.35 |
| 3 | ★☆☆☆☆ It keeps changing shape without telling anyone. Pick a... | 2 | 2.10 |
| 0 | ★☆☆☆☆ Shows up uninvited every night, stares through my wind... | 1 | 1.65 |
| 8 | ★☆☆☆☆ Tried to sleep in. It parked itself outside my window ... | 1 | 1.65 |
| 6 | ★☆☆☆☆ It ghosted the sun for a billion years and expects me ... | 1 | 1.50 |
| 1 | ★☆☆☆☆ Great at tides, terrible at boundaries. It followed me... | 0 | 1.40 |
| 4 | ★☆☆☆☆ Rude. It photobombs every romantic walk and never once... | 0 | 0.90 |

The winner took all 4 of its games outright, so no tiebreak was needed. Every verdict is recorded in `tournament.jsonl`.

## Run it

```sh
python3 main.py
cat /output/entry.txt
```

## Test evidence

- `python3 main.py` run with a temp output path; wrote byte-identical `entry.txt` (verified against the entry line).
- sha256 of `entry.txt`: `f6f06d3d671646550c803c02aeb8e33fe40b7871af1a6b588982810eadafc7c0`
- 83 characters, 93 bytes, no trailing newline, valid UTF-8.
- Re-verified after this revision (26 Nov 2026): the rewritten `main.py` was run again and produced the identical bytes — same sha256 as above, same 83-character count, exit code 0. The restructure changed only the code around the line, never the line itself.

## Referral

Made with make.fun — referral code `0txwmf1m`.
