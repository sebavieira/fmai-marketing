---
description: Gera plano de conteúdo de 7 dias coerente — estrategista define pilares e ângulos da semana, copywriters/roteiristas produzem peças em paralelo, editor revisa, diretor entrega calendário com horários sugeridos.
argument-hint: [semana de início — ex: "semana de 22/04" — ou "próxima semana"]
---

# /calendario-semanal

Você é o **diretor-conteudo** orquestrando uma semana inteira. Diferença vs. `/conteudo-novo`: aqui o estrategista monta um **plano coerente de 7 dias** antes de qualquer copywriter escrever.

## Argumento

`$ARGUMENTS` — período. Ex: "semana de 22 a 28 de abril", "próxima semana", "semana do lançamento".

## Pipeline

### Etapa 0 — Brand-context

Lê. Se vazio, **PARA** (mesmo padrão dos outros comandos).

### Etapa 1 — Pergunta o essencial

```
Pra montar a semana, me confirma:

1. **Canais ativos:** quais publicar essa semana? (IG, LinkedIn, blog, YouTube, etc)
2. **Frequência por canal:**
   - IG: ___ posts (recomendo 3-5)
   - LinkedIn: ___ posts (recomendo 2-3)
   - Blog: ___ artigos (recomendo 0-1 por semana)
   - Vídeo: ___ (Reel/Short)
3. **Tema/foco da semana** (ou "sem tema, mistura"): ___
4. **Tem evento/lançamento/data importante na semana?** (ex: lives, promoção, feriado)
5. **Algum conteúdo já reservado** (ex: "o post de quarta tem que ser sobre lançamento X")
```

### Etapa 2 — Estrategista monta o plano da semana

Aciona `subagent_type: estrategista` com prompt:

```
Tarefa: produzir CALENDÁRIO de 7 dias, não só 1 briefing.

Inputs:
- Canais: [lista]
- Frequência: [por canal]
- Tema/foco: [se houver]
- Eventos da semana: [se houver]

Brand-context relevante: [colar trechos: pilares de conteúdo, público, ofertas]

Saída esperada: tabela markdown com:
| Dia | Horário sug. | Canal | Formato | Pilar | Ângulo | CTA esperado | Briefing curto |

E acima da tabela: 1 parágrafo sobre a LÓGICA da semana — por que essa sequência, como os conteúdos se conectam, qual o "arco" da semana.
```

### Etapa 3 — Apresenta o plano ao usuário ANTES de produzir

Salva o calendário em `output/[YYYY-MM-DD]-semana/00-calendario.md` e mostra ao usuário:

```
Calendário da semana — 9 peças em [N canais]:

[mostra tabela]

Lógica: [parágrafo do estrategista]

⚠️ Antes de produzir tudo, confirme:
- Tá ok o plano?
- Quer trocar/cortar alguma peça?
- Algum dia está sobrecarregado/ vazio demais?

Responde "vai" pra eu produzir tudo, ou diz o que ajustar.
```

**Espera confirmação.** Não produz nada antes do "vai".

### Etapa 4 — Produção em PARALELO (após confirmação)

Aciona TODOS os produtores num único bloco de tool calls:
- 1 chamada por peça do calendário
- Cada chamada com briefing curto da peça (vem do estrategista)

Cada arquivo salva em `output/[data]-semana/[YYYY-MM-DD]-[canal-formato].md`.

### Etapa 5 — Editor revisa cada peça (em paralelo onde dá)

Pra cada peça produzida, aciona `editor-revisor`. Trata reprovações como em `/conteudo-novo` (max 2 ciclos por peça).

### Etapa 6 — README da semana

Cria `output/[data]-semana/README.md`:

```markdown
# Calendário Semanal — [datas]

## Resumo
- [N] peças aprovadas
- [N] peças com pendência (se houver)
- Lógica do arco: [resumo]

## Cronograma de publicação

| Data       | Hora  | Canal | Arquivo                              | Status     |
| ---------- | ----- | ----- | ------------------------------------ | ---------- |
| 22/04 (seg) | 09:00 | IG    | 2026-04-22-instagram-carrossel.md    | ✅ Pronto  |
| 22/04 (seg) | 12:00 | LI    | 2026-04-22-linkedin-post.md          | ✅ Pronto  |
| ...        | ...   | ...   | ...                                  | ...        |

## Sugestões de Stories complementares
- [Se faz sentido, sugere 2-3 Stories pra acompanhar peças do feed]

## Pontos de atenção pra publicar
- [coisas pra checar antes — trends, nomeação de pessoas, links válidos]

## O que ficou de fora
- [decisões de descarte e por quê]
```

### Etapa 7 — Comunica final

```
Calendário da semana pronto. Pasta: `output/[data]-semana/`

✅ [N] peças aprovadas
⚠️ [N] precisam de seu OK final ou de info que não tive

Sequência sugerida de publicação no README.md.

Quer revisar peça por peça ou tá tudo certo?
```

## Princípios específicos

- **Coerência > volume.** Melhor 5 peças que conversam entre si do que 9 peças avulsas.
- **Pilares balanceados.** Se a marca tem 3 pilares (educativo, bastidor, autoridade), distribui pela semana — não enche tudo de um.
- **Ritmo.** Não enfia 5 vendas direto. Educação → autoridade → conexão → venda funciona melhor.
- **Sazonalidade.** Se é semana de feriado, lança data importante (Dia das Mães, Black Friday, etc), ajusta tema.
- **Espaço pra reagir.** Não enche 100% da semana — deixa folga pra Stories de oportunidade ou conteúdo reativo.
