---
name: avaliar-ferramenta
description: Use quando o usuário mandar uma skill, plugin, servidor MCP, repositório, CLI, prompt pronto, lista de "comandos" ou post/reel recomendando ferramenta de IA, e perguntar se vale instalar, se presta ou se é lixo — ou pedir para instalar algo de terceiros. Também quando ele mandar vários links de uma vez para triagem.
---

# Avaliar ferramenta de IA antes de instalar

## Princípio

Instalar tem custo mesmo quando a ferramenta é boa: descrição lida em toda sessão, ações que rodam sozinhas, regras que brigam com as do usuário, skill que "rouba" o pedido de outra. O veredito sai de evidência lida e medida, nunca de popularidade.

## Roteiro (em ordem)

1. **Achar a fonte real.** Reel/post: transcreva com a skill `transcrever-video`. Repositório: `gh repo view <repo> --json isFork,parent,licenseInfo,pushedAt,createdAt`. Cópia/espelho (manifest, README ou badge apontando para outro dono; `createdAt == pushedAt`) → avalie o original, e diga que era cópia.
2. **Ler o que ele instala**, não o README: `SKILL.md`, `.claude-plugin/`, `hooks/`, `.mcp.json`/`server.json`, scripts de instalação. Anote tudo que roda sozinho (hooks, telemetria, auto-update, wizard que pede cookie/credencial) e o que envia código ou dados para fora.
3. **Ver onde a instalação cai.** Global? Só no projeto? Copia para outros programas de IA (`npx skills add` sem `-a claude-code`, `--all`)? Escreve no `CLAUDE.md` ou no `settings.json`? Plugin exige `/plugin` digitado pelo usuário.
4. **Comparar com o que já existe**, lendo na hora: `ls ~/.claude/skills`, plugins ativos, `CLAUDE.md`, memórias. Mesma função já coberta = repetição, não reforço.
5. **Medir o custo por sessão**: tamanho da `description` de cada skill (entra em toda sessão), nº de ferramentas de MCP, regras "sempre carregadas". Preferir CLI (custo zero) a skill quando der.
6. **Checar o encaixe no uso do usuário** (idioma, tipo de texto, área), pelo que a memória e o `CLAUDE.md` dizem dele — não pelo tema das sessões recentes, que mostra a fase, não o perfil. Regra de estilo em inglês costuma estragar texto formal em português.
7. **Ferramenta de código: testar numa cópia**, nunca no projeto original, e conferir o resultado por inspeção direta (resposta certa com confiança errada é pior que nada).

## Sinais que não provam qualidade

Estrelas, instalações, "oficial" no nome e "mais instalada do mundo" são contáveis, não confiáveis: repositório novo com milhares de estrelas promovendo produto pago é funil. Use como primeiro filtro, nunca como veredito. Não afirme que um número é "legítimo" — você não tem como saber.

## Alternativas passam pelo mesmo roteiro

Antes de recomendar o "original", a "versão completa" ou "copiar só as partes boas", rode os passos 2–5 nelas. Recomendação sem avaliação é chute.

## Formato da resposta

1. **Veredito numa linha**: vale / talvez (sob condição) / lixo para este usuário.
2. **Tabela** item → o que é → veredito → motivo concreto (arquivo lido, número medido).
3. **Versão mínima** quando só uma parte presta (ex.: uma linha no `CLAUDE.md`, instalar só no projeto, usar como CLI).
4. **Custo e alcance** da instalação, se recomendada: onde cai, quanto pesa por sessão, o que roda sozinho.
5. Separar o que foi **lido/medido** do que foi **inferido**.

Quando o veredito for "não vale", encerre no veredito e na versão mínima. Instalar é decisão do usuário: ofereça só se ele pedir.

## Erros comuns

| Erro | Correção |
|---|---|
| Avaliar o README e não o que instala | Ler hooks, manifests e scripts |
| "Tem 17 mil estrelas, deve ser bom" | Estrela é filtro, não prova |
| Recomendar o original de uma cópia sem olhar | Rodar o roteiro no original |
| Instalar no global por padrão | Projeto primeiro; global só com motivo |
| Achar que o instalador fez só o que prometeu | Conferir depois: skills, `CLAUDE.md`, outros programas |
| Aceitar "conferi" de subagente | Conferir o resultado (arquivo, imagem) você mesmo |
