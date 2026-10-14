# Fleet self-learning

A skill-only plugin that helps your Grok Bot agents get a little better with every interaction. One bot or a whole fleet logs your corrections, edits, reactions and explicit "always/never" instructions to a shared lessons folder. A weekly review promotes repeated signals to rules and applies them to skills or memory. A single example never becomes a rule.

## What it does
- **Logs signals** during normal work: corrections, edits you make to a draft before using it, reactions, and explicit always/never instructions.
- **Stages lessons** in three levels: example (one instance), pattern(n) (seen in 2+ pieces), rule (3+ sightings, your approval, or an explicit always/never).
- **Reviews weekly** through a scheduled routine: promotes, demotes on conflict (your latest explicit statement wins), archives stale rules (never deletes), applies rules to the owning skill or memory, and sends you one short digest, or nothing if nothing changed.
- **Shares across bots** in multi-bot setups, so lessons from one bot reach related bots as examples only.

Nothing is retrained. Learning lives in plain markdown notes, memory and skills that you can read and edit.

## Install
1. In Grok Bot or Cursor, add `https://github.com/joacod/bot-plugins` as a plugin source and install **Fleet self-learning**. In Grok, install it from `/plugins` > **Marketplace**.
2. Ask your bot: "Set up fleet self-learning." The skill walks it through the one-time install below.

To test locally before installing from the marketplace, copy `plugins/fleet-self-learning` to `~/.cursor/plugins/local/fleet-self-learning`, reload, and confirm the `fleet-self-learning` skill shows up under Customize.

## One-time setup (done by the bot)
1. Create a lessons folder in the box workspace (default `lessons/`, any path works) with an `archive/` subfolder.
2. Copy `skills/fleet-self-learning/templates/lessons-README.md` to `lessons/README.md`, and `skills/fleet-self-learning/templates/area-template.md` to `lessons/<area>.md` for each area you work in (writing, code, design, social...).
3. Create the weekly review routine (see below).
4. Multi-bot setups only: brief your other bots or groups with `skills/fleet-self-learning/references/bot-brief.md`. The bot asks you before sending anything.

## Weekly review routine
Create a scheduled routine in Grok Bot with the prompt from `skills/fleet-self-learning/references/routine-prompt.md`.

- **Schedule:** your choice. The suggestion is once a week on a weekday afternoon, for example cron `0 16 * * 4` (Thursday 16:00).
- **Time zone:** set the routine to your own time zone. The plugin assumes none.
- **Folder:** if you changed the lessons path, edit it in the prompt.

The routine sends one short digest to the chat: rules applied, patterns forming, and conflicts that need your call.

## How it works in Grok Bot
| Piece | Where it lives |
|---|---|
| Logging a signal | Lesson files in the shared box folder; any bot appends a line during the turn it sees the signal |
| Short rules | Agent memory or shared user memory, one sentence each |
| Skill updates | The shared skill library, updated by the weekly review |
| Weekly review | A scheduled routine |
| Sharing across bots | Agent messages and group chats; shared lessons arrive as examples only |

The box filesystem is shared by all of a user's agents, so every bot reads and writes the same lessons folder.

Details: `skills/fleet-self-learning/references/how-it-works.md`.

## Try it
1. Ask a bot to draft a short post, then edit it and tell the bot what you changed.
2. Check `lessons/<area>.md`: a new line at level `example`.
3. Say "always end posts with a question." The bot logs it as a rule and updates its memory or skill right away.

## Contents
```
.cursor-plugin/plugin.json
.grok-plugin/plugin.json
assets/logo.png, logo.svg           plugin logo
skills/fleet-self-learning/SKILL.md
skills/fleet-self-learning/references/   how-it-works, routine prompt, bot brief
skills/fleet-self-learning/templates/    lessons README, area template
CHANGELOG.md
```

## License
MIT. See `LICENSE`.
