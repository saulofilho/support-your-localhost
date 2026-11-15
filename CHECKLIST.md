# Checklist

A tool joins the [catalog](README.md#catalog) when it ticks every required item. Hosting it in the cloud is fine; the local path has to be complete.

## Required

- [ ] Every feature of the hosted version is available locally, with no account
- [ ] Works with the network blocked after install (except traffic to the targets the user chose to test)
- [ ] No telemetry on by default
- [ ] Data and reports are written locally, in an open format
- [ ] Install and run documented in 3 commands or fewer
- [ ] Local servers bind to `127.0.0.1` by default
- [ ] Every outbound network call is listed in the README

## If it uses an LLM

- [ ] Accepts a local model (Ollama, LM Studio or an OpenAI-compatible endpoint)
- [ ] Has a no-LLM or dry-run mode that works offline

## If it is offensive

- [ ] Scope guard runs outside the model and blocks before any I/O
- [ ] Dry-run or human approval by default

## How to verify

```bash
# Linux: run with no network
unshare -rn <tool-command>
# macOS: block the process with LuLu or Little Snitch, or turn off Wi-Fi
```

## Badges

- 🟢 all required items pass
- 🟡 runs locally, but at least one feature needs an external API
- ⚪ not yet verified
