---
description: Pega 1 conteúdo existente (URL, arquivo, vídeo, post) e gera 8 derivados em formatos diferentes — carrossel IG, post LinkedIn, Reel, Short, blog, email, thread, ad. Cada peça respeita o canal, não é cópia.
argument-hint: [URL ou caminho do arquivo de origem — ex: "https://blog.exemplo.com/artigo-x" ou "./artigos/post.md"]
---

# /repurpose

Pega **1 fonte** e transforma em **8 peças** distintas, cada uma adaptada ao canal. Não é cópia — é tradução criativa.

## Por que repurpose

- 1 conteúdo bem feito alimenta 2-4 semanas de feed
- Cada canal tem quem só consome lá (não cruza com outros)
- ROI por minuto de criação altíssimo

## Argumento

`$ARGUMENTS` — pode ser:
- URL de blog/artigo
- Caminho local pra arquivo .md, .txt, .pdf
- URL de vídeo YouTube
- URL de Reel/post IG público
- Texto colado direto (se < 5000 chars)

## Pipeline

### Etapa 0 — Brand-context

Lê. Se vazio, PARA (padrão).

### Etapa 1 — Pega o conteúdo de origem

Dependendo do tipo de input:

| Input              | Como obter                                |
| ------------------ | ----------------------------------------- |
| URL                | `WebFetch` no link                        |
| Arquivo local      | `Read` no caminho                         |
| YouTube            | `WebFetch` na página (pega title/description) |
| Texto inline       | Use direto                                |

Se não conseguiu, fala com o usuário:
> "Não consegui acessar [origem]. Cola o texto direto na próxima mensagem ou me passa um caminho local."

### Etapa 2 — Identifica os 3-5 "núcleos" do conteúdo

Antes de gerar derivados, identifica as **ideias-chave** do material original. Isso vira a "spine" pra todas as peças.

Pergunta-se:
- Qual o ângulo central?
- Qual a tese / posicionamento?
- Tem dado/número específico que funciona em qualquer canal?
- Tem case ou exemplo que dá pra extrair?
- Tem frase memorável que vira hook?

Lista esses 3-5 núcleos num arquivo: `output/[data]-repurpose-[slug]/00-nucleos.md`.

### Etapa 3 — Briefing breve do estrategista (rápido)

Aciona `subagent_type: estrategista` com prompt:

```
Tarefa: produzir BRIEFING DE REPURPOSE.

Conteúdo original: [cole ou referencia o arquivo]
Núcleos identificados: [da etapa 2]

Saída esperada: pra cada um dos 8 formatos abaixo, define:
- Qual núcleo do original ele explora
- Qual ângulo específico (não pode ser igual a outro derivado)
- CTA esperado

Formatos:
1. Carrossel IG (10 slides) — desenvolve 1 núcleo profundo
2. Reel IG (30s) — recorta 1 ideia provocativa
3. Post LinkedIn (~1000 chars) — versão "executivo brasileiro"
4. Carrossel LinkedIn (8 slides) — versão B2B do tema
5. Short YouTube (60s) — versão pra YT
6. Blog enxuto (800 palavras) — só se a fonte original NÃO for blog
7. Email newsletter (350 palavras) — versão íntima/conversacional
8. Ad em vídeo 15s — recorta hook + promessa pra meta/yt ads

Se algum formato NÃO faz sentido pra essa fonte específica, recuse e justifique.
```

### Etapa 4 — Mostra plano ao usuário

```
Repurpose plan — 8 derivados:

[mostra a tabela do estrategista: formato | núcleo | ângulo | CTA]

⚠️ [Se algum formato foi recusado pelo estrategista, mostra aqui com justificativa]

Confirma "vai" pra produzir tudo, ou pede pra cortar/ajustar formato.
```

Espera confirmação.

### Etapa 5 — Produção em paralelo

Aciona TODOS os produtores num único bloco:
- Carrossel IG → `copywriter-instagram`
- Reel IG → `roteirista-video` + `copywriter-instagram` (legenda)
- Post LinkedIn → `copywriter-linkedin`
- Carrossel LinkedIn → `copywriter-linkedin`
- Short YT → `roteirista-video`
- Blog enxuto → `redator-blog`
- Email → `copywriter-instagram` (mais versátil pra esse formato)
- Ad vídeo 15s → `roteirista-video`

Cada um recebe:
- O briefing de repurpose específico do estrategista
- Núcleo extraído da fonte
- Brand-context relevante
- Caminho pra salvar

### Etapa 6 — Editor revisa todas em paralelo

Pra cada peça, aciona `editor-revisor`. Reprovações tratadas como nos outros comandos.

### Etapa 7 — README + sequência de publicação

Cria `output/[data]-repurpose-[slug]/README.md`:

```markdown
# Repurpose — [tema da fonte] — [data]

## Fonte original
[URL / caminho]
[Resumo de 1 parágrafo do que era]

## Núcleos extraídos
1. [núcleo 1]
2. [núcleo 2]
3. [núcleo 3]

## 8 peças derivadas

| # | Formato              | Arquivo                     | Núcleo | Status |
| - | -------------------- | --------------------------- | ------ | ------ |
| 1 | Carrossel IG         | ig-carrossel.md             | #1     | ✅     |
| 2 | Reel IG              | ig-reel.md                  | #2     | ✅     |
| ...| ...                 | ...                         | ...    | ...    |

## Sequência sugerida de publicação (4 semanas)

**Semana 1 (apresentação):**
- Seg: Reel IG (puxa atenção pro tema)
- Qua: Post LinkedIn (versão B2B)
- Sex: Email newsletter

**Semana 2 (aprofundamento):**
- Ter: Carrossel IG (núcleo principal)
- Qui: Carrossel LinkedIn

**Semana 3 (alcance ampliado):**
- Seg: Short YouTube
- Qua: Blog (se a fonte não era blog)

**Semana 4 (conversão):**
- Ter: Ad em vídeo (campanha paga)

## O que ficou de fora
- [decisões e por quê]
```

### Etapa 8 — Entrega final

```
Pronto. 8 peças derivadas em `output/[data]-repurpose-[slug]/`

[lista de arquivos]

Sequência de 4 semanas no README.md.

⚠️ Pontos pra você decidir:
- [se há decisão pendente, ex: "trocar @perfil tagueado em algum slide"]

Próximo: quer que eu agende essas peças no [calendário/ferramenta], ou só publica manualmente?
```

## Princípios

- **Adaptação > tradução literal.** Cada canal tem regras próprias. Repurpose ruim copia o blog inteiro pro LinkedIn.
- **Cada peça stand-alone.** Funciona sem ter visto a fonte original.
- **Não enxe linguiça pra chegar em 8 peças.** Se 6 fazem sentido e 2 não, recusa as 2.
- **Sequência importa.** A ordem de publicação amplia ou destrói o efeito do conjunto.
- **Atribui crédito.** Se a fonte é externa (artigo de outro autor), cita.
