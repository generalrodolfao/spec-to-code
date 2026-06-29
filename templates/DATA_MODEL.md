# DATA MODEL — Modelo de Dados

> Template. Copie para `specs/DATA_MODEL.md` e preencha.

---

## Entidades

### User

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | UUID | ✅ | Chave primária |
| `email` | string | ✅ | Único |
| `name` | string | ✅ | |
| `created_at` | datetime | ✅ | |
| `updated_at` | datetime | ✅ | |

---

### *(entidade 2)*

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | UUID | ✅ | |
| *(campo)* | *(tipo)* | | |

---

## Relacionamentos

```
User 1──N Task
Task N──N Tag
Task 1──N Comment
```

---

## Índices

| Tabela | Índice | Tipo | Justificativa |
|---|---|---|---|
| `User` | `email` | UNIQUE | Login |
| *(tabela)* | *(coluna)* | | |

---

## Migrations

- Versionamento de schema com Alembic (SQLAlchemy) ou Prisma
- Rollback sempre documentado
