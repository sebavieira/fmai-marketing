---
name: seo-pt-br
description: SEO + AEO/GEO (Answer Engine Optimization, Generative Engine Optimization) para o mercado brasileiro. Use ao escrever blog, página de site, ou qualquer conteúdo que precisa ranquear no Google ou ser citado por ChatGPT, Perplexity, Claude e Gemini. Cobre keyword research pt-BR, estrutura de artigo, otimização AEO e checklist técnico.
---

# SEO + AEO em Português Brasileiro

## Quando usar

- Redator-blog escrevendo qualquer artigo
- Criando página de site (institucional, serviço, produto)
- Otimizando conteúdo existente
- Decidindo qual keyword atacar antes de escrever

## Diferença SEO vs AEO/GEO (importante em 2026)

| SEO clássico                | AEO / GEO (novo)                                       |
| --------------------------- | ------------------------------------------------------ |
| Otimiza pra ranquear no Google | Otimiza pra ser citado em respostas de IA           |
| Foco em backlinks, keyword density | Foco em estrutura clara, definições, FAQ        |
| Tráfego direto → seu site   | Citação → autoridade + tráfego indireto                |
| KPI: clique no resultado    | KPI: aparecer na resposta + ser linkado quando relevante |

**Você otimiza pros dois ao mesmo tempo.** As práticas se sobrepõem em ~70%.

---

## Keyword research pt-BR

### Onde buscar
- **Google Suggest** (digita a keyword + espaço, vê sugestões)
- **People Also Ask** (perguntas relacionadas no Google)
- **Google Trends** com filtro Brasil — pra ver sazonalidade e regionalidade
- **Ubersuggest** (free tier) — volume + dificuldade
- **Answer The Public** (free tier limitado) — ótimo pra perguntas
- **Resposta no ChatGPT/Perplexity**: pergunta "quais são as principais dúvidas sobre [tema] no Brasil"

### Específico do mercado BR

- **Variação regional**: "guaraná" vs "guaraná natural", "biscoito" vs "bolacha", "abóbora" vs "jerimum". Pesquise as duas formas.
- **Gíria + termo técnico**: muita gente busca em gíria ("emagrecer barriga rápido") mas profissional pesquisa em termo técnico ("redução de gordura abdominal"). Decida quem você quer atrair.
- **Singular vs plural**: o Google trata diferente. "clínica de estética em brasília" ≠ "clínicas de estética em brasília". Geralmente o **plural** tem mais volume comercial.
- **Localidade**: keywords + cidade/estado funcionam muito bem pra negócio local. "[serviço] em [cidade]" é o padrão de fundo de funil.
- **Linguagem natural pra AEO**: pessoas perguntam pra IA com frases inteiras. Otimize pra "como faço pra X" (não só "como X").

### Tipos de keyword (intenção de busca)

| Tipo            | Exemplo                                  | Pra que tipo de conteúdo            |
| --------------- | ---------------------------------------- | ----------------------------------- |
| Navegacional    | "instagram login"                        | Geralmente não faz sentido competir |
| Informacional   | "o que é botox", "como funciona ozempic" | Blog de topo de funil              |
| Comercial       | "melhor clínica botox", "comparativo X"  | Blog de meio/fundo                  |
| Transacional    | "agendar botox brasília", "comprar X"    | Página de serviço/produto           |

---

## Estrutura de artigo que ranqueia E é citado por IA

### Esqueleto

```
H1 com keyword principal (única no artigo)
↓
TL;DR no topo (3-5 bullets) — RESPOSTA DIRETA — IA AMA ISSO
↓
Intro curta (2-3 parágrafos), com keyword nos primeiros 100 palavras
↓
H2 com keyword secundária + resposta direta na primeira frase
   H3 com sub-tópico
   H3 com sub-tópico
↓
H2 com keyword secundária + caso/exemplo concreto
↓
H2 — Erros comuns / o que NÃO fazer
↓
H2 — Tabela ou checklist (estruturado, IA copia)
↓
Conclusão curta
↓
H2 — FAQ (3-7 perguntas em linguagem natural)
↓
Fontes citadas
```

### Por que essa estrutura funciona pros dois

- **TL;DR no topo**: featured snippet do Google + resposta de IA copia literalmente
- **H2 começando com resposta**: direto ao ponto, melhora dwell time E facilita extração por IA
- **Tabelas/listas**: Google rankeia bem + IA cita como estrutura
- **FAQ**: schema FAQPage no Google + AI gera respostas com base em FAQs
- **Fontes citadas**: aumenta E-E-A-T (Experience, Expertise, Authoritativeness, Trust) + IA prefere conteúdo que cita fonte

---

## Densidade e uso de keyword

- **Keyword principal**: 0.5%-1.5% do texto. Em artigo de 1.500 palavras, isso é 7-22 ocorrências.
- **Variações semânticas**: use 3-5 sinônimos/termos relacionados. Google usa LSI/embeddings, não conta repetição literal.
- **Aparição em**:
  - H1 (uma vez)
  - Primeiro parágrafo (primeiras 100 palavras)
  - Pelo menos 2 H2
  - Meta description (150-160 caracteres)
  - Slug da URL (curta, com keyword, hífens)
  - Alt text de pelo menos 1 imagem
  - Texto âncora de pelo menos 1 link interno (se aplicável)

**Não force.** Se ler pesado/repetitivo, refaça. Google penaliza keyword stuffing.

---

## Otimização específica pra AEO (ser citado por IA)

### O que faz IA citar você

1. **Resposta direta no início.** IA escaneia primeiros parágrafos buscando resposta clara à query. Enrolação = não citado.
2. **Estrutura semântica clara.** H1 → H2 → H3 hierárquico. Listas e tabelas estruturadas.
3. **Definições explícitas.** "X é Y." Frase curta, definitiva, em linha própria.
4. **FAQ no rodapé.** IA gosta de Q&A. Cada Q como H3, A começando com resposta.
5. **Dado citável**: número específico + fonte. "73% das clínicas X (segundo Y)" tem mais chance de ser citado que afirmação vaga.
6. **Frescura**: data visível no artigo. Conteúdo desatualizado é evitado por IA pra evitar dar info errada.
7. **Schema markup**: Article, FAQPage, HowTo, Product (depende do tipo). Você sugere, dev implementa.
8. **Autoridade do domínio**: IA prefere fonte respeitada. Não dá pra forçar — é fruto de tempo + qualidade.

### O que IA NÃO cita

- Conteúdo paywall (não consegue ler)
- Conteúdo carregado via JS sem SSR
- Texto em imagem (PNGs com texto)
- PDFs sem versão HTML
- Sites com anúncios bloqueando o conteúdo principal

---

## Meta description que funciona

- 150-160 caracteres (Google corta acima)
- Inclui keyword principal naturalmente
- Inclui benefício/promessa
- Inclui CTA implícito ("descubra", "veja", "aprenda")
- **Não é cópia da intro do artigo**

Exemplo bom: "Botox: como saber se você precisa, quanto custa em 2026 e por que escolher um profissional certo importa mais que a marca do produto. Guia completo."

Exemplo ruim: "Neste artigo, você vai aprender tudo sobre botox e seus benefícios. Confira!"

---

## Slug que funciona

- Curto: 3-5 palavras
- Sem stopwords desnecessárias ("o", "a", "de", "para") quando dá pra cortar
- Hífens, não underline
- Tudo minúsculo, sem acento
- Inclui a keyword principal

Exemplos:
- ✅ `/botox-quanto-custa`
- ✅ `/clinica-estetica-brasilia`
- ❌ `/o-que-e-o-botox-e-como-ele-funciona-no-rosto-de-uma-pessoa`
- ❌ `/post-2026-04-17-botox`

---

## FAQ no rodapé — formato

Cada pergunta como H3. Resposta direta na primeira frase. Pode expandir depois.

```markdown
### Quanto custa botox em Brasília em 2026?
Em Brasília, o botox custa entre R$ 1.200 e R$ 3.500 por aplicação completa, dependendo da clínica, da marca da toxina e do número de áreas. [Continua expandindo...]

### Botox dura quanto tempo?
A duração média é de 4 a 6 meses para a maioria das pessoas, podendo chegar a 8 meses em quem aplicou várias vezes consecutivas. [Expansão...]
```

Pergunta:
- Em linguagem natural (como pessoa pergunta no Google ou ChatGPT)
- Inclui keyword/variação quando faz sentido
- Curta (até 12 palavras idealmente)

---

## Checklist técnico (você sugere, dev implementa)

- [ ] Tag `<title>` única, 50-60 caracteres
- [ ] Meta description 150-160 caracteres
- [ ] Canonical URL definida
- [ ] OpenGraph + Twitter Card pra preview de redes
- [ ] Schema Article + FAQPage (mínimo)
- [ ] Imagens com alt text descritivo + lazy loading
- [ ] HTTPS, mobile-friendly, Core Web Vitals OK
- [ ] Internal links pra outros artigos relacionados
- [ ] Updated date visível no artigo
- [ ] Autor visível (autoridade)
- [ ] Sitemap atualizado

---

## Anti-padrões SEO 2026

- ❌ Encher de keyword "burra" (Google detecta)
- ❌ Escrever pra Google em vez de pra pessoa
- ❌ Backlinks comprados em PBN (penalização garantida)
- ❌ Conteúdo gerado por IA sem revisão humana (Google detecta padrão)
- ❌ Copiar estrutura do top 1 sem agregar nada
- ❌ Artigos curtos (<500 palavras) tentando ranquear keyword competitiva
- ❌ "TL;DR" no fim do artigo (no fim não serve pra featured snippet)

---

## Script auxiliar: contar densidade de keyword

Salve como `check-density.sh` (ou Python equivalente) e rode pra checar densidade:

```bash
#!/bin/bash
# Uso: ./check-density.sh artigo.md "keyword principal"

ARQUIVO=$1
KEYWORD=$2

if [ -z "$ARQUIVO" ] || [ -z "$KEYWORD" ]; then
  echo "Uso: $0 artigo.md \"keyword\""
  exit 1
fi

TOTAL_PALAVRAS=$(wc -w < "$ARQUIVO")
OCORRENCIAS=$(grep -oi "$KEYWORD" "$ARQUIVO" | wc -l)
DENSIDADE=$(echo "scale=2; ($OCORRENCIAS / $TOTAL_PALAVRAS) * 100" | bc)

echo "Total de palavras: $TOTAL_PALAVRAS"
echo "Ocorrências de '$KEYWORD': $OCORRENCIAS"
echo "Densidade: $DENSIDADE%"
echo ""
if (( $(echo "$DENSIDADE < 0.5" | bc -l) )); then
  echo "⚠️  Densidade baixa — considere reforçar"
elif (( $(echo "$DENSIDADE > 1.5" | bc -l) )); then
  echo "⚠️  Densidade alta — risco de stuffing"
else
  echo "✅ Densidade ok (0.5%-1.5%)"
fi
```
