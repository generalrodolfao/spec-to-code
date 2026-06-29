# COMPONENTS — Árvore de Componentes Frontend

> Template. Copie para `specs/COMPONENTS.md` e preencha.

---

## Stack

| Camada | Escolha |
|---|---|
| Framework | React 19 |
| Estilo | Tailwind CSS |
| Roteamento | React Router v7 |
| Estado | Zustand |
| Formulários | React Hook Form + Zod |
| Ícones | Lucide |

---

## Árvore de Componentes

```
App
├── Layout
│   ├── Navbar
│   │   ├── Logo
│   │   ├── NavLinks
│   │   └── UserMenu
│   └── Footer
├── Pages
│   ├── HomePage
│   ├── LoginPage
│   │   └── LoginForm
│   ├── RegisterPage
│   │   └── RegisterForm
│   ├── DashboardPage
│   │   ├── StatsCard
│   │   ├── RecentActivity
│   │   └── QuickActions
│   └── NotFoundPage
└── Shared
    ├── Button
    ├── Input
    ├── Modal
    ├── Card
    ├── Spinner
    └── Toast
```

---

## Estados por Componente

| Componente | Loading | Empty | Error | Edge |
|---|---|---|---|---|
| `DashboardPage` | Skeleton cards | "Nenhum dado ainda. Crie sua primeira task." | Toast + retry | Permissão negada → 403 |
| *(componente)* | | | | |

---

## Design Tokens

```css
:root {
  --color-primary: #00154E;
  --color-accent: #F17405;
  --color-bg: #FAFAFA;
  --color-text: #1A1A1A;
  --radius: 8px;
  --shadow: 0 1px 3px rgba(0,0,0,0.1);
}
```
