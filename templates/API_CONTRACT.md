# API CONTRACT — Contrato da API

> Template. Copie para `specs/API_CONTRACT.md` e preencha.

---

## Base URL

```
https://api.exemplo.com/v1
```

## Autenticação

Todas as rotas (exceto `/auth/*`) exigem header:

```
Authorization: Bearer <token>
```

---

## Endpoints

### `POST /auth/register`

Cria novo usuário.

**Request:**
```json
{
  "email": "user@example.com",
  "password": "min.8chars",
  "name": "Fulano"
}
```

**Response 201:**
```json
{
  "id": "uuid",
  "email": "user@example.com",
  "name": "Fulano",
  "token": "jwt..."
}
```

**Erros:**

| Código | Descrição |
|---|---|
| 400 | Email inválido ou senha curta |
| 409 | Email já cadastrado |

---

### *(próximo endpoint)*

*(repetir estrutura: método, path, request, response, erros)*

---

## Paginação

Endpoints de lista aceitam:

```
GET /tasks?page=1&limit=20
```

Response inclui metadados:

```json
{
  "data": [...],
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 142,
    "pages": 8
  }
}
```

---

## Tratamento de Erros

Resposta de erro padronizada:

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Descrição amigável",
    "details": [...]
  }
}
```
