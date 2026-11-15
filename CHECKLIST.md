# Checklist LOCAL ONLY

Para entrar no hub, a ferramenta precisa marcar todos os itens obrigatórios.

## Obrigatórios
- [ ] Funciona com a rede bloqueada após a instalação (exceto os alvos que o usuário escolheu testar)
- [ ] Nenhuma telemetria ativa por padrão
- [ ] Dados e relatórios gravados localmente, em formato aberto
- [ ] Instalação e execução documentadas em até 3 comandos
- [ ] Servidores escutam em `127.0.0.1` por padrão
- [ ] Toda chamada de rede está listada no README

## Se usa LLM
- [ ] Aceita modelo local (Ollama / LM Studio / endpoint compatível com OpenAI)
- [ ] Tem um modo sem LLM ou dry-run que funciona offline

## Se é ofensiva
- [ ] Guarda de escopo fora do modelo, com bloqueio antes de qualquer I/O
- [ ] Dry-run ou aprovação humana por padrão

## Como verificar
```bash
# Linux: roda sem rede
unshare -rn <comando-da-ferramenta>
# macOS: Little Snitch / LuLu em modo bloqueio, ou desligar o Wi-Fi
```
