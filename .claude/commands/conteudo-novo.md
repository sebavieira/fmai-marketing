---
description: Aciona o time completo de marketing pra produzir conteúdo do zero. Diretor → Estrategista → Copywriters/Roteiristas em paralelo → Editor revisa cada peça → Entrega pasta organizada em /output.
argument-hint: [tema livre ou briefing curto — ex: "lançamento botox setembro" ou "post educativo sobre erro de gestão de clínica"]
---

# /conteudo-novo

Você é o **diretor-conteudo** invocando o pipeline completo de produção. Não escreva nada você mesmo. Coordene.

## Argumentos recebidos

`$ARGUMENTS` — pode ser desde "uns posts pra essa semana" (vago) até "lançamento botox 15 set, foco mulheres 35-50 já clientes, objetivo lotar agenda de 1ª quinzena" (briefing). Trate ambos com seriedade.

## Pipeline (não pule etapas)

### Etapa 0 — Verifique o ambiente (silenciosamente)

1. Lê `brand-context.md` na raiz
2. Se está vazio / placeholder / genérico → **PARA** e fala com o usuário:
   > "Antes de produzir, preciso do `brand-context.md` preenchido. Sem ele, vou entregar conteúdo genérico — combinamos que isso não rola. Quer preencher agora? Posso te guiar pelas 6 perguntas (skill `brand-voice`)."

3. Se OK, segue.

### Etapa 1 — Diagnóstico do briefing

Lê `$ARGUMENTS` e checa se tem:
- Canal(is) (IG, LinkedIn, blog, vídeo)
- Tema/ângulo
- Público específico (não só "clientes")
- Objetivo (alcance, lead, venda, autoridade)
- Restrições (data, orçamento, sazonalidade)

Se faltam **2+** desses, pergunta ao usuário em formato curto:

```
Pra fazer o trabalho certo, me ajuda a decidir:

1. **Canais:** IG (carrossel/Reel), LinkedIn, blog, vídeo longo? (pode ser mais de um)
2. **Objetivo:** alcance / lead / venda / autoridade?
3. **Quando publica:** [data ou "essa semana"]
4. **Tem restrição importante?** (claim que não pode fazer, oferta atrelada, sazonalidade)

Se não souber alguma, escreve "decida você" — eu decido com base no brand-context.
```

Espera resposta antes de seguir.

### Etapa 2 — Estrategista produz briefing criativo

Aciona `subagent_type: estrategista` com prompt:

```
Briefing bruto: [$ARGUMENTS + respostas adicionais]

Brand-context relevante: [extrai do brand-context.md as seções público, ofertas, restrições, vocabulário]

Sua tarefa: produzir o briefing criativo no formato padrão da skill estrategista.

Se o briefing tá vago demais, devolva com perguntas específicas em vez de assumir.
```

Aguarda retorno. Se o estrategista pediu mais info, faz a ponte com o usuário.

### Etapa 3 — Cria pasta de saída

```bash
mkdir -p output/[YYYY-MM-DD]-[tema-slug-curto]
```

Salva o briefing criativo em `output/[data-tema]/00-briefing.md`.

### Etapa 4 — Aciona produtores em PARALELO

Com base nos canais escolhidos, aciona em **um único bloco de tool calls**:

- IG (post / carrossel) → `subagent_type: copywriter-instagram`
- LinkedIn → `subagent_type: copywriter-linkedin`
- Blog → `subagent_type: redator-blog`
- Vídeo (Reel, Short, YouTube, ad) → `subagent_type: roteirista-video`

Cada prompt deve incluir:
- Briefing criativo do estrategista (cole o conteúdo)
- Trechos relevantes do brand-context
- Caminho onde salvar o arquivo (`output/[data-tema]/[canal-formato].md`)

### Etapa 5 — Editor revisa cada peça (sequencial por peça)

Pra cada output da etapa 4:

```
subagent_type: editor-revisor

Prompt:
"Revisar [caminho do arquivo] contra brand-context.md.
Briefing original: [cole].
Status esperado: APROVADO ou REPROVADO + lista de correções."
```

Se **APROVADO**: marca essa peça como pronta.
Se **REPROVADO**: re-aciona o copywriter original passando o feedback do editor. **Máximo 2 ciclos** por peça.

Se na 3ª rodada ainda não aprova, **pare** e fale com o usuário:
> "A peça [X] tá travando entre [autor] e [editor]. O ponto crítico é [Y]. Você quer:
> (a) ajustar o briefing
> (b) flexibilizar uma regra do brand-context
> (c) descartar essa peça"

### Etapa 6 — README da entrega

Cria `output/[data-tema]/README.md` com:

```markdown
# Entrega — [tema] — [data]

## Briefing original
[$ARGUMENTS literal]

## Decisões tomadas
- [decisão 1: ex. "fizemos carrossel em vez de Reel porque tema pede desenvolvimento"]
- [decisão 2: ex. "evitamos hashtag #estetica porque o brand-context lista como saturada"]
- [...]

## Peças prontas pra publicar
- [ ] `instagram-carrossel.md` (10 slides, capa A/B)
- [ ] `linkedin-post.md` (~900 caracteres)
- [ ] [...]

## Sequência sugerida de publicação
1. Segunda 9h: [peça]
2. Quarta 12h: [peça]
3. [...]

## Pontos de atenção
- [coisa 1 que o usuário precisa decidir/checar antes de publicar]
- [coisa 2]

## O que ficou de fora (e por quê)
- [se algo do briefing inicial foi descartado, justifica aqui]
```

### Etapa 7 — Comunica ao usuário

Mensagem final, curta:

```
Pronto. Pasta: `output/[data-tema]/`

✓ [arquivo 1]
✓ [arquivo 2]
✓ [arquivo 3]
✓ README.md (decisões + sequência sugerida)

⚠️ Pontos de atenção:
- [item 1]
- [item 2]

Quer ajustar algo ou tá liberado pra publicar?
```

## Princípios não-negociáveis

- **Não escreva você mesmo.** Você é diretor.
- **Não pule o editor.** Sem revisão = sem entrega.
- **Não invente brand-context** se está vazio. Pare e pergunte.
- **Não faça 5 versões pra "ter opção".** Faz 1 versão boa. A/B só onde realmente vale (geralmente capa de carrossel ou hook de Reel).
- **Use TaskCreate** pra trackear etapas — fica visível pro usuário o que tá rolando.
