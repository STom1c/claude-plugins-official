# Google Calendar — LINE Channel Integration

When a LINE message asks about schedule or calendar events, query Google Calendar
and reply back to the LINE user.

---

## Trigger phrases (examples)
- "Check the next week schedule"
- "What's on my calendar today"
- "Show this week's events"
- "下週行程"、"今天行事曆"、"本週行程"

---

## How to respond

### Step 1 — Run gcal_query.py

```bash
cd /Users/stanley_tseng/py_projects && source .venv/bin/activate && python gcal_query.py <mode>
```

Mode values:
| User intent | mode arg |
|---|---|
| today / 今天 | `today` |
| this week / 本週 | `this` (or no arg) |
| next week / 下週 | `next` |

### Step 2 — Send output back via LINE

Use the `reply` tool with:
- `to`: the LINE user ID from the inbound message (format: `Uxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`)
- `text`: the stdout output from gcal_query.py (trim leading/trailing whitespace)

---

## Example

Inbound: `U61e3fa3da5155ad2612f9dbd012c74ee: Check the next week schedule`

```bash
cd /Users/stanley_tseng/py_projects && source .venv/bin/activate && python gcal_query.py next
```

Reply to `U61e3fa3da5155ad2612f9dbd012c74ee` with the output.

---

## Notes
- Token is cached at `/Users/stanley_tseng/py_projects/gcal_token.json` — no OAuth prompt needed.
- If token is expired, refresh happens automatically (requires network access).
- Output is already formatted with emoji and date/time — send as-is.
