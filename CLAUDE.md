# CLAUDE.md — Instruções para Agentes

> **Quem lê:** Claude Code, OpenCode, ou qualquer AI agent spec-driven.
> **Objetivo:** Definir padrões, convenções e restrições para geração de código consistente.

---

## Regras Gerais

1. **Leia as specs antes de codar.** Comece por `specs/PRD.md`, depois `ARCHITECTURE.md`, `DATA_MODEL.md`, `API_CONTRACT.md`, `COMPONENTS.md`.
2. **Nunca gere código sem spec.** Se uma decisão não está documentada, pergunte antes de implementar.
3. **Spec é a fonte da verdade.** Se o código desvia da spec, corrija o código — não a spec.
4. **Código em inglês, specs em português.**
5. **Conventional Commits** — `feat:`, `fix:`, `docs:`, `test:`, `chore:`, `refactor:`.
6. **Nenhum segredo no código.** Use variáveis de ambiente (`os.getenv`) e nunca hardcode tokens, senhas ou chaves.

---

## Estrutura de Saída

```
src/
├── backend/
│   ├── main.py
│   ├── models/
│   ├── routes/
│   ├── services/
│   ├── tests/
│   └── requirements.txt
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── hooks/
│   │   ├── lib/
│   │   └── main.tsx
│   ├── package.json
│   └── tailwind.config.js
└── README.md
```

---

## Backend (FastAPI)

- **Framework:** FastAPI + Pydantic v2 + SQLAlchemy 2.0
- **Banco:** especificado em `ARCHITECTURE.md`
- **Autenticação:** JWT com `python-jose`
- **Testes:** pytest + httpx (TestClient)
- **Migrations:** Alembic
- **Validação:** Pydantic models para request/response
- **Erros:** HTTPException com mensagens claras

### Exemplo de padrão:

```python
# models/user.py
class User(Base):
    __tablename__ = "users"
    id: Mapped[uuid.UUID] = mapped_column(primary_key=True, default=uuid.uuid4)
    email: Mapped[str] = mapped_column(unique=True, index=True)

# routes/auth.py
@router.post("/auth/register", response_model=UserOut)
async def register(user: UserCreate, db: Session = Depends(get_db)):
    ...
```

---

## Frontend (React)

- **Framework:** React 19 + TypeScript
- **Estilo:** Tailwind CSS (utility-first, sem CSS modules)
- **Estado global:** Zustand
- **Formulários:** React Hook Form + Zod
- **Requisições:** fetch nativo (sem axios)
- **Roteamento:** React Router v7

### Exemplo de padrão:

```tsx
// components/Button.tsx
interface ButtonProps {
  variant: "primary" | "secondary";
  children: React.ReactNode;
  onClick?: () => void;
}

export function Button({ variant, children, onClick }: ButtonProps) {
  return (
    <button
      onClick={onClick}
      className={variant === "primary"
        ? "bg-[#00154E] text-white px-4 py-2 rounded-lg"
        : "border border-[#00154E] text-[#00154E] px-4 py-2 rounded-lg"
      }
    >
      {children}
    </button>
  );
}
```

---

## CI/CD

```yaml
# .github/workflows/ci.yml
name: CI

on: [push, pull_request]

jobs:
  backend:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with: { python-version: "3.12" }
      - run: pip install -r src/backend/requirements.txt
      - run: pytest src/backend/tests/ -v

  frontend:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm ci
        working-directory: src/frontend
      - run: npm run build
        working-directory: src/frontend
```
