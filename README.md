# avaliar-ferramenta

Skill para Claude Code que avalia, antes de instalar, skills, plugins, servidores MCP, repositórios, CLIs e "prompts prontos" recomendados em posts e reels.

Ela troca popularidade (estrelas, instalações) por evidência lida e medida: o que a ferramenta instala de verdade, o que roda sozinho, onde a instalação cai, quanto pesa em toda sessão, o que repete do que já está instalado e se serve para o uso de quem pergunta. A resposta sai em veredito (vale / talvez / lixo) com o motivo de cada item.

## Instalação

```bash
git clone https://github.com/diegocamara89/avaliar-ferramenta ~/.claude/skills/avaliar-ferramenta
```

Dispara sozinha quando você manda uma ferramenta para avaliar ("vale instalar?", "isso presta?").

Usa, quando disponível, a skill `transcrever-video` para reels e o GitHub CLI (`gh`) para ler repositórios.

## Licença

MIT
