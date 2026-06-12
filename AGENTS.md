# kuch-bhi — Agent Instructions

## What this project does
`kuch-bhi` is a CLI food ordering agent for Swiggy and Zomato. It reads past order history, finds nearby restaurants with active discounts, and places Cash on Delivery orders.

## Running the agent

### Show suggestions (no order placed)
```bash
npx order-kuch-bhi suggest
```
Parse the line starting with `KUCH_BHI_SUGGESTIONS:` from stdout — it contains a JSON array of ranked suggestions.

### Place a specific order
```bash
npx order-kuch-bhi place '<suggestion-json>'
```
Takes a single suggestion object from the suggest output and places that order. Asks for confirmation before placing.

### Full interactive flow
```bash
npx order-kuch-bhi
```

## Using as a slash command (Claude Code / Codex CLI)

1. Run `npx order-kuch-bhi suggest 2>&1`
2. Parse the `KUCH_BHI_SUGGESTIONS:` JSON line from output
3. Present the options to the user and ask them to pick one
4. Run `npx order-kuch-bhi place '<selected-json>'`

## Auth setup (one-time)
```bash
npx order-kuch-bhi connect swiggy
npx order-kuch-bhi connect zomato
```

## Environment variables
| Variable | Description |
|---|---|
| `LLM_PROVIDER` | `claude` (default) · `openai` · `ollama` |
| `ANTHROPIC_API_KEY` | Required for Claude |
| `OPENAI_API_KEY` | Required for OpenAI |
| `OPENAI_MODEL` | OpenAI model name (default: `gpt-4o`) |
| `OLLAMA_MODEL` | Ollama model name (default: `qwen2.5:7b`) |
| `OLLAMA_BASE_URL` | Ollama base URL (default: `http://localhost:11434`) |
