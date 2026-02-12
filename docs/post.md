# POST

O **POST** serve para **enviar dados para o servidor e criar um novo recurso**.

👉 Diferente do GET (que só busca), o **POST modifica o sistema**, normalmente criando algo novo.

---

# 📌 De forma simples:

| Método | Serve para      |
| ------ | --------------- |
| GET    | Buscar dados    |
| POST   | Criar dados     |
| PUT    | Atualizar tudo  |
| PATCH  | Atualizar parte |
| DELETE | Remover         |

---

# 🎯 Quando usar POST?

Use POST quando quiser:

✔ Criar usuário
✔ Criar produto
✔ Criar pedido
✔ Fazer login
✔ Enviar formulário

---

# 🛒 Exemplo no Serverest

## 🔹 Criar usuário

```
POST https://serverest.dev/usuarios
```

### Body (JSON):

```json
{
  "nome": "Maria Silva",
  "email": "maria@email.com",
  "password": "123456",
  "administrador": "true"
}
```

---

## 📦 Resposta esperada:

```json
{
  "message": "Cadastro realizado com sucesso",
  "_id": "abc123"
}
```

👉 Perceba que ele **criou um novo usuário** e retornou o ID.

---

# 🔐 Outro exemplo: Login

```
POST https://serverest.dev/login
```

### Body:

```json
{
  "email": "maria@email.com",
  "password": "123456"
}
```

👉 Aqui o POST é usado para **enviar credenciais** e receber um **token**.

---

# ⚠️ Características do POST

* ✅ Envia dados no Body
* ✅ Cria recurso novo
* ❌ Não é idempotente (cada requisição pode criar algo novo)
* ❌ Não deve ser cacheado

---

# 🧪 Exemplo de Teste no Postman

```javascript
pm.test("Status 201 - Criado", function () {
    pm.response.to.have.status(201);
});

var jsonData = pm.response.json();
pm.expect(jsonData._id).to.not.be.null;
```

---

# 🧠 Diferença prática

| GET              | POST         |
| ---------------- | ------------ |
| Só consulta      | Cria algo    |
| Não altera banco | Altera banco |
| Não tem body     | Tem body     |

---

# 🎯 Resumo Final

👉 **POST é usado para criar ou enviar dados ao servidor.**
👉 Ele altera o sistema.
👉 Geralmente retorna **201 Created**.

---

Desafio:

* 🔥 Qual a diferença entre POST e PUT
* 🔥 O que é idempotência
* 🔥 Quando usar POST para login
* 🔥 Como fazer fluxo completo (POST + GET + DELETE)

