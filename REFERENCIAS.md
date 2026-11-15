# Referências

Base teórica, normativa e de incidentes que sustenta o [manifesto LOCAL ONLY](MANIFESTO.md). Os números entre colchetes são citados no manifesto.

## Fundamentos

**[1]** KLEPPMANN, M.; WIGGINS, A.; VAN HARDENBERG, P.; McGRANAGHAN, M. *Local-first software: you own your data, in spite of the cloud.* In: Onward! '19, ACM SIGPLAN, Atenas, 2019, p. 154–178. DOI: [10.1145/3359591.3359737](https://doi.org/10.1145/3359591.3359737). Versão aberta: [inkandswitch.com/local-first](https://inkandswitch.com/local-first/).
> O artigo que deu nome ao movimento. Mostra que no software em nuvem, se o serviço cai ou acaba, você perde acesso aos próprios dados, e propõe priorizar o disco local. → princípios 1 e 2.

**[2]** STALLMAN, R. *Who does that server really serve?* GNU Project / Boston Review, 2010 (revisado em 2013 e 2023). [gnu.org/philosophy/who-does-that-server-really-serve.html](https://www.gnu.org/philosophy/who-does-that-server-really-serve.html).
> Define SaaSS (*Service as a Software Substitute*): fazer sua computação no servidor de outra pessoa entrega seus dados a ela. → princípios 1 e 2.

**[3]** SALTZER, J. H.; SCHROEDER, M. D. *The protection of information in computer systems.* Proceedings of the IEEE, v. 63, n. 9, p. 1278–1308, 1975. DOI: [10.1109/PROC.1975.9939](https://doi.org/10.1109/PROC.1975.9939).
> Princípios clássicos de *fail-safe defaults*, *least privilege* e *economy of mechanism*. → princípios 3, 5 e 8.

## Normas e guias

**[4]** CISA et al. *Shifting the Balance of Cybersecurity Risk: Principles and Approaches for Secure by Design Software.* abr. 2023, atualizado em out. 2023. [cisa.gov/resources-tools/resources/secure-by-design-and-default](https://www.cisa.gov/resources-tools/resources/secure-by-design-and-default).
> Seguro por padrão: o produto deve resistir a ataques sem precisar de reconfiguração, e o ônus da segurança não deve cair só no usuário. → princípios 3, 5 e 7.

**[5]** BRASIL. *Lei nº 13.709/2018 (LGPD)*, art. 6º, III (necessidade) e art. 46, §2º (segurança desde a concepção). [planalto.gov.br](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm).
> Minimização de dados e segurança desde a concepção como obrigação legal. → princípios 2 e 3.

**[6]** UNIÃO EUROPEIA. *Regulamento (UE) 2016/679 (GDPR)*, art. 25: *data protection by design and by default*. [eur-lex.europa.eu](https://eur-lex.europa.eu/eli/reg/2016/679/oj).
> Equivalente europeu do [5]. → princípios 2 e 3.

**[7]** NIST. *SP 800-207: Zero Trust Architecture.* 2020. DOI: [10.6028/NIST.SP.800-207](https://doi.org/10.6028/NIST.SP.800-207).
> Nenhuma rede é confiável por padrão. → princípio 5.

**[8]** OWASP. *Top 10 for LLM Applications 2025*, LLM02: Sensitive Information Disclosure. [genai.owasp.org](https://genai.owasp.org/llm-top-10/).
> LLMs podem expor dados confidenciais enviados a eles; o item subiu quatro posições em relação a 2024. → princípio 6.

## Incidentes

**[9]** Samsung, 2023. Engenheiros colaram código-fonte de semicondutores e atas de reunião no ChatGPT; a empresa proibiu IA generativa nos dispositivos corporativos. Bloomberg, 2 maio 2023: [bloomberg.com](https://www.bloomberg.com/news/articles/2023-05-02/samsung-bans-chatgpt-and-other-generative-ai-use-by-staff-after-leak).
> Dado sensível enviado a um LLM em nuvem é dado que saiu da empresa. → princípio 6.

**[10]** MANDIANT. *UNC5537 Targets Snowflake Customer Instances for Data Theft and Extortion.* jun. 2024. [cloud.google.com/blog](https://cloud.google.com/blog/topics/threat-intelligence/unc5537-snowflake-data-theft-extortion).
> Cerca de 165 organizações expostas com credenciais roubadas por infostealers; dados concentrados num serviço em nuvem viraram alvo único. → princípios 1 e 2.

**[11]** CISA. *Advanced Persistent Threat Compromise of Government Agencies, Critical Infrastructure, and Private Sector Organizations (SolarWinds)*, AA20-352A, 2020. [cisa.gov](https://www.cisa.gov/news-events/cybersecurity-advisories/aa20-352a).
> Uma atualização automática foi o vetor de ataque. → princípio 7.

**[12]** CrowdStrike, jul. 2024. Uma atualização de conteúdo distribuída automaticamente derrubou cerca de 8,5 milhões de máquinas Windows. [crowdstrike.com/falcon-content-update-remediation-and-guidance-hub](https://www.crowdstrike.com/falcon-content-update-remediation-and-guidance-hub/).
> Atualização que chega sem ação do usuário também é risco de disponibilidade. → princípio 7.
