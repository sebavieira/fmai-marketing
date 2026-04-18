---
description: Versão express — pula estrategista e editor, vai direto pro copywriter/roteirista certo. Use quando o briefing já está claro e você quer 1 peça em poucos minutos. NÃO use pra peças críticas/lançamento.
argument-hint: [tipo] [tema] — ex: "carrossel-ig 5 erros de gestão de clínica" ou "post-linkedin lançamento da agenda 2026"
---

# /conteudo-rapido

Versão **express** do pipeline. Pula estratégia formal e revisão. **Você assume o risco** de qualidade.

## Quando usar essa versão

- Você já tem o ângulo definido na cabeça
- Peça é tática, não estratégica (não é lançamento, não é institucional)
- Você vai revisar pessoalmente antes de publicar
- Tá com pressa real

## Quando NÃO usar (use `/conteudo-novo`)

- Lançamento de produto/serviço
- Conteúdo institucional / posicionamento
- Peça que vai pro CEO/sócio aprovar
- Tema novo onde você não tem ângulo claro

## Argumentos

`$ARGUMENTS` — formato `[tipo] [tema/ângulo]`. Tipos aceitos:

| Tipo                    | Aciona                                    |
| ----------------------- | ----------------------------------------- |
| `feed-ig`               | copywriter-instagram                      |
| `carrossel-ig`          | copywriter-instagram                      |
| `reel`                  | roteirista-video + copywriter-instagram (legenda) |
| `post-linkedin`         | copywriter-linkedin                       |
| `carrossel-linkedin`    | copywriter-linkedin                       |
| `blog`                  | redator-blog                              |
| `short` / `tiktok`      | roteirista-video                          |
| `youtube`               | roteirista-video                          |
| `ad-meta` / `ad-yt`     | roteirista-video                          |
| `email`                 | copywriter-instagram (versátil) ou redator-blog (longo) |

## Pipeline express

### Etapa 0 — Verifica brand-context (rápido)

Lê `brand-context.md`. Se tá obviamente vazio (placeholders), **PARA**:

> "Brand-context tá vazio. Pra ir rápido vou precisar disso preenchido. Quer rodar `/conteudo-novo` pra eu te guiar, ou você preenche e a gente continua?"

Se tá preenchido (mesmo se imperfeito), segue.

### Etapa 1 — Diagnóstico mínimo

Se `$ARGUMENTS` tem só tipo e tema vago ("carrossel-ig dicas de marketing"), pede ao usuário em **1 mensagem curta**:

```
Pra ser rápido, preciso saber:
- Ângulo específico? (ex: "5 erros que clínica de estética comete em IG")
- Pra quem? (público específico)
- CTA? (comentar, salvar, link na bio, agendar)

Responde em 1 linha cada.
```

Se `$ARGUMENTS` já tem ângulo claro, segue direto.

### Etapa 2 — Aciona o agente certo (UM SÓ)

Não chama estrategista. Não chama editor. Você manda direto pro produtor com prompt completo:

```
Subagent: [agente correspondente ao tipo]

Prompt:
"PEÇA EXPRESS — sem revisão do editor.

Tipo: [tipo solicitado]
Tema/ângulo: [extraído de $ARGUMENTS + respostas]
Público: [se mencionado, ou pega do brand-context]
CTA: [se mencionado, ou pega do brand-context]

Brand-context relevante:
- Tom: [extrai]
- Vocabulário SIM/NÃO: [extrai]
- Restrições do nicho: [extrai]

Salva em: output/[YYYY-MM-DD]-rapido-[slug]/[tipo].md

⚠️ Importante: aplica anti-IA checklist da sua skill antes de entregar. Não vou ter editor revisando."
```

### Etapa 3 — Entrega ao usuário

```
Pronto. Express:

✓ output/[data]-rapido-[slug]/[arquivo].md

⚠️ Sem revisão do editor — dá uma lida antes de publicar. Pontos pra checar:
- [hook tá forte?]
- [CTA tá específico?]
- [tom bate com o que vc espera?]

Se quiser revisão formal, roda `/conteudo-novo` com o mesmo briefing.
```

## Princípios

- **Você é diretor**, mas tá no modo "atalho consciente"
- **Não chame editor**, é express
- **Não rode A/B**, é express
- **Avise o usuário** sempre que pulou revisão
- Se o tema chegar grande/sensível ("lançamento", "pivô da marca"), **recuse e sugira `/conteudo-novo`**
