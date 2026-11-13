# Agents Replay

See what your AI agents did on your Mac, from your iPhone: a recap of every day and a replay of every click.
Your iPhone reads it straight from your Mac over your own Wi‑Fi, end-to-end encrypted. More at [agentsreplay.com](https://agentsreplay.com).

This repository is the plugin that installs Agents Replay on your Mac. It works the same way in Claude Code and in Codex.

## Install

Claude Code:

```sh
claude plugin marketplace add agentsreplay/plugin
claude plugin install agents-replay
```

Codex:

```sh
codex plugin marketplace add agentsreplay/plugin
codex plugin add agents-replay@agents-replay
```

Start a new session. The Mac app installs itself in the background (Apple-notarized, checked before it runs), and Codex asks you to trust the plugin's hooks once. Then ask your agent to "pair my iPhone with Agents Replay" and scan the QR code with the iPhone app.

## What the plugin does

- `bin/ensure-daemon` runs when a session starts: it downloads the Mac app from agentsreplay.com if it is missing or out of date, verifies Apple's notarization and our Developer ID team, and keeps it running.
- The hooks tell the Mac app that something just happened, so it reads the agent's session log right away. They send nothing anywhere else.
- The MCP server gives your agent six tools: `status`, `pair`, `unpair`, `rescan`, `keep_awake`, `permissions`.

## Remove

Unpair in the iPhone app, then `claude plugin uninstall agents-replay` or `codex plugin remove agents-replay@agents-replay`, and delete `~/Applications/AgentReplay.app` and `~/Library/Application Support/AgentReplay`.

[Support](https://agentsreplay.com/support) · [Privacy](https://agentsreplay.com/privacy)
