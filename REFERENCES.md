# References

The theory, standards and incidents behind the [manifesto](README.md#the-also-local-manifesto). Bracketed numbers are cited in the README.

## Foundations

**[1]** KLEPPMANN, M.; WIGGINS, A.; VAN HARDENBERG, P.; McGRANAGHAN, M. *Local-first software: you own your data, in spite of the cloud.* Onward! '19, ACM SIGPLAN, Athens, 2019, pp. 154–178. DOI: [10.1145/3359591.3359737](https://doi.org/10.1145/3359591.3359737). Open version: [inkandswitch.com/local-first](https://inkandswitch.com/local-first/).
> The paper that named the movement. With cloud software, if the service goes away, so does access to your own data; local storage should come first. → principles 1, 2, 3.

**[2]** STALLMAN, R. *Who does that server really serve?* GNU Project / Boston Review, 2010 (revised 2013 and 2023). [gnu.org/philosophy/who-does-that-server-really-serve.html](https://www.gnu.org/philosophy/who-does-that-server-really-serve.html).
> Defines SaaSS (*Service as a Software Substitute*): doing your computing on someone else's server hands them your data. → principle 1.

**[3]** SALTZER, J. H.; SCHROEDER, M. D. *The protection of information in computer systems.* Proceedings of the IEEE, 63(9), pp. 1278–1308, 1975. DOI: [10.1109/PROC.1975.9939](https://doi.org/10.1109/PROC.1975.9939).
> The classic principles of fail-safe defaults, least privilege and economy of mechanism. → principles 4, 9.

## Standards and guidance

**[4]** CISA et al. *Shifting the Balance of Cybersecurity Risk: Principles and Approaches for Secure by Design Software.* Apr. 2023, updated Oct. 2023. [cisa.gov/resources-tools/resources/secure-by-design-and-default](https://www.cisa.gov/resources-tools/resources/secure-by-design-and-default).
> Secure by default: products should resist exploitation without reconfiguration, and security shouldn't be the customer's burden alone. → principles 4, 8.

**[5]** BRAZIL. *Law No. 13,709/2018 (LGPD)*, art. 6, III (necessity) and art. 46, §2 (security by design). [planalto.gov.br](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm).
> Data minimization and security by design as legal obligations. → principle 3.

**[6]** EUROPEAN UNION. *Regulation (EU) 2016/679 (GDPR)*, art. 25: data protection by design and by default. [eur-lex.europa.eu](https://eur-lex.europa.eu/eli/reg/2016/679/oj).
> The European counterpart to [5]. → principle 3.

**[7]** NIST. *SP 800-207: Zero Trust Architecture.* 2020. DOI: [10.6028/NIST.SP.800-207](https://doi.org/10.6028/NIST.SP.800-207).
> No network is trusted by default. → principle 6.

**[8]** OWASP. *Top 10 for LLM Applications 2025*, LLM02: Sensitive Information Disclosure. [genai.owasp.org](https://genai.owasp.org/llm-top-10/).
> LLMs can expose confidential data sent to them; the item rose four places from 2024. → principle 7.

## Incidents

**[9]** Samsung, 2023. Engineers pasted semiconductor source code and meeting notes into ChatGPT; the company banned generative AI on corporate devices. Bloomberg, May 2, 2023: [bloomberg.com](https://www.bloomberg.com/news/articles/2023-05-02/samsung-bans-chatgpt-and-other-generative-ai-use-by-staff-after-leak).
> Sensitive data sent to a cloud LLM has left the company. → principle 7.

**[10]** MANDIANT. *UNC5537 Targets Snowflake Customer Instances for Data Theft and Extortion.* June 2024. [cloud.google.com/blog](https://cloud.google.com/blog/topics/threat-intelligence/unc5537-snowflake-data-theft-extortion).
> About 165 organizations exposed through infostealer credentials; data concentrated in one cloud service became a single target. → principles 1, 3.

**[11]** CISA. *Advanced Persistent Threat Compromise of Government Agencies, Critical Infrastructure, and Private Sector Organizations (SolarWinds)*, AA20-352A, 2020. [cisa.gov](https://www.cisa.gov/news-events/cybersecurity-advisories/aa20-352a).
> An automatic update was the attack vector. → principle 8.

**[12]** CrowdStrike, July 2024. An automatically distributed content update crashed about 8.5 million Windows machines. [crowdstrike.com](https://www.crowdstrike.com/falcon-content-update-remediation-and-guidance-hub/).
> Updates that arrive without user action are an availability risk too. → principle 8.
