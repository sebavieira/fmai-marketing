# fmai-marketing

Time de agentes orquestrado para criação de conteúdo de marketing em português brasileiro. Funciona dentro do **Claude Code** (CLI).

## O que tem aqui

```
.
├── .claude/
│   ├── agents/                     ← 8 agentes especializados
│   │   ├── diretor-conteudo.md     ← orquestrador (você fala com ele)
│   │   ├── estrategista.md         ← define ângulo, público, CTA
│   │   ├── copywriter-instagram.md
│   │   ├── copywriter-linkedin.md
│   │   ├── redator-blog.md
│   │   ├── roteirista-video.md
│   │   ├── editor-revisor.md       ← revisa tudo antes de entregar
│   │   └── analista-performance.md ← analisa dados reais
│   ├── skills/                     ← 7 skills reutilizáveis
│   │   ├── brand-voice/SKILL.md
│   │   ├── hooks-pt-br/SKILL.md
│   │   ├── seo-pt-br/SKILL.md
│   │   ├── cta-brasil/SKILL.md
│   │   ├── reels-shorts/SKILL.md
│   │   ├── carrossel-ig/SKILL.md
│   │   └── linkedin-br/SKILL.md
│   └── commands/                   ← 4 slash commands
│       ├── conteudo-novo.md
│       ├── conteudo-rapido.md
│       ├── calendario-semanal.md
│       └── repurpose.md
├── brand-context.md                ← cérebro de marca (você preenche)
├── CLAUDE.md                       ← regras gerais (idioma, ética, anti-IA)
└── output/                         ← entregas geradas, organizadas por data-tema
```

---

## Instalação

Pré-requisito: ter **Claude Code** instalado. Se não tem:
- macOS / Linux: `curl -fsSL https://claude.ai/install.sh | sh`
- Windows: baixa o app no claude.ai/code

Depois:

```bash
# 1. Clone ou copie a pasta deste projeto
cd /caminho/escolhido
# (se copiou pasta, pula o git)
git clone <repo-url> fmai-marketing
cd fmai-marketing

# 2. Abre o Claude Code aqui dentro
claude
```

Pronto. Os agentes/skills/commands são detectados automaticamente porque estão em `.claude/`.

---

## Uso (3 fluxos comuns)

### Fluxo 1 — Cliente novo, primeiro conteúdo

1. Edite `brand-context.md` substituindo o exemplo (Rita Trindade Clínica) pela sua marca/cliente.
   - Se não souber preencher, peça ao Claude: `lê a skill brand-voice e me faz as 6 perguntas pra extrair a voz da [nome do cliente]`
2. Rode `/conteudo-novo` com seu briefing:
   ```
   /conteudo-novo carrossel pro IG sobre os 5 erros mais comuns que clínicas cometem em campanhas de pré-verão
   ```
3. O diretor te perguntará detalhes que faltam, depois orquestra: estrategista → copywriter → editor → entrega.
4. Resultado em `output/[data]-[tema]/`.

### Fluxo 2 — Já sei o que quero, quero rápido

```
/conteudo-rapido post-linkedin polêmica sobre por que parar de oferecer "avaliação grátis" aumentou nosso ticket médio em 30%
```

Pula estratégia formal e revisão. Você assume risco de qualidade. Bom pra peça tática.

### Fluxo 3 — Plano da semana

```
/calendario-semanal próxima semana, foco em pré-Black Friday, IG (4 posts) + LinkedIn (3) + 1 blog
```

Diretor pergunta detalhes, estrategista monta plano coerente de 7 dias, mostra pra você aprovar, **só depois** produz tudo em paralelo.

### Fluxo 4 — Reaproveitar um conteúdo

```
/repurpose https://meublog.com/artigo-sobre-escalar-clinicas
```

Pega 1 fonte e gera 8 derivados (carrossel IG, post LinkedIn, Reel, Short, blog enxuto, email, ad em vídeo, carrossel LinkedIn).

---

## Como preencher `brand-context.md` pra um novo cliente

O arquivo padrão tem o exemplo da Rita Trindade Clínica. Pra adaptar:

1. **Substitua o nome e a descrição** (seção 1)
2. **Reescreva o público primário** com profundidade — não só demografia, **psicografia também** (seção 2). Sem isso, agentes entregam genérico.
3. **Escolha 1 arquétipo principal + 1 secundário** (seção 3). Se não souber, use a skill `brand-voice`.
4. **Liste 3-5 frases que a marca DIRIA literalmente + 3-5 que NUNCA diria** (seção 4). Esse é o teste mais valioso.
5. **Liste vocabulário SIM e NÃO** (seção 5). Específico — não "linguagem profissional".
6. **NÃO PULE a seção 6 (Restrições éticas/regulatórias)** — ela protege a marca de claim ilegal.
7. **Defina os pilares de conteúdo** (seção 8) — proporcionar produção balanceada.
8. **Deixe a seção 11 vazia** se não tem dado de performance ainda. Vai sendo preenchida com o tempo.

> Atalho: cole o brand-context.md do cliente anterior, abra com o Claude, peça `adapta esse brand-context pra [nova marca: descrição]`. Funciona bem como rascunho — depois revisa.

---

## Como criar um novo agente

Exemplo: você quer adicionar um `copywriter-whatsapp` (alinhado ao Pedro SDR do FalaMais.AI).

1. Crie `.claude/agents/copywriter-whatsapp.md`
2. Use o template:

```markdown
---
name: copywriter-whatsapp
description: [DESCRIÇÃO IMPORTA — Claude usa pra auto-roteamento. Diga claramente QUANDO usar, em que tipo de tarefa, com palavras-chave que o usuário escreveria.]
tools: Read, Write, Edit, Glob
model: sonnet
---

Você é **Copywriter de WhatsApp**...

## Antes de escrever
[...]

## Formatos que você produz
[...]

## Regras inquebráveis
[...]

## Anti-IA: cheque antes de entregar
[...]

## Entrega
[...]
```

3. Se precisa de skills auxiliares, crie em `.claude/skills/[nome-skill]/SKILL.md` no mesmo padrão.
4. Atualize o `diretor-conteudo.md` adicionando uma linha na tabela "Como você decide quem chamar".
5. Reinicie o Claude Code (ou rode `/agents` pra ver os agentes detectados).

---

## Como criar uma nova skill

Skills são padrões de conhecimento reutilizáveis (não tomam decisão, só ensinam).

1. Crie diretório `.claude/skills/[nome-da-skill]/`
2. Dentro, crie `SKILL.md` com frontmatter:

```markdown
---
name: nome-da-skill
description: [QUANDO usar — Claude auto-aciona com base nisso. Seja específico.]
---

# Conteúdo da skill

[Princípios, exemplos, padrões, scripts auxiliares]
```

3. Se a skill tem scripts (Python, shell, etc.), coloca no mesmo diretório (`.claude/skills/nome-da-skill/script.py`).
4. Os agentes auto-descobrem skills relevantes pelo `description`. Não precisa "import".

---

## Como criar um novo slash command

1. Crie `.claude/commands/[nome].md`
2. Frontmatter:

```markdown
---
description: [O que o comando faz, em 1 linha]
argument-hint: [como o usuário chama — ex: "[tema] [canal]"]
---

# /[nome]

[Instruções de execução, pipeline, princípios]
```

3. Use no Claude Code: `/[nome] [argumentos]`

---

## Boas práticas

- **Mantenha `brand-context.md` vivo.** Atualize sempre que aprender algo novo (especialmente via análise de performance).
- **Não crie 1 brand-context pra todos os clientes.** Cada cliente = 1 projeto = 1 brand-context.
- **Trate cada nicho com cuidado.** Saúde, jurídico, financeiro: cheque restrições da seção 6 do brand-context. Editor-revisor reprova claims regulados.
- **Pediu rápido com `/conteudo-rapido`? Você revisa.** Sem editor, qualidade é responsabilidade sua.
- **Editor-revisor tem voto final.** Se reprova, trate o feedback como ordem, não sugestão.

---

## Modelo de uso recomendado

Pra cliente recorrente (atende toda semana):

```bash
# Estrutura
seu-workspace/
├── cliente-rita-trindade/         ← clone fmai-marketing aqui
│   ├── .claude/
│   ├── brand-context.md            ← personalizado
│   └── output/                     ← histórico de entregas
├── cliente-manta-natacao/         ← outro clone, outro brand-context
│   ├── .claude/
│   ├── brand-context.md
│   └── output/
└── falamais-ai/                    ← seu produto próprio
    ├── .claude/
    ├── brand-context.md
    └── output/
```

Cada cliente tem o time inteiro disponível, com o cérebro de marca dele. As skills são genéricas (servem todos), mas o brand-context é específico.

---

## Manutenção e evolução

- **Skill desatualizada?** Edita `SKILL.md`. Próxima sessão pega.
- **Padrão novo descoberto?** Adiciona à skill correspondente.
- **Agente performando mal?** Edita o system prompt em `.claude/agents/[nome].md` — geralmente é falta de exemplo concreto ou falta de regra explícita.
- **Cliente novo?** Clone a pasta inteira. Mantém versionado em git por cliente.

---

## Suporte e contribuição

- Ajuste qualquer arquivo em `.claude/` — é seu, livre pra mexer.
- Se uma skill ou agente fica genérico, **abre exemplos concretos** dentro dele. É o que separa "OK" de "bom".
- Documente padrões que funcionam **na seção 11 do `brand-context.md`** — vira referência pros próximos.

---

## Licença / propriedade

Esse projeto é interno. Os agentes e skills foram desenhados por Sebastião Vieira. Use à vontade dentro da operação fmai/clientes.
