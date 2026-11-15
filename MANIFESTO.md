# LOCAL ONLY — Manifesto

> *Support your localhost.*

**Português** · [English](#english) · [Referências](REFERENCIAS.md)

## O problema

Ferramenta de segurança que manda seus dados para a nuvem de outra pessoa já começa com um vazamento.

Alvos, escopos, achados, credenciais de teste e código-fonte de cliente são o material mais sensível que um profissional de segurança manipula. Mesmo assim, virou normal processar tudo isso no servidor de terceiros, com uma conta, uma API key e uma política de privacidade que ninguém leu.

Isso não é um medo abstrato:

- Em 2023, engenheiros da Samsung colaram código-fonte de semicondutores e atas de reunião no ChatGPT para conseguir ajuda. A empresa respondeu proibindo IA generativa nos dispositivos corporativos. [9]
- Em 2024, um único grupo usou credenciais roubadas para acessar dados de cerca de 165 organizações num mesmo serviço de nuvem. Não precisou invadir o provedor: bastou que todos os dados estivessem no mesmo lugar. [10]
- Em 2020 e em 2024, atualizações automáticas foram o problema. Uma carregou um backdoor para dentro de governos e empresas (SolarWinds) [11]; a outra derrubou cerca de 8,5 milhões de máquinas Windows num só dia (CrowdStrike). [12]
- A OWASP coloca o vazamento de informação sensível entre os maiores riscos de aplicações com LLM em 2025. [8]

O que esses casos têm em comum: dados e controle que saíram da máquina de quem era dono deles.

## A ideia

Há anos se fala nisso com outros nomes. Stallman chamou de *Service as a Software Substitute*: quando sua computação roda no servidor de outro, quem controla os dados é ele, não você. [2] Kleppmann e colegas chamaram a alternativa de *local-first*: o software prioriza o seu disco e continua funcionando se o serviço cair ou acabar. [1]

**LOCAL ONLY** leva isso para segurança ofensiva e defensiva, e com mais rigor: não é *local primeiro*, é *local e pronto*. A nuvem entra só quando você decide, e de forma visível.

## Princípios

### 1. Roda na sua máquina
Depois do setup, a ferramenta funciona sem internet. Toda chamada de rede é declarada, opcional e pode ser desligada. Se o fornecedor sumir amanhã, a ferramenta continua funcionando. [1][2]

### 2. Seus dados ficam no seu disco
Relatórios, achados e configurações ficam em formatos abertos (Markdown, JSON, SARIF, SQLite) e podem ser lidos sem a ferramenta. Coletar só o necessário é obrigação legal (LGPD, art. 6º, III; GDPR, art. 25), e não coletar nada é a forma mais simples de cumpri-la. [1][5][6]

### 3. Seguro por padrão, inclusive a privacidade
Zero telemetria. Se existir, é opt-in e documentada. Seguindo Saltzer e Schroeder, na dúvida a ferramenta nega; seguindo a CISA, quem instala não deveria precisar reconfigurar nada para ficar seguro. [3][4][5]

### 4. Sobe com um comando
`pip install`, `gem install`, `docker compose up` ou `make run`. Sem "crie uma conta primeiro". Quanto menos peças, menos coisa para dar errado. [3]

### 5. Escuta em `127.0.0.1`
Nenhuma rede é confiável por padrão, nem a sua. [7] Abrir a ferramenta para a rede é decisão explícita de quem usa, nunca o padrão.

### 6. IA é opcional, e local quando possível
Se a ferramenta usa LLM, ela aceita um modelo local (Ollama, LM Studio, endpoint compatível com OpenAI) e tem um modo que funciona sem modelo nenhum. Mandar um alvo para um LLM em nuvem é decisão sua, com aviso, nunca uma dependência escondida. [8][9]

### 7. Atualização é um ato, não um efeito colateral
Regras, feeds de CVE e modelos chegam por um comando que você roda, de forma verificável e reversível. O que muda o seu ambiente sem você pedir é, por definição, uma superfície de ataque. [4][11][12]

### 8. Escopo é contrato
Ferramentas ofensivas só agem sobre alvos autorizados. O guarda de escopo é código determinístico fora do modelo, bloqueia antes de qualquer I/O e registra cada ação. Menor privilégio também vale para agentes. [3]

## O teste

Desligue a rede. Rode a ferramenta. Se ela faz o trabalho dela, é **LOCAL ONLY**.

O teste não vale para os alvos que você escolheu atacar ou auditar: uma ferramenta de pentest precisa alcançar o alvo. A regra é que **nada além disso** saia da máquina.

Critérios de verificação no [CHECKLIST.md](CHECKLIST.md). Fontes completas em [REFERENCIAS.md](REFERENCIAS.md).

---

## English

### The problem

A security tool that ships your data to someone else's cloud starts out as a leak.

Targets, scopes, findings, test credentials and client source code are the most sensitive material a security professional handles. Yet processing them on third-party servers has become the default.

- In 2023, Samsung engineers pasted semiconductor source code and meeting notes into ChatGPT; the company banned generative AI on corporate devices. [9]
- In 2024, one group used stolen credentials to reach data from about 165 organizations on a single cloud service, without breaching the provider. [10]
- In 2020 and 2024, automatic updates were the problem: one shipped a backdoor (SolarWinds) [11], the other took down about 8.5 million Windows machines in a day (CrowdStrike). [12]
- OWASP ranks sensitive information disclosure among the top risks for LLM applications in 2025. [8]

### The idea

Stallman called it *Service as a Software Substitute* [2]; Kleppmann et al. proposed *local-first* as the alternative [1]. **LOCAL ONLY** brings that to security tooling, more strictly: not local *first*, local, period. The cloud is a visible, deliberate choice.

### Principles

1. **Runs on your machine.** Works offline after setup; every network call is declared and can be turned off. [1][2]
2. **Your data stays on your disk,** in open formats, readable without the tool. Data minimization is the law; collecting nothing is the simplest way to comply. [1][5][6]
3. **Secure, and private, by default.** Zero telemetry; fail-safe defaults; no reconfiguration needed to be safe. [3][4]
4. **One command to start.** No "create an account first". [3]
5. **Binds to `127.0.0.1`.** No network is trusted by default, including yours. [7]
6. **AI is optional, and local when possible.** Local models supported, and a mode that works with no model at all. [8][9]
7. **Updating is an act, not a side effect.** Explicit, verifiable, reversible. [4][11][12]
8. **Scope is a contract.** Deterministic scope guard outside the model, blocking before any I/O, logging every action. [3]

### The test

Unplug the network, run the tool. If it does its job, it's **LOCAL ONLY**. The only traffic allowed is to the targets you chose to test.
