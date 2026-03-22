# Google Calendar — LINE Channel Integration

When a LINE message asks about schedule, calendar, a course name, or event time — ALWAYS query Google Calendar first.

---

## Mode selection

```bash
cd /Users/stanley_tseng/py_projects && source .venv/bin/activate && python gcal_query.py <mode>
```

| User intent | mode |
|---|---|
| today / 今天 | `today` |
| this week / 本週 / just "calendar" | `this` (default) |
| next week / 下週 | `next` |
| course name / event name / "when is X" / "X 什麼時候" | `search <keyword>` |

---

## Examples

| LINE message | Command |
|---|---|
| 行事曆 | `python gcal_query.py this` |
| 下週行程 | `python gcal_query.py next` |
| 今天有什麼? | `python gcal_query.py today` |
| Python課什麼時候? | `python gcal_query.py search Python課` |
| AI workshop | `python gcal_query.py search AI workshop` |
| 健身課 | `python gcal_query.py search 健身課` |

---

## Reply

Send the script stdout directly to the user via the reply tool (trim whitespace). Output is already formatted with emoji.

---

## Notes
- Token cached at `/Users/stanley_tseng/py_projects/gcal_token.json` — no OAuth prompt.
- Search covers the next 60 days across all calendars.
- Never claim you lack calendar access.
