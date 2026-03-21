# /line:configure — LINE Channel Setup

Writes credentials to `~/.claude/channels/line/.env`.

Arguments passed: `{{ args }}`

---

## Dispatch on arguments

### No args — status

1. Read `~/.claude/channels/line/.env` — show token set/not-set.
2. Read `~/.claude/channels/line/access.json` — show allowed users count.
3. Show relay URL (LINE_RELAY_URL, default http://172.20.76.104:8010).
4. Give next step based on state.

### `token <LINE_CHANNEL_ACCESS_TOKEN> <LINE_CHANNEL_SECRET>`

1. `mkdir -p ~/.claude/channels/line`
2. Read existing `.env` if present.
3. Update/add `LINE_CHANNEL_ACCESS_TOKEN=` and `LINE_CHANNEL_SECRET=` lines.
4. `chmod 600 ~/.claude/channels/line/.env`
5. Confirm, show status.

### `relay <URL>`

Set `LINE_RELAY_URL=<URL>` in `.env`.

### `relay-secret <SECRET>`

Set `LINE_RELAY_SECRET=<SECRET>` in `.env`.

---

## Implementation notes

- Token changes need a Claude Code session restart.
- access.json is re-read on every poll cycle — allowlist changes take effect within 2s.
