# **Playlist**, 

## **Testes de API com Postman usando o Serverest.dev** (simulador de e-commerce).

A ideia é que você consiga:

* Trabalhar com **GET, POST, PUT, PATCH e DELETE**
* Criar **fluxo com autenticação (token)**
* Usar **Pre-request Scripts**
* Usar **Tests (pós-script)**
* Criar **variáveis de ambiente**
* Encadear requisições**

---

# 🎯 Estrutura da Playlist

### 🔹 Módulo 1 – Configuração Inicial

1. Criando conta no Postman
2. Criando Workspace
3. Criando Environment
4. Configurando variável `baseUrl`

---

# 🔹 MÓDULO 1 — Configuração

## 🎥 Aula 1 – Criando Environment

1. Abra o Postman
2. Vá em **Environments**
3. Clique em **New Environment**
4. Nome: `Serverest - Local`
5. Crie variável:

| Variable | Initial Value                                  | Current Value                                  |
| -------- | ---------------------------------------------- | ---------------------------------------------- |
| baseUrl  | [https://serverest.dev](https://serverest.dev) | [https://serverest.dev](https://serverest.dev) |

Salve.

---

# 🔹 MÓDULO 2 — Testando GET

## 🎥 Aula 2 – GET Listar Produtos

### Endpoint:

```
GET {{baseUrl}}/produtos
```

### Passos:

1. Nova requisição
2. Método: GET
3. URL: `{{baseUrl}}/produtos`
4. Clique em Send

---

### 🧪 Tests (aba Tests)

```javascript
pm.test("Status code é 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Tempo de resposta menor que 1000ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(1000);
});

pm.test("Retorna lista de produtos", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.produtos).to.be.an("array");
});
```

---

# 🔹 MÓDULO 3 — Criando Usuário (POST)

## 🎥 Aula 3 – Criar Usuário

### Endpoint:

```
POST {{baseUrl}}/usuarios
```

### Body → raw → JSON

```json
{
  "nome": "João Teste",
  "email": "joao{{timestamp}}@teste.com",
  "password": "123456",
  "administrador": "true"
}
```

---

## 🎯 Pre-request Script (gerar timestamp)

```javascript
pm.environment.set("timestamp", new Date().getTime());
```

---

## 🧪 Tests

```javascript
pm.test("Usuário criado com sucesso", function () {
    pm.response.to.have.status(201);
});

var jsonData = pm.response.json();
pm.environment.set("userId", jsonData._id);
```

Agora temos o `userId` salvo.

---

# 🔹 MÓDULO 4 — Login e Token

## 🎥 Aula 4 – Login

### Endpoint:

```
POST {{baseUrl}}/login
```

### Body:

```json
{
  "email": "joao{{timestamp}}@teste.com",
  "password": "123456"
}
```

---

## 🧪 Tests – Salvando Token

```javascript
pm.test("Login realizado com sucesso", function () {
    pm.response.to.have.status(200);
});

var jsonData = pm.response.json();
pm.environment.set("token", jsonData.authorization);
```

Agora temos:

* userId
* token

---

# 🔹 MÓDULO 5 — Criar Produto (POST com Token)

## 🎥 Aula 5 – Cadastro de Produto

### Endpoint:

```
POST {{baseUrl}}/produtos
```

### Headers:

```
Authorization: {{token}}
```

### Body:

```json
{
  "nome": "Produto Teste {{timestamp}}",
  "preco": 470,
  "descricao": "Produto para teste automatizado",
  "quantidade": 381
}
```

---

## 🧪 Tests

```javascript
pm.test("Produto criado com sucesso", function () {
    pm.response.to.have.status(201);
});

var jsonData = pm.response.json();
pm.environment.set("productId", jsonData._id);
```

---

# 🔹 MÓDULO 6 — GET Produto Específico

## 🎥 Aula 6 – Buscar Produto

```
GET {{baseUrl}}/produtos/{{productId}}
```

### Tests

```javascript
pm.test("Retorna produto correto", function () {
    pm.response.to.have.status(200);
});

var jsonData = pm.response.json();
pm.expect(jsonData._id).to.eql(pm.environment.get("productId"));
```

---

# 🔹 MÓDULO 7 — PUT (Atualização Total)

## 🎥 Aula 7 – Atualizar Produto

```
PUT {{baseUrl}}/produtos/{{productId}}
```

### Headers:

```
Authorization: {{token}}
```

### Body:

```json
{
  "nome": "Produto Atualizado",
  "preco": 999,
  "descricao": "Produto atualizado via PUT",
  "quantidade": 10
}
```

### Tests:

```javascript
pm.test("Produto atualizado", function () {
    pm.response.to.have.status(200);
});
```

---

# 🔹 MÓDULO 8 — PATCH (Atualização Parcial)

## 🎥 Aula 8 – PATCH Produto

```
PATCH {{baseUrl}}/produtos/{{productId}}
```

⚠️ Se o endpoint não suportar PATCH, você pode simular usando PUT parcial.

### Body:

```json
{
  "preco": 1500
}
```

---

# 🔹 MÓDULO 9 — DELETE

## 🎥 Aula 9 – Remover Produto

```
DELETE {{baseUrl}}/produtos/{{productId}}
```

### Headers:

```
Authorization: {{token}}
```

### Tests:

```javascript
pm.test("Produto deletado com sucesso", function () {
    pm.response.to.have.status(200);
});
```

---

# 🔹 MÓDULO 10 — Fluxo Automatizado (Runner)

## 🎥 Aula 10 – Criando Collection

1. Crie Collection: `Serverest API Tests`
2. Organize ordem:

```
1 - Criar Usuário
2 - Login
3 - Criar Produto
4 - Buscar Produto
5 - Atualizar Produto
6 - Deletar Produto
```

3. Execute via **Runner**

Agora você tem:

* Fluxo completo
* Variáveis dinâmicas
* Token automático
* Testes automatizados

---

# 🔥 EXTRA – Validação Avançada de Schema

```javascript
var schema = {
  "type": "object",
  "required": ["_id"],
  "properties": {
    "_id": { "type": "string" }
  }
};

pm.test("Schema válido", function () {
  pm.response.to.have.jsonSchema(schema);
});
```

---

# 🚀 Resultado Final

Você aprendeu:

✔ GET
✔ POST
✔ PUT
✔ PATCH
✔ DELETE
✔ Pre-request Script
✔ Pós-script (Tests)
✔ Variáveis de ambiente
✔ Token dinâmico
✔ Execução automatizada

---

Se quiser, posso:

* 🔥 Montar um **projeto completo estilo portfólio QA**
* 🔥 Criar versão para **Newman (CI/CD)**
* 🔥 Criar exercícios práticos
* 🔥 Criar roteiro estilo curso para YouTube
* 🔥 Criar versão avançada com testes negativos

Qual próximo nível você quer? 🚀
