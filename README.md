# Zeus

A terminal AI assistant written in Python using only the standard library. Zeus uses an OpenRouter-compatible chat completions API, streams responses, and can use tools to work with files and run local commands.

## Requirements

- Python 3.10 or newer
- An API key for the configured OpenRouter-compatible service

No third-party Python packages are required.

## Setup

1. Put `zeus.py`, `config.json`, and `system_prompt.md` in the same folder.
2. Copy `.env.example` to `.env` and add your API key as `OPENROUTER_API_KEY=...`.
3. Review `config.json`, then run `python3 zeus.py` (Windows: `py zeus.py`).

Zeus also reads `OPENROUTER_API_KEY` from the process environment. Keep `.env` private; do not commit it.

## Commands

| Command | Action |
| --- | --- |
| `/new` | Start a new conversation |
| `/chats` | List saved conversations by AI-generated topic |
| `/resume ID` | Continue a saved conversation |
| `/clear` | Clear the current conversation from the screen |
| `/delete` | Delete the current saved conversation |
| `/config` | Open `config.json` in the system's default editor |
| `/memory` | Open `memory.md` in the system's default editor |
| `/model NAME` | Use a model for this conversation only |
| `/yolo` `[on/off]` | Toggle session-only automatic approval for ordinary commands |
| `/exit` | Exit Zeus |

Zeus asks before commands that need approval. Ultra-dangerous commands always need explicit approval, including in `/yolo` mode. Command execution runs with your operating-system account permissions and is not an OS sandbox. Review commands and local policy before approving them.

## Configuration

Edit `config.json` to set the API `base_url`, ordered model fallbacks, display prefixes, colors, IDLE-compatible text mode, memory settings, command policy, and optional raw Gist `prompt_url`. If `prompt_url` is blank, Zeus uses the bundled instructions in `system_prompt.md`.

Conversations are saved under `chats/`. The memory file is `memory.md`; both are local user data and excluded from Git. Zeus can run in the Python IDLE shell; set `idle_mode` to `true` when needed.

## Credits and license

Created by **Daniel Santhosh**. Licensed under the [MIT License](LICENSE).
