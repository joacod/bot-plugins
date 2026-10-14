# How it works

## Lesson files
One markdown file per area in the lessons folder (default `lessons/` in the box workspace). Append-only, one line per signal. The box filesystem is shared by all of a user's agents, so every bot reads and writes the same folder. Detail lives here; only short rules reach memory or skills.

## Levels
- **example**: one instance. A sample of taste, never a rule.
- **pattern(n)**: the same signal in 2+ different pieces; n counts sightings.
- **rule**: 3+ sightings, user approval, or an explicit always/never. Only rules go into skills or always-on memory.

This staging step is the point: one edited draft never becomes a format rule.

## Signals
- Correction: the user says something was wrong.
- Edit: the user changes a draft before using it (log the short diff).
- Reaction: thumbs up/down etc. (arrive as hidden events). Example level only.
- Explicit: "always" / "never". Becomes a rule immediately.

## Weekly review
A scheduled routine reads all lesson files, promotes, demotes on conflict, archives stale rules, applies rules to skills or memory, and sends the user one digest (or nothing). Skills change at most weekly, so behavior stays stable.

## Archive
Rules not used or confirmed in 30 days move to `archive/`. Nothing is deleted, so a rule can be restored if it turns out to matter.

## What runs where in Grok Bot
| Piece | Where it lives | How it works |
|---|---|---|
| Logging a signal | Lesson files in the shared box folder | Any bot appends a line during the turn it sees the signal |
| Short rules | Agent memory (profile/log/note) or shared user memory | Only rule-level lessons, kept to one sentence |
| Skill updates | Shared skill library (SKILL.md via UpdateSkill; extra files via shell) | The weekly review applies rules to the skill that owns the area |
| Weekly review | A scheduled routine | Promotes, demotes, archives, sends one digest or nothing |
| Looking back | RecallMemory, ReadTranscript for owned agents, lesson files | No full-text search across every past session |
| Sharing across bots | SendToAgent and group chats | Lessons from another bot arrive as examples only |

Not possible: automatic review after every turn without a routine, retraining model weights, and reading transcripts of agents you do not own.
