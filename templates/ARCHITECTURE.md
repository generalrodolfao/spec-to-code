# ARCHITECTURE — Decisões Técnicas

> Template. Copie para `specs/ARCHITECTURE.md` e preencha.

---

## ADR-0001: Stack Tecnológica

**Decisão:** *(ex: FastAPI + React + PostgreSQL)*

**Alternativas consideradas:**

| Opção | Prós | Contras | Decisão |
|---|---|---|---|
| *(stack A)* | | | ✅ |
| *(stack B)* | | | ❌ |

**Justificativa:** *(1 parágrafo)*

---

## ADR-0002: Estratégia de Dados

**Decisão:** *(ex: SQLite para dev, PostgreSQL para prod)*

**Justificativa:** *(1 parágrafo)*

---

## ADR-0003: Autenticação

**Decisão:** *(ex: JWT + OAuth2 via Google)*

**Justificativa:** *(1 parágrafo)*

---

## ADR-0004: Deploy

**Decisão:** *(ex: Docker + Fly.io / Vercel)*

**Justificativa:** *(1 parágrafo)*

---

## Diagrama de Arquitetura

```
┌──────────┐     ┌──────────┐     ┌──────────┐
│  Client  │────→│   API    │────→│    DB    │
│ (React)  │     │ (FastAPI)│     │(Postgres)│
└──────────┘     └──────────┘     └──────────┘
```

---

## Decisões Pendentes

- [ ] *(tópico ainda não decidido)*
