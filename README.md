# Projeto CRUD — Foco em API (Backend)

Este projeto tem como foco principal o desenvolvimento da **API REST em PHP**.
O frontend foi fornecido pronto e é usado para consumir/testar a API.

Este repositório contém:

- **Frontend pronto** (fornecido): [crud-frontend](crud-frontend)
- **Backend em PHP** (implementado neste projeto): [crud-backend](crud-backend)

---

## Estrutura

- [crud-frontend](crud-frontend): interface web (JavaScript)
- [crud-backend](crud-backend): API REST em PHP + armazenamento em JSON

---

## Tecnologias

- PHP 8+
- JSON como persistência de dados
- JavaScript (frontend)
- Docker (opcional, no frontend)

---

## Como rodar

### 1) Backend (API)

Na pasta [crud-backend](crud-backend), inicie o servidor embutido do PHP:

```bash
php -S localhost:8000 -t /home/aluno32/projeto-crud/crud-backend/public
```

Se a porta `8000` estiver ocupada, use outra (ex.: `8010`) e ajuste as URLs de teste/frontend.

### 2) Frontend

Você pode rodar o frontend como já está definido em [crud-frontend/README.md](crud-frontend/README.md).

> Observação: o frontend está configurado para consumir a API em `http://localhost:8000/api/users`.

---

## Endpoints da API

Base URL:

```text
http://localhost:8000/api/users
```

### GET /api/users
Lista usuários.

### POST /api/users
Cria usuário.

Corpo JSON:

```json
{
  "name": "João",
  "age": 25,
  "email": "joao@email.com"
}
```

### PUT /api/users?id=1
Atualiza todos os campos de um usuário.

### PATCH /api/users?id=1
Atualiza parcialmente um usuário.

### DELETE /api/users?id=1
Remove usuário.

---

## Exemplos com curl

```bash
# GET
curl -i http://localhost:8000/api/users

# POST
curl -i -X POST http://localhost:8000/api/users \
  -H "Content-Type: application/json" \
  -d '{"name":"João","age":25,"email":"joao@email.com"}'

# PUT
curl -i -X PUT "http://localhost:8000/api/users?id=1" \
  -H "Content-Type: application/json" \
  -d '{"name":"João Silva","age":26,"email":"joao.silva@email.com"}'

# PATCH
curl -i -X PATCH "http://localhost:8000/api/users?id=1" \
  -H "Content-Type: application/json" \
  -d '{"age":27}'

# DELETE
curl -i -X DELETE "http://localhost:8000/api/users?id=1"
```

---

## Respostas e erros

- Sucesso retorna JSON com dados e status HTTP apropriado (`200` / `201`)
- Erros retornam JSON no formato:

```json
{ "error": "mensagem" }
```

---

## Arquivos importantes do backend

- Entrada HTTP: [crud-backend/public/index.php](crud-backend/public/index.php)
- Roteamento por método: [crud-backend/src/api.php](crud-backend/src/api.php)
- Controllers: [crud-backend/src/controllers.php](crud-backend/src/controllers.php)
- Regras de negócio: [crud-backend/src/services.php](crud-backend/src/services.php)
- Persistência JSON: [crud-backend/src/data.php](crud-backend/src/data.php)
- Validações: [crud-backend/src/validation.php](crud-backend/src/validation.php)
- Configurações: [crud-backend/config/config.php](crud-backend/config/config.php)
- Base de dados em arquivo: [crud-backend/data/data.json](crud-backend/data/data.json)

---

## Observações

- O frontend foi aproveitado pronto.
- O objetivo principal é a API; o frontend serve como cliente para testes e uso.
