# support your localhost

**Um hub de ferramentas de segurança que rodam 100% na sua máquina.** Sem nuvem, sem conta, sem enviar seus alvos para ninguém.

Leia o [manifesto LOCAL ONLY](MANIFESTO.md) · Quer submeter uma ferramenta? Veja o [checklist](CHECKLIST.md).

## Selos
- 🟢 **LOCAL ONLY** — passa no checklist inteiro, sem rede
- 🟡 **LOCAL FIRST** — roda local, mas alguma função depende de API externa (geralmente um LLM em nuvem)
- ⚪ **Em avaliação** — ainda não verificada

## Catálogo

### Planejamento e geração (determinísticas, sem LLM)

| Ferramenta | O que faz | Roda como | Selo |
|---|---|---|---|
| [security-pentest-planner](https://saulofilho.github.io/security-pentest-planner/) | Gera planos de pentest a partir de OpenAPI, código ou docs de design: vetores, payloads, remediações e RFCs para correções estruturais. | Gem Ruby (CLI) · skill de agente | ⚪ |
| [security-pentest-planner-python](https://saulofilho.github.io/security-pentest-planner-python/) | Port Python do planner: escopo autorizado → engagement → riscos do contrato → plano determinístico → remediações. | CLI · lib Python · plugin MCP | ⚪ |
| [agent-eval-planner](https://saulofilho.github.io/agent-eval-planner/) | Lê o contrato de um agente (system prompt, ferramentas, regras de escopo) e gera um pacote de evals determinístico: prompts de ataque, critérios de pass/fail, suíte JSONL e remediações. | Gem Ruby (CLI) | ⚪ |
| [agent-eval-planner-python](https://saulofilho.github.io/agent-eval-planner-python/) | Port Python do agent-eval-planner, com a mesma saída; roda também no GitHub Actions. | CLI · lib Python | ⚪ |
| [routes_api_spec_generator](https://saulofilho.github.io/routes_api_spec_generator/) | Lê `routes.rb` e controllers de uma API Rails e gera specs rswag, sem precisar de OpenAPI. | Gem Ruby · rake task | ⚪ |

### Análise e detecção

| Ferramenta | O que faz | Roda como | Selo |
|---|---|---|---|
| [SecScan](https://secscan.ai.studio/) | Suíte AppSec: SAST, matriz de segredos, data flow e quality gate com saída SARIF. Você sobe o servidor local e analisa os arquivos ali. | Servidor local (Node 22) | ⚪ |
| [WebAudit Pro](https://webauditpro.ai.studio/) | Auditoria de websites em segurança, SEO, performance, acessibilidade e privacidade, com relatórios e diff visual de regressão. | App web local (React/Vite) | 🟡 relatórios via Gemini |
| [exposure-canary](https://saulofilho.github.io/exposure-canary/) | Cria canary tokens (URL, DNS, e-mail) nos seus ativos, importa hits do coletor e mostra quando e por quem cada um foi tocado. | CLI Python · servidor MCP | ⚪ |

### Ofensivas (uso autorizado apenas)

| Ferramenta | O que faz | Roda como | Selo |
|---|---|---|---|
| [scopehound](https://saulofilho.github.io/scopehound/) | Agente de IA para pentest assistido por humano. Escopo, permissões e limites ficam numa camada separada do modelo, e toda ação é registrada. | Local (um analista) | ⚪ |
| [pentest-harness](https://saulofilho.github.io/pentest-harness/) | Orquestração LangGraph para AppSec autorizado, com guarda de escopo, aprovação humana e dry-run por padrão. | CLI Python | 🟡 `run` usa LLM em nuvem |
| [hackbot](https://saulofilho.github.io/hackbot/) | Agente ReAct que escolhe ferramentas de segurança contra um alvo autorizado, com guarda de escopo, kill switch e dry-run. | CLI Python | 🟡 `run` usa LLM; `demo` é offline |
| [Caipora](https://saulofilho.github.io/caipora/) | Red teaming de LLMs e agentes com foco no Brasil: ataques em PT-BR, detecção de dados pessoais brasileiros, honeypot de agentes e auditoria de servidores MCP. | CLI · CI | ⚪ |

> ⚠️ As ferramentas ofensivas só devem ser usadas contra sistemas seus ou com autorização por escrito.

## Roadmap
1. Rodar o checklist em cada ferramenta e atribuir o selo
2. Suporte a LLM local (Ollama) nas ferramentas 🟡
3. Launcher único: `syl list`, `syl up <ferramenta>`
4. Site do hub e processo de submissão para terceiros
