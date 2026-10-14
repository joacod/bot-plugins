---
name: fleet-self-learning
description: >-
  Use to install self-learning for one bot or many (lessons folder plus weekly
  review routine), and afterwards whenever the user corrects a bot or group,
  edits a draft before using it, reacts to a result, or gives an always/never
  instruction, to log the lesson without overgeneralizing; also when running
  the weekly lessons review.
---
# Fleet self-learning

Every interaction makes your bots a little better, through lesson notes, memory and skills, without turning one example into a rule.

How the parts fit together: `references/how-it-works.md`.

## Install (one time)
1. Create a lessons folder in the box workspace (default `lessons/`) with an `archive/` subfolder.
2. Copy `templates/lessons-README.md` to `lessons/README.md`. For each area you work in (writing, code, design, social...), copy `templates/area-template.md` to `lessons/<area>.md`.
3. Create a weekly routine with the prompt in `references/routine-prompt.md` (suggested: a weekday afternoon, once a week). Adjust the folder path if you changed it.
4. Multi-bot setups only: brief the other bots or groups with `references/bot-brief.md`, so they log signals to the same folder. Ask the user before sending.

## On each signal
Signals: a correction, an edit to a draft before use, a reaction, or an explicit always/never.
1. Pick the area and the bot or group it applies to.
2. Append one line to that area file (format in the README). If the same signal is already there, bump its count instead.
3. Levels: **example** (one instance, never a rule), **pattern(n)** (seen in 2+ different pieces), **rule** (3+ sightings, user approval, or explicit always/never).
4. Explicit always/never: update the owning skill or memory right away and tell the owning bot.
5. Reactions alone count only as examples. Never write format rules (length, tone, structure) from one piece.
6. Unsure if it is general? Ask once: "always, or just this time?" Default to example.

## Weekly review
Run by the routine. Read all lesson files, promote patterns at 3+ sightings, demote rules contradicted by newer signals (the latest explicit statement wins), move rules unused for 30 days to `archive/` (never delete), suggest lessons to related bots as examples only, apply rules to the owning skill or memory (rules section about 40 lines max, each with reason and date), then send the user one short digest. Send nothing if nothing changed.

## Limits
- No review on every turn. Skills change at most weekly, except explicit always/never.
- Keep always-on memory small; detail lives in lesson files.
- A wrong rule goes back to example or archive when the user corrects it.
- Nothing is retrained; learning lives in notes, memory and skills.

