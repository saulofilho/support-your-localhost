# support your localhost

**Security tools you can use in the cloud, and also run 100% on your own machine.**

Deploy them, host them, use the online demo. But when the target is sensitive, the client is under NDA, or the network is off, the same tool runs on `localhost`, with no account, no API you didn't choose, and nothing leaving your machine.

[Manifesto](#the-also-local-manifesto) · [Catalog](#catalog) · [Checklist](CHECKLIST.md) · [References](REFERENCES.md)

---

## The *also local* manifesto

### Not anti-cloud. Pro-choice.

The cloud is a good place for demos, teams and shared dashboards. It is a bad place to be *forced* to send targets, scopes, findings, test credentials and client source code, which are the most sensitive material a security professional handles.

The problem isn't hosting. The problem is tools that *only* work hosted. Some examples:

- In 2023, Samsung engineers pasted semiconductor source code and meeting notes into ChatGPT to get help. The company banned generative AI on corporate devices. [9]
- In 2024, one group used stolen credentials to reach data from about 165 organizations on a single cloud service, without breaching the provider. [10]
- In 2020 and 2024, automatic updates were the problem: one shipped a backdoor into governments and companies (SolarWinds) [11]; the other took down about 8.5 million Windows machines in one day (CrowdStrike). [12]
- OWASP ranks sensitive information disclosure among the top risks for LLM applications in 2025. [8]

What these cases have in common is that the user had no local alternative, or didn't use one.

### Where the idea comes from

Stallman called it *Service as a Software Substitute*: when your computing runs on someone else's server, they control your data. [2] Kleppmann and colleagues proposed *local-first* as the alternative: software that prioritizes your disk and keeps working if the service goes down or disappears. [1]

**support your localhost** applies that to security tooling, without dogma: a tool can live in the cloud, as long as it **also** runs entirely on your machine. Local is never the second-class version.

### Principles

**1. The local path is first-class.**
Everything the hosted version does, the local version does too, with the same features and no account. If the vendor disappears tomorrow, the tool keeps working. [1][2]

**2. Offline after setup.**
Once installed, the tool works without internet. Every network call is declared and can be turned off. The only exception is the targets you chose to test.

**3. Your data stays on your disk.**
Reports, findings and settings use open formats (Markdown, JSON, SARIF, SQLite) and are readable without the tool. Data minimization is the law (LGPD art. 6, GDPR art. 25), and collecting nothing is the simplest way to comply. [1][5][6]

**4. Secure, and private, by default.**
Zero telemetry; opt-in and documented if it exists at all. Fail-safe defaults [3], and no reconfiguration needed to be safe. [4]

**5. One command to start.**
`pip install`, `gem install`, `docker compose up` or `make run`. No "create an account first."

**6. Bind to `127.0.0.1`.**
No network is trusted by default, including yours. [7] Exposing the tool is an explicit choice.

**7. AI is optional, and local when possible.**
If the tool uses an LLM, it accepts a local model (Ollama, LM Studio, any OpenAI-compatible endpoint) and has a mode that works with no model at all. Sending a target to a cloud LLM is your call, made visibly. [8][9]

**8. Updating is an act, not a side effect.**
Rules, CVE feeds and models arrive through a command you run, verifiable and reversible. [4][11][12]

**9. Scope is a contract.**
Offensive tools act only on authorized targets. The scope guard is deterministic code outside the model, blocks before any I/O and logs every action. [3]

### The test

Unplug the network and run the tool. If it does its job, it supports your localhost. Traffic to the targets you chose to test is the only thing allowed out.

---

## Catalog

Every tool here has a hosted page or demo **and** a local path.

| Badge | Meaning |
|---|---|
| 🟢 | **Fully local.** Every feature runs offline. |
| 🟡 | **Local, with a cloud dependency.** Runs locally, but at least one feature needs an external API (usually a cloud LLM). Local LLM support is on the roadmap. |
| ⚪ | **Not yet verified** against the [checklist](CHECKLIST.md). |

### Planning and generation (deterministic, no LLM)

| Tool | What it does | Run locally | Badge |
|---|---|---|---|
| [security-pentest-planner](https://saulofilho.github.io/security-pentest-planner/) | Builds pentest action plans from OpenAPI specs, code or design docs: attack vectors, payloads, remediations, and RFCs for structural fixes. | Ruby gem (CLI) · agent skill | ⚪ |
| [security-pentest-planner-python](https://saulofilho.github.io/security-pentest-planner-python/) | Python port: authorized scope → engagement → contract risks → deterministic plan → remediations → selective RFCs. | `pip install security-pentest-planner` · CLI, library, MCP plugin | ⚪ |
| [agent-eval-planner](https://saulofilho.github.io/agent-eval-planner/) | Reads an agent's contract (system prompt, tools, out-of-scope rules) and builds a deterministic eval pack: attack prompts, pass/fail criteria, a JSONL suite and remediations. | Ruby gem (CLI) | ⚪ |
| [agent-eval-planner-python](https://saulofilho.github.io/agent-eval-planner-python/) | Python port of agent-eval-planner, with the same output. Also runs in GitHub Actions. | `pip install agent-eval-planner` · CLI, library | ⚪ |
| [routes_api_spec_generator](https://saulofilho.github.io/routes_api_spec_generator/) | Reads `routes.rb` and controllers from a Rails API and generates rswag request specs, with no OpenAPI input needed. | Ruby gem · rake task | ⚪ |

### Analysis and detection

| Tool | What it does | Run locally | Badge |
|---|---|---|---|
| [SecScan](https://secscan.ai.studio/) | AppSec suite: SAST, secret matrix, data flow and a quality gate, with SARIF output. | Local server (Node 22) | ⚪ |
| [WebAudit Pro](https://webauditpro.ai.studio/) | Website audit covering security, SEO, performance, accessibility and privacy, with reports and visual regression diffs. | Local web app (React/Vite) | 🟡 AI reports use Gemini |
| [exposure-canary](https://saulofilho.github.io/exposure-canary/) | Creates canary tokens (URL, DNS, email) on assets you own, imports collector hits and reports when and by whom each one was touched. | Python CLI · MCP server | ⚪ |

### Offensive (authorized use only)

| Tool | What it does | Run locally | Badge |
|---|---|---|---|
| [scopehound](https://saulofilho.github.io/scopehound/) | Human-in-the-loop AI pentest agent. Scope, permissions and limits are enforced by a layer separate from the model, and every action is logged. | Local, single analyst | ⚪ |
| [pentest-harness](https://saulofilho.github.io/pentest-harness/) | LangGraph orchestration for authorized AppSec work, with a scope guard, a human approval gate and dry-run on by default. | Python CLI | 🟡 `run` needs a cloud LLM; `check-scope` is offline |
| [hackbot](https://saulofilho.github.io/hackbot/) | ReAct agent that picks security tools against an authorized target, with a scope guard, a kill switch and dry-run by default. | Python CLI | 🟡 `run` needs an LLM; `demo` is offline |
| [Caipora](https://saulofilho.github.io/caipora/) | Brazil-focused red teaming for LLMs and agents: Portuguese-language attacks, detection of Brazilian personal data (CPF, CNPJ, Pix…), an agent honeypot and MCP server audits. | CLI · CI | ⚪ |

> ⚠️ Use the offensive tools only against systems you own or have written authorization to test.

---

## Roadmap

1. Run the [checklist](CHECKLIST.md) on every tool and assign badges.
2. Add local LLM support (Ollama / OpenAI-compatible) to the 🟡 tools.
3. Add a single launcher: `syl list`, `syl up <tool>`.
4. Open submissions for third-party tools.

## Contributing

Have a tool that also runs locally? Check it against the [checklist](CHECKLIST.md) and open a PR adding it to the catalog.

## References

Full sources in [REFERENCES.md](REFERENCES.md).
