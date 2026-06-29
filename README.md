<h1 align="center">Spec-to-Code</h1>
<p align="center">
  <em>Template de desenvolvimento spec-driven com AI agents — do PRD ao código em minutos</em>
  <br/>
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/license-MIT-00154E?style=flat-square" /></a>
  <a href="https://www.python.org"><img src="https://img.shields.io/badge/python-3.11%2B-00154E?style=flat-square&logo=python&logoColor=F17405" /></a>
</p>

---

## O que é Spec-Driven Development?

Especificação antes do código. Você escreve o **PRD** (product requirements doc) e specs técnicas, e um AI agent gera todo o código — frontend, backend, testes, docs e CI — a partir delas.

Diferente de "prompt engineering", spec-driven é **determinístico**: mesma spec = mesma saída. Rastreável. Auditável. Versionável.

---

## Fluxo

```
PRD.md ──→ Specs Técnicas ──→ AI Agent ──→ Código
   │              │                │
   ▼              ▼                ▼
O que            Como            Implementação
(resumo 1p)    (detalhado)    (front + back + tests + CI)
```

1. **Escreva o PRD** — 1 página descrevendo o problema, usuário, features e critérios de aceite
2. **Gere as specs** — arquitetura, modelo de dados, API contract, componentes (templates prontos)
3. **Rode o agent** — Claude Code / OpenCode gera o código a partir das specs
4. **Valide** — testes rodam automaticamente, CI/CD verifica qualidade

---

## Templates incluídos

| Template | Descrição |
|---|---|
| `templates/PRD.md` | Product Requirements Document — 1 página, foco no problema |
| `templates/ARCHITECTURE.md` | Decisões de arquitetura (ADR-style), stack, diagramas |
| `templates/DATA_MODEL.md` | Entidades, relacionamentos, schema |
| `templates/API_CONTRACT.md` | Endpoints REST/GraphQL, request/response, erros |
| `templates/COMPONENTS.md` | Árvore de componentes (React/Vue), props, estados |
| `templates/ROADMAP.md` | Milestones, fases, prioridades |
| `templates/CLAUDE.md` | Instruções para o agente — padrões, convenções, restrições |

---

## Quickstart

```bash
# 1. Clone este repo como template
git clone https://github.com/generalrodolfao/spec-to-code.git meu-projeto
cd meu-projeto

# 2. Escreva seu PRD
cp templates/PRD.md specs/PRD.md
# Edite specs/PRD.md com seu produto

# 3. Gere specs a partir do PRD (com AI)
# Exemplo: "Leia specs/PRD.md e preencha os templates em specs/ baseado nele"

# 4. Gere o código
# Exemplo com Claude Code:
# "Leia todos os specs em specs/ e implemente o código completo em src/"
```

---

## Exemplo Real

Veja [`examples/task-app/`](examples/task-app/) — um app de tarefas completo gerado a partir das specs:

| Arquivo | Conteúdo |
|---|---|
| `specs/PRD.md` | App de tarefas estilo Todoist — features e critérios |
| `specs/ARCHITECTURE.md` | FastAPI + SQLite + React, decisões de design |
| `specs/DATA_MODEL.md` | Usuários, tasks, projetos, tags |
| `specs/API_CONTRACT.md` | 12 endpoints REST |
| `src/backend/` | FastAPI completo com autenticação, CRUD, testes (pytest) |
| `src/frontend/` | React + Tailwind, componentes, hooks |

---

## Por que Spec-Driven?

| Abordagem | Prompt Engineering | Spec-Driven |
|---|---|---|
| Determinismo | Baixo (mesmo prompt, resultados diferentes) | Alto (mesma spec = mesma saída) |
| Rastreabilidade | Difícil (o que mudou entre versões?) | Fácil (git diff na spec) |
| Colaboração | Uma pessoa escreve prompts | Time escreve specs, AI implementa |
| Qualidade | Varia muito | Consistente (templates padronizados) |
| Documentação | Precisa escrever depois | Já existe (a spec é a doc) |

---

## Estrutura do Projeto

```
meu-projeto/
├── specs/
│   ├── PRD.md
│   ├── ARCHITECTURE.md
│   ├── DATA_MODEL.md
│   ├── API_CONTRACT.md
│   └── COMPONENTS.md
├── templates/         # Templates reutilizáveis (não editar)
├── src/
│   ├── backend/
│   └── frontend/
├── tests/
├── CLAUDE.md          # Instruções para o agente
└── README.md
```

---

## Convenções

- **Specs em português** (PT-BR) — o time entende, o agente entende
- **Código em inglês** — variáveis, funções, comentários
- **Conventional Commits** — `feat:`, `fix:`, `docs:`, `chore:`
- **1 spec = 1 arquivo** — nunca juntar PRD com arquitetura no mesmo markdown

---

<p align="center">
  <a href="https://github.com/generalrodolfao"><img src="https://img.shields.io/badge/github-generalrodolfao-00154E?style=flat-square&logo=github&logoColor=F17405" /></a>
  <a href="https://linkedin.com/in/generalrodolfao"><img src="https://img.shields.io/badge/LinkedIn-generalrodolfao-00154E?style=flat-square&logo=linkedin&logoColor=F17405" /></a>
</p>
