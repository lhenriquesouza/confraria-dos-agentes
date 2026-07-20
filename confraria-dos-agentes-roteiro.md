# Confraria dos Agentes — Roteiro do Workshop

> **Formato:** Presencial — grupo fechado.
> **Duração estimada:** ~7h10 de conteúdo / ~8h50 com intervalos — início às 9h, término previsto às 17h50 (ver Timeline Resumida)
> ⚠️ Sem intervalo entre os Módulos 1 e 5 da manhã — bloco contínuo de ~3h35 (09:25 às 13:00). Avaliar se cabe uma pausa curta informal durante o Módulo 5 (instalação tem esperas naturais).
> **Modelo base:** DeepSeek V4 Pro (OpenRouter)
> **Modelos de apoio:** GLM 5.2, Kimi K3
> **Interface principal:** OpenWebUI (nesquena/hermes-webui)
> **Pré-requisitos:** ver Módulo 0 — devem estar prontos ANTES do dia do workshop, não consomem tempo de sessão.

---

## 🗺️ Sumário — Agenda do Dia

> Início às 9h. Horários fechados considerando o almoço de 1h30 — se a sessão começar mais tarde, deslocar tudo proporcionalmente.

| Horário | Módulo | O que acontece |
|---|---|---|
| — | **Módulo 0** — Pré-requisitos | Feito antes do dia: contas, créditos, instalação prévia |
| 09:00 | **Módulo 1** — Aquecimento: Ferramentas Google | NotebookLM, Gemini Chat, Gemini Gems — os 3 conceitos-base (RAG, LLM puro, Skill) |
| 09:25 | **Módulo 2** — Modelos de Linguagem | Preço, contexto e reasoning — como escolher o modelo certo pra tarefa certa |
| 10:25 | **Módulo 3** — Harness | O que transforma um LLM em agente que age (ferramentas, memória, skills, autonomia) |
| 10:55 | **Módulo 4** — Coleta de Credenciais | OpenRouter, Telegram, Google Cloud — tudo levantado antes de instalar |
| 11:15 | **Módulo 5** — Setup + Cobrinha | Instala o Hermes (com mais tempo pra troubleshooting), conecta Telegram e Google Workspace, sobe o OpenWebUI, e mostra prompt vs. contexto com o jogo da cobrinha |
| 13:00 | *Almoço (1h30)* | |
| 14:30 | **Módulo 6** — Skills + `/goal` + `/delegate_task` | Instala Prisma e o pack do Matt Pocock; ensina delegação sequencial (`/goal`) e paralela (`/delegate_task`) — módulo estendido, com mais tempo prático |
| 16:30 | **Módulo 7** — MCP | Conecta o agente a serviços reais (OpenRouter, Gupy) |
| 16:55 | *Intervalo* | |
| 17:05 | **Módulo 8** — Autonomia: Cron | Agenda o monitoramento de preços construído no Módulo 6 pra rodar sozinho |
| 17:35 | **Fechamento** | Recap + agenda de próximos passos |
| ~17:50 | Fim | |

---

## 📦 Entregáveis do Dia

- [ ] Conta OpenRouter com créditos + API key
- [ ] Hermes Agent instalado e configurado
- [ ] OpenWebUI rodando como interface principal
- [ ] DeepSeek V4 Pro configurado como modelo padrão
- [ ] Skill Prisma instalada (relatórios executivos automatizados)
- [ ] Skill Pack Matt Pocock instalada
- [ ] MCP configurado (OpenRouter + Gupy)
- [ ] Monitoramento de preços agendado (cron job)
- [ ] Agente no Telegram
- [ ] Google Workspace integrado
- [ ] 🎁 Ollama + modelo local rodando

---

## ⏱️ Módulo 0 — Pré-requisitos (preparação prévia, antes do workshop)

> Não é tempo de sessão. Enviar esta lista para os participantes com antecedência — sem isso pronto, o Módulo 4/5 trava no meio da instalação.

- [ ] Notebook próprio com permissão de instalação (admin/sudo local) — sem isso, `curl | bash` do Hermes e o Ollama não instalam.
- [ ] Conta Google (pessoal, não corporativa gerenciada) para criar projeto no Google Cloud Console e habilitar OAuth — contas de workspace corporativo gerenciado costumam bloquear a criação de OAuth client "Desktop app".
- [ ] Cartão de crédito ou Pix disponível para colocar crédito na OpenRouter (R$ 30-50).
- [ ] Telegram instalado no celular, com acesso ao @BotFather.
- [ ] Git, Node.js/npm e Python 3 já instalados no notebook (pré-requisito do Hermes, da OpenWebUI e do skill pack via `npx`).
- [ ] Conta gratuita no Apify criada com antecedência (usada no MCP da Gupy, Módulo 7.3).
- [ ] ~5 GB livres em disco (modelos locais do Ollama + clones de repositório).

---

## ⏱️ Módulo 1 — Aquecimento: Ferramentas Google (25 min)

> Warmup prático. Cada ferramenta serve de gancho conceitual para o que vem depois. Tende a andar rápido com esse grupo — se sobrar tempo, usar de folga para o Módulo 5 (setup costuma ser o gargalo real do dia).

### 1.1 NotebookLM — O Bibliotecário (8 min)

**URL:** `https://notebooklm.google.com`

**Atividade prática:**
- Criar um notebook novo
- Adicionar 2-3 fontes: PDF / URL / texto colado
- Explorar o que sai: resumo executivo, FAQ, timeline
- 🎧 Gerar o podcast de áudio

**Conceito:** Isso é **RAG** (Retrieval-Augmented Generation). O modelo busca nas fontes que você deu, não no treino dele. É o mesmo mecanismo que o Hermes usa quando acessa arquivos locais antes de responder.

---

### 1.2 Gemini Chat — O LLM por Trás (5 min)

**URL:** `https://gemini.google.com`

**Atividade prática:**
- Perguntas diretas
- Colar contexto grande (arquivo, URL)

**Conceito:** Isso é um **LLM + Interface**. O modelo (Gemini) processa texto. A interface (site) é só a casca. O LLM sozinho é um cérebro sem corpo — não acessa arquivos, não executa comandos, não lembra de você.

---

### 1.3 Gemini Gems — O Especialista Sob Medida (8 min)

**URL:** `https://gemini.google.com` → Gems (menu lateral)

**Atividade prática:**
- Criar um Gem com instruções sobre o contexto de cada pessoa
- Nome, objetivo, instruções de tom e formato
- Testar o Gem vs Gemini genérico

**Conceito:** Isso é uma **Skill**. Instruções que você ensina uma vez, nomeia, e chama quando precisa. Mesmo conceito das skills do Hermes — mas lá as skills podem acessar ferramentas (web, arquivos, terminal).

---

### 1.4 Fechamento do Módulo (4 min)

| Ferramenta | Conceito | No Hermes é... |
|---|---|---|
| NotebookLM | RAG | Contexto + arquivos locais |
| Gemini Chat | LLM + Interface | OpenWebUI + modelos |
| Gemini Gems | Instruções persistentes | Skills |

---

## ⏱️ Módulo 2 — O Cérebro: Modelos de Linguagem (1h)

> O que está por baixo do capô. Toda escolha de ferramenta começa aqui.

### 2.1 O Ecossistema de Modelos (20 min)

**Preço por milhão de tokens (OpenRouter)**

| Modelo | Origem | Input $/M | Output $/M | Contexto |
|---|---|---|---|---|
| Claude Fable 5 | 🇺🇸 | $10,00 | $50,00 | 1M |
| Claude Opus 4.8 | 🇺🇸 | $5,00 | $25,00 | 1M |
| Claude Sonnet 4.6 | 🇺🇸 | $3,00 | $15,00 | 1M |
| **DeepSeek V4 Pro** ⭐ | 🇨🇳 | **$0,435** | **$0,87** | 1M |
| GLM 5.2 | 🇨🇳 | $0,91 | $2,86 | 1M |
| Kimi K3 | 🇨🇳 | — | — | 1M |

**A pergunta não é "qual é melhor". É: qual é o melhor para a tarefa certa?**

**Por que NÃO usar Fable/Opus para tudo:**
- Custo 10-100× maior para ganho marginal em tarefas rotineiras
- DeepSeek V4 Pro entrega qualidade equivalente em 90% dos casos
- Modelos caros reservados para: código crítico, tarefas que justificam o custo

**Capacidades por tarefa:**

| Tarefa | Modelo | Motivo |
|---|---|---|
| Chat rápido, dúvidas, texto | DeepSeek V4 Pro | $0,87/M output, excelente |
| Pesquisa profunda, relatórios | DeepSeek V4 Pro ou GLM 5.2 | Contexto 1M |
| Codificação complexa | Claude Opus 4.8 / Fable 5 | 88-95% SWE-bench |
| Tarefas agentic (terminal) | GLM 5.2 | 81% Terminal-Bench |
| Agente do dia a dia (Hermes) | DeepSeek V4 Pro | 14× mais barato que Claude |

---

### 2.2 Contexto — Por Que o Tamanho Importa (10 min)

**Janela de contexto = memória de trabalho do modelo.**

- Contexto pequeno (8K-32K): modelo "esquece" o que foi dito no começo
- Contexto grande (128K-1M): processa documentos inteiros, código longo, conversas extensas
- **Na prática:** 1M de tokens = vários livros, um projeto inteiro, ou horas de reunião

| Modelo | Contexto | Equivalente |
|---|---|---|
| DeepSeek V4 Pro | 1M | O Código Limpo inteiro (~460 pág) |
| Claude Sonnet 4.6 | 200K | Um projeto médio |
| GPT-4o | 128K | Um documento grande |

**Por que isso importa no dia a dia:**
- Colocar o contexto certo = o modelo entende o que você precisa
- Economiza tokens (dinheiro) porque você não precisa reexplicar
- Habilidade crucial: **saber o que colocar no contexto e o que deixar de fora**

---

### 2.3 Reasoning — Low, Medium, High, XHigh (10 min)

- **O que é:** controle sobre quanto o modelo "pensa" antes de responder
- **Low/Medium:** resposta rápida, tasks simples
- **High/XHigh:** resposta mais lenta, tasks complexas
- **Trade-off:** mais reasoning = mais tokens = mais caro e mais lento

**Regra prática:**

| Tarefa | Reasoning | Modelo |
|---|---|---|
| "Resuma este email" | Low | DeepSeek |
| "Crie o esqueleto de uma API" | Medium | DeepSeek |
| "Debug este bug intermitente" | High | DeepSeek ou Opus |
| "Projete a arquitetura" | XHigh | Opus / Fable |

---

### 2.4 Mão na Massa: Modelo Local com Ollama (15 min)

> Um modelo útil roda no próprio laptop — sem internet, sem custo.

```bash
# Instalar Ollama
curl -fsSL https://ollama.com/install.sh | sh

# Rodar modelo pequeno
ollama run qwen2.5:1.5b
```

**O que demonstrar:**
- Funciona offline
- Responde em português
- É pior que DeepSeek/Claude, mas é **grátis e seu**
- Cenário de uso: dados sensíveis, prototipação, estudos

**Conceito:** Modelo local existe, funciona. Mas um modelo sozinho é só um chat no terminal.

---

## ⏱️ Módulo 3 — O Corpo: Harness (30 min)

> Modelo de IA gera texto. Harness faz ele AGIR.

### 3.1 O que um Harness Adiciona (15 min)

| LLM sozinho | Com Harness |
|---|---|
| Gera texto | Executa comandos no terminal |
| Responde perguntas | Cria, lê e edita arquivos |
| Segue prompts | Pesquisa na web, extrai dados |
| Não lembra de nada | Memória permanente entre sessões |
| Só conversa | Age em background, Telegram, cron |

**Analogia:** LLM é o motor. Harness é o carro inteiro — volante, rodas, painel.

**Capacidades principais que um harness implementa:**
1. **Ferramentas (tools):** terminal, arquivos, web, APIs
2. **Memória:** contexto permanente entre sessões
3. **Skills:** instruções empacotadas reutilizáveis
4. **Autonomia:** cron jobs, background tasks
5. **Múltiplos canais:** CLI, API, Telegram, WhatsApp, etc.
6. **Provedores:** conectar a qualquer LLM — sem ficar preso a fornecedor

---

### 3.2 Ecossistema de Harnesses (10 min)

| Harness | Foco | Modelos | Interface | Licença |
|---|---|---|---|---|
| **Hermes Agent** ⭐ | Assistente pessoal | 200+ (OpenRouter) | CLI, Telegram, WebUI | Open source |
| **Cursor** | IDE + Agente | Anthropic, OpenAI | Editor | Proprietária |
| **Claude Code** | Terminal + Código | Só Anthropic | Terminal (TUI) | Proprietária |
| **Cline** | VS Code + Agente | Provider-agnóstico | VS Code ext. | Open source |
| **Pi** | Terminal + Código | 30+ provedores | Terminal (TUI) | Open source |

**Por que Hermes para este workshop:**
- Provider-agnóstico (OpenRouter → qualquer modelo)
- Multi-canal (terminal + Telegram + web)
- Skills e cron jobs nativos
- Open source — sem amarras
- MCP nativo

---

## ⏱️ Módulo 4 — Pré-Setup: Coleta de Credenciais (20 min)

> Antes de instalar o Hermes, vamos coletar TUDO que precisamos.
> Assim a instalação e configuração são contínuas, sem interrupção.

### 4.1 OpenRouter — Conta + API Key (5 min)

**URL:** `https://openrouter.ai`

1. Sign In com Google
2. Credits → Adicionar R$ 30-50 (PIX ou cartão)
3. Settings → Keys → Create Key
4. **Copiar chave** (`sk-or-v1-...`) e salvar no bloco de notas
5. **Anotar email e senha** usados

**O que é uma API Key:** A senha que permite seu computador falar com os modelos. Trate como senha de banco — não compartilhe, não suba para o GitHub.

---

### 4.2 Telegram — Criar Bot no @BotFather (5 min)

1. Telegram → @BotFather
2. `/newbot`
3. Nome: `Confraria [Seu Nome]`
4. Username: `[seunome]_confraria_bot`
5. **Copiar o token** (formato `123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11`) e salvar

---

### 4.3 Google Workspace — Projeto no Google Cloud (10 min)

> Setup antecipado do OAuth. Mais burocrático, faremos agora para não travar depois.

| Etapa | URL / Instrução |
|---|---|
| Criar/selecionar projeto | https://console.cloud.google.com/projectselector2/home/dashboard |
| Habilitar APIs necessárias | Gmail API, Google Calendar API, Google Drive API, Google Sheets API, Google Docs API, People API |
| Criar OAuth client | https://console.cloud.google.com/apis/credentials → Criar Credenciais → OAuth 2.0 Client ID → "Desktop app" → Criar |
| Adicionar email como test user | https://console.cloud.google.com/auth/audience → Test users → Adicionar usuários → colocar o email |
| Baixar JSON | Botão de download no client criado → **salvar o arquivo** |

**Checklist do Módulo 4:**
- [ ] OpenRouter API key (`sk-or-v1-...`)
- [ ] Telegram bot token (`123456:ABC-DEF...`)
- [ ] Google Cloud OAuth JSON (arquivo `client_secret_....json`)

---

## ⏱️ Módulo 5 — Setup: Hermes + Integrações + OpenWebUI + Cobrinha (1h45)

> Agora que temos todas as credenciais, a instalação flui sem parar.

### 5.1 Instalação do Hermes Agent (30 min)

> Tempo alongado de propósito — é aqui que aparecem os problemas reais (permissão, PATH, versão de dependência). Reservar folga pra troubleshooting individual em vez de travar o grupo todo esperando uma pessoa.

```bash
# Instalar
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash

# Fechar e reabrir o terminal

# Setup guiado
hermes setup
# → Provider: OpenRouter
# → Colar API key (que salvamos no Módulo 4)
```

**Verificação:**
```bash
hermes doctor
```

---

### 5.2 Configurar Modelo Padrão + Telegram + Google Workspace (20 min)

**Modelo padrão — DeepSeek V4 Pro:**
```bash
hermes model
# → OpenRouter → deepseek/deepseek-chat
```

**Telegram — Conectar o bot:**
```bash
hermes gateway setup
# → Telegram → colar o token do @BotFather (Módulo 4)
hermes gateway install
hermes gateway start
```

**Google Workspace — Setup OAuth:**
```bash
export GSETUP="python3 $HOME/.hermes/skills/productivity/google-workspace/scripts/setup.py"

# Verificar se já configurado
$GSETUP --check

# Passar o arquivo JSON baixado no Módulo 4
$GSETUP --client-secret /caminho/do/client_secret_....json

# Gerar URL de autorização
$GSETUP --auth-url --services email,calendar --format json

# Colar a URL de retorno após autorizar no navegador
$GSETUP --auth-code "URL_OU_CODIGO_RETORNADO"

# Verificar
$GSETUP --check
# → AUTHENTICATED
```

**Testar Google Workspace:**
```bash
export GAPI="python3 $HOME/.hermes/skills/productivity/google-workspace/scripts/google_api.py"

$GAPI gmail search "is:unread" --max 5
$GAPI calendar list
```

> Neste ponto o Hermes já está no terminal, no Telegram e integrado ao Google.

---

### 5.3 ⭐ O Choque: 3 Prompts, 1 Tarefa — Jogo da Cobrinha (30 min)

> Logo após a instalação, vamos mostrar o poder na prática. Ainda no terminal.

**Rodada 1 — O Amador (5 min)**

```bash
hermes chat -q "Crie um jogo da cobrinha em HTML."
```

Resultado: funciona. Feio. Genérico.

---

**Rodada 2 — O Detalhista (7 min)**

```bash
hermes chat -q "Crie um jogo da cobrinha em HTML com: tema escuro, grid no fundo, efeito ao comer fruta, placar, game over, setas + touch."
```

Resultado: melhor. Mais bonito. Mais completo.

---

**Rodada 3 — O Profissional (10 min)**

Criar arquivo `especificacao.md`:

```markdown
# Especificação: Jogo da Cobrinha

## Visual
- Tema neon sobre fundo preto (#0a0a0a)
- Cobra: gradiente verde (#00ff88 → #00cc66)
- Fruta: 🍎 🍇 🍊 🫐 (rotativa)
- Partículas ao comer fruta
- Grid toggle (tecla G)

## Mecânicas
- Velocidade progressiva (+5% a cada 5 frutas)
- Fruta bônus dourada a cada 20pts (5×, 5s)
- Som com Web Audio API
- Pausa: Espaço

## UX
- Tela inicial com JOGAR
- Placar + high score (localStorage)
- Game over + JOGAR NOVAMENTE
- Touch buttons para mobile

## Código
- HTML/CSS/JS puro, arquivo único
- Comentários em português
- Sem dependências externas
```

```bash
hermes chat -q "Leia o arquivo especificacao.md e crie o jogo exatamente como especificado."
```

**Lição (3 min):**

> A diferença NÃO foi o modelo. Foi o **CONTEXTO**.
>
> Editar o contexto é o movimento profissional. Reescrever prompt é o movimento amador.
>
> A especificação é uma skill descartável — você escreve uma vez, o agente executa.

---

### 5.4 OpenWebUI — A Interface Principal (20 min)

> Agora que o Hermes está instalado e configurado, vamos instalar a interface web.

**Prompt para o Hermes instalar (no terminal):**

```bash
hermes -q "Clone o repositório https://github.com/nesquena/hermes-webui.git, execute o bootstrap.py e inicie o servidor web. Depois me diga em qual URL está rodando."
```

**Alternativa manual (se o prompt acima falhar):**

```bash
git clone https://github.com/nesquena/hermes-webui.git hermes-webui
cd hermes-webui
python3 bootstrap.py
```

**Servidor:** `http://localhost:8787`

### 5.5 Tour pelo OpenWebUI (10 min)

Recursos principais para conhecer:

- **Layout três painéis:** sidebar (sessões) | centro (chat) | direita (workspace)
- **Composer footer:** campo de mensagem + seletor de modelo + indicador de contexto (anel circular)
- **Seletor de modelos:** trocar entre DeepSeek, GLM, Claude na hora
- **Hermes Control Center:** configurações, profiles, MCP, cron jobs
- **Tool call cards:** cada chamada de ferramenta mostrada inline com args e resultado
- **Subagent cards:** atividade de agentes filhos com indentação visual
- **Mermaid diagrams:** renderizam direto no chat
- **Reasoning blocks:** collapsible para extended thinking (low/medium/high/xhigh)
- **Workspace file browser:** navegar arquivos do projeto sem sair do browser
- **Aprovação de comandos:** allow once / session / always / deny

> ⚠️ **Isso não é só uma configuração — é uma decisão de risco.** `always` = o agente roda comandos sem perguntar de novo, inclusive os que apagam ou sobrescrevem arquivo, ou enviam mensagem/email. Combinado com cron (Módulo 8) e Google Workspace (Gmail/Calendar), um `always` mal calibrado pode ter efeito real e irreversível sem revisão humana no meio. Regra prática: `always` só para leitura/pesquisa; comandos que escrevem, enviam ou apagam ficam em `session` ou `once`.

**Testar:** uma conversa no OpenWebUI. "Quem é você e o que pode fazer?"

> ⚠️ **A partir daqui, tudo roda pelo OpenWebUI.** As instruções de terminal abaixo são referência, mas o grupo opera pela interface web.

---

## ⏱️ Módulo 6 — Skills + /goal + /delegate_task (2h)

> Você ensina UMA vez. O agente carrega pra sempre. E com as skills certas, você delegar trabalho complexo.

### 6.1 Skill Prisma — Relatórios Executivos Automatizados (15 min)

> Skill pronta, já preparada para o workshop (arquivo `prisma_skill.zip` na pasta do treinamento). Ela lê dados de Databricks, de uma query, ou de um arquivo (PDF/Excel/DOCX/CSV) e entrega um relatório HTML interativo, pronto pra apresentar — dashboard, relatório narrativo, explorador de dados ou slideshow, dependendo do pedido.

**Instalar:**
```bash
unzip prisma_skill.zip -d ~/.hermes/skills/
mv ~/.hermes/skills/prisma_export ~/.hermes/skills/prisma
```

**Testar:**
```
Use a skill prisma: crie um dashboard a partir do arquivo vendas.csv
```

> **Conceito:** essa é a mesma lógica do Gemini Gem do Módulo 1.3 e da especificação da cobrinha do Módulo 5.3 — só que empacotada, versionada e reutilizável por qualquer pessoa do time. Uma skill boa elimina a necessidade de reexplicar o "como" toda vez; só o "o quê" muda a cada uso.

---

### 6.2 Skill Pack do Matt Pocock (15 min)

> Skills do Matt Pocock — 177k ⭐ no GitHub, usadas por milhares de engenheiros.
> São skills prontas para engenharia de software real: especificação, planejamento, code review, TDD.

**Instalação (30 segundos):**

```bash
npx skills@latest add mattpocock/skills
```

> Selecionar as skills desejadas. **Importante:** marcar `/setup-matt-pocock-skills`.

**Setup no projeto:**
```
/setup-matt-pocock-skills
```

---

### 6.3 Visão Geral do Pacote (5 min)

| Skill | Pra quê |
|---|---|
| **`/grill-me`** ⭐ | Entrevista relentlessly sobre um plano ou design |
| **`/grill-with-docs`** ⭐ | Grill-me + constrói glossário e ADRs do projeto |
| **`/to-spec`** | Transforma conversa em especificação publicável |
| **`/to-tickets`** | Quebra spec em tickets com dependências |
| **`/implement`** | Implementa spec com TDD e code review |
| **`/code-review`** | Revisão em dois eixos: padrões + fidelidade à spec |
| **`/tdd`** | Red-green-refactor |
| **`/diagnosing-bugs`** | Loop disciplinado para bugs complexos |
| **`/improve-codebase-architecture`** | Escaneia e sugere melhorias de design |
| **`/research`** | Investigação contra fontes primárias, em background |
| **`/handoff`** | Compacta conversa para outro agente continuar |
| **`/ask-matt`** | Roteador — pergunta qual skill usar pra cada situação |

---

### 6.4 ⭐ /goal — Tarefa Complexa (35 min)

> `/goal` delega uma tarefa para **1 agente**. O agente trabalha do começo ao fim.
> Use quando a tarefa é linear, com múltiplos passos em sequência.

**Exercício:** Pesquisa completa sobre um tema + relatório executivo + HTML de apresentação.

No OpenWebUI (ou terminal), cada um dispara:

```
/goal "Faça uma pesquisa completa sobre o mercado de agentes de IA no Brasil em 2026. 
1. Pesquise as principais ferramentas, players, tendências e preços
2. Crie um relatório executivo em markdown com: resumo, análise de mercado, concorrentes, recomendações
3. Converta o relatório para um HTML estilizado (tema escuro, design profissional) pronto para apresentar
4. Salve o HTML como relatorio-mercado-agentes.html"
```

> O agente executa os 4 passos EM SEQUÊNCIA, usando as ferramentas que precisar (web search, file write, etc.).

**Resultado esperado:**
- Pesquisa web em múltiplas rodadas
- Relatório markdown com seções e fontes
- HTML estilizado salvo localmente
- Tudo isso em um único comando

**Conceito:** `/goal` é para tarefas **sequenciais** com múltiplos passos. O agente gerencia a ordem sozinho.

> **Ponte com o Módulo 6.1:** o que acabamos de fazer na mão — pesquisar, estruturar e gerar HTML — é exatamente o que a skill Prisma empacota para dados (Databricks, CSV, planilha). `/goal` é o motor genérico; uma skill como a Prisma é esse motor já especificado e pronto para reuso.

---

### 6.5 ⭐ /delegate_task — Implementação Paralela (40 min)

> `/delegate_task` dispara **N agentes independentes em paralelo**.
> Use quando as tarefas são independentes entre si.

**Fluxo do exercício:**

**Passo 1 — Criar a spec com grill-me**
```
/grill-me
# Tema: "Quero criar um sistema de monitoramento de preços de concorrentes que:
#  - Coleta preços de 3 concorrentes automaticamente
#  - Gera alertas quando o preço muda
#  - Mostra num dashboard simples HTML
#  - Envia resumo semanal por email"
```
> O grill-me entrevista até o escopo estar claro e documentado.

**Passo 2 — Quebrar em tickets com /to-tickets**
```
/to-tickets
```
> Gera tickets independentes com dependências mapeadas.

**Passo 3 — Implementar com /delegate_task**
```
/delegate_task
  1. "Ticket 1: Coletor de preços — script em Python que acessa a API dos 3 concorrentes e salva em JSON"
  2. "Ticket 2: Dashboard HTML — página que carrega o JSON e mostra gráficos dos preços ao longo do tempo"
  3. "Ticket 3: Sistema de alertas — compara preços e envia notificação no Telegram quando detecta mudança"
```
> Cada ticket vira um agente isolado. Todos rodam AO MESMO TEMPO.

**Resultado esperado:**
- 3 agentes trabalhando em paralelo
- Cada um com seu próprio contexto e arquivos
- Resultados independentes que compõem o sistema completo

---

### 6.6 /goal vs /delegate_task — Tabela Comparativa (10 min)

| | `/goal` | `/delegate_task` |
|---|---|---|
| **Agentes** | 1 | Até 3 |
| **Paralelismo** | Não (sequencial) | Sim (cada um em isolamento) |
| **Quando usar** | Tarefa única com múltiplos passos | Várias tarefas independentes |
| **Exemplo** | "Pesquise, analise e gere relatório" | "Pesquise 3 concorrentes ao mesmo tempo" |
| **Custo** | 1 agente filho | N agentes simultâneos |

**Regra prática:**
> Se os passos **dependem** um do outro (B precisa do resultado de A) → `/goal`.
> Se as tarefas são **independentes** (A, B e C não se cruzam) → `/delegate_task`.

**Pipeline completo de engenharia:**

```
Ideia → /grill-with-docs (alinhar) → /to-spec (especificar)
     → /to-tickets (quebrar) → /goal ou /delegate_task (executar)
```

---

## ⏱️ Módulo 7 — MCP: Agentes Conectados ao Mundo (25 min)

> Até agora o Hermes acessa web e arquivos. MCP conecta a serviços reais.

### 7.1 O que é MCP (5 min)

Model Context Protocol = padrão universal para agente conversar com serviço externo.

```
Agente ←──MCP──→ API / Banco / Plataforma
```

---

### 7.2 OpenRouter MCP (7 min)

```bash
hermes mcp add openrouter https://mcp.openrouter.ai/mcp
hermes mcp login openrouter
```

**O que o agente passa a fazer:**
- Consultar modelos e preços em tempo real
- Verificar saldo de créditos
- Testar mensagens em diferentes modelos
- Escolher modelo ideal para cada tarefa

**Testar (no OpenWebUI):**
```
"Quanto de crédito tenho na OpenRouter? Quais modelos estão disponíveis?"
```

---

### 7.3 Gupy MCP (via Apify) (8 min)

```json
{
  "mcpServers": {
    "apify": {
      "command": "npx",
      "args": ["mcp-remote",
        "https://mcp.apify.com/?tools=pmodinger/gupy-vagas-brasil",
        "--header",
        "Authorization: Bearer SEU_TOKEN"
      ]
    }
  }
}
```

Precisa de conta gratuita no Apify + token de API.

**Testar:**
```
"Busque vagas de engenharia de software em São Paulo no Gupy."
```

---

### 7.4 Ecossistema MCP (5 min)

MCP é um padrão em crescimento:
- **Oficiais:** GitHub, Slack, Notion, Figma, Google Drive
- **Comunidade:** dezenas de servidores open source
- **Crie o seu:** qualquer API REST vira MCP em minutos

---

## ⏱️ Módulo 8 — Autonomia: Cron (30 min)

> O agente trabalha sozinho. Você só recebe o resultado.

### 8.1 Agendando o Monitoramento de Preços do Módulo 6.5 (15 min)

> Em vez de um exemplo solto, agenda o próprio sistema que o grupo construiu no `/delegate_task` (coletor + comparação + alerta no Telegram) pra rodar sozinho todo dia.

```bash
hermes cron create "0 9 * * *" \
  -s monitor-precos \
  -q "Rode o coletor de preços dos 3 concorrentes, compare com o histórico salvo e envie alerta no Telegram se houver mudança."
```

**Anotar o JOB ID.**

**Disparo coletivo — todos ao mesmo tempo:**
```bash
hermes cron run [JOB_ID]
```

> Neste momento, N agentes estão monitorando preços sozinhos. Ninguém fez prompt. Ninguém está revisando. É o que roda todo dia às 9h sem ninguém olhar.

### 8.2 Telegram — Testar o Bot ao Vivo (10 min)

Voltar ao Telegram e testar comando real com o bot já configurado:

```
Use a skill prisma: crie um dashboard rápido com os dados de preço coletados
```

### 8.3 Dicas de Autonomia no Dia a Dia (5 min)

- **Cron + Telegram:** alerta de mudança de preço chega no celular sem ninguém revisar
- **Cron + Google Workspace:** agente arquiva emails, cria eventos na agenda
- **Múltiplos crons:** monitoramento de concorrentes + outros processos recorrentes que valem a pena rodar sozinhos
- **`hermes cron list`** para ver todos os agendamentos ativos

---

## ⏱️ Fechamento (15 min)

### Recap dos Entregáveis

- [ ] Conta OpenRouter com créditos + API key
- [ ] Hermes Agent instalado e configurado
- [ ] DeepSeek V4 Pro como modelo padrão
- [ ] Telegram bot conectado e funcionando
- [ ] Google Workspace integrado (Gmail + Calendar)
- [ ] OpenWebUI rodando em http://localhost:8787
- [ ] Skill Prisma + Skill Pack Matt Pocock instaladas
- [ ] MCP (OpenRouter + Gupy)
- [ ] Monitoramento de preços agendado (cron job)
- [ ] 🎁 Ollama + modelo local (qwen2.5:1.5b)

### Agenda para os Próximos Dias

Cada um define o que vai delegar para o agente:
- ________________________________
- ________________________________
- ________________________________

---

## ⏱️ Timeline Resumida

| Módulo | Tema | Duração |
|---|---|---|
| 0 | **Pré-requisitos** (antes do dia, não conta no tempo de sessão) | — |
| 1 | Aquecimento: Google Tools | 25 min |
| 2 | Modelos de Linguagem (LLMs) | 1h |
| 3 | Harness: o corpo do agente | 30 min |
| 4 | **Pré-Setup: Coleta de Credenciais** | **20 min** |
| 5 | Setup: Hermes + Integrações + OpenWebUI + Cobrinha | 1h45 |
| — | Almoço | 1h30 |
| 6 | Skills (Prisma + Matt Pocock) + /goal + /delegate_task | 2h |
| 7 | MCP | 25 min |
| — | Intervalo | 10 min |
| 8 | Autonomia: Cron | 30 min |
| | Fechamento | 15 min |
| **Total conteúdo** | | **~7h10** |
| **Total com intervalos** | | **~8h50 (9h às 17h50)** |

> Sem intervalo entre Módulos 1 e 5 (manhã inteira corrida, ~3h35 sem pausa formal). O único intervalo do dia agora é à tarde, entre os Módulos 7 e 8. Módulo 5 ganhou +15 min pra dar folga real na instalação do Hermes; Módulo 6 dobrou de tamanho (1h15 → 2h) com mais tempo prático em `/goal` e `/delegate_task`.

---

## Apêndice — Comandos Rápidos

```bash
# Terminal (caso precise)
hermes                             # chat interativo
hermes model                       # trocar modelo
hermes skills list                 # listar skills
hermes cron list                   # listar cron jobs
hermes cron run ID                 # executar cron manual
hermes gateway setup               # configurar Telegram
hermes gateway start               # iniciar gateway
hermes mcp add NOME URL            # adicionar MCP
hermes mcp login NOME              # autenticar MCP
hermes doctor                      # diagnóstico
ollama run qwen2.5:1.5b            # modelo local

# Google Workspace
GSETUP="python3 $HOME/.hermes/skills/productivity/google-workspace/scripts/setup.py"
GAPI="python3 $HOME/.hermes/skills/productivity/google-workspace/scripts/google_api.py"
```

**No OpenWebUI:** tudo disponível pela interface — chat, skills, cron, MCP, troca de modelos.

---

## Apêndice — Modelos no OpenRouter

```bash
deepseek/deepseek-chat             # DeepSeek V4 Pro — padrão do workshop
google/gemini-2.5-flash            # Alternativa gratuita
anthropic/claude-sonnet-4.6        # Qualidade superior
z-ai/glm-5.2                       # Especialista agentic
```
