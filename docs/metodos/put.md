# PUT

O **PUT** serve para **atualizar completamente um recurso já existente**.

👉 Ele substitui todos os dados daquele registro.

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

# 🎯 Quando usar PUT?

Use PUT quando quiser:

✔ Atualizar todos os dados de um produto
✔ Atualizar todos os dados de um usuário
✔ Substituir completamente um registro

---

# 🛒 Exemplo no Serverest

## 🔹 Atualizar Produto

```
PUT https://serverest.dev/produtos/ID_DO_PRODUTO
```

### Headers:

```
Authorization: SEU_TOKEN
```

### Body (JSON):

```json
{
  "nome": "Produto Atualizado",
  "preco": 999,
  "descricao": "Produto atualizado via PUT",
  "quantidade": 10
}
```

👉 Aqui você precisa enviar **todos os campos**, mesmo que só queira alterar um.

---

# 📦 O que acontece?

Se o produto antes era:

```json
{
  "nome": "Mouse",
  "preco": 50,
  "descricao": "Mouse simples",
  "quantidade": 100
}
```

Após o PUT, ele será totalmente substituído pelo novo JSON.

---

# ⚠️ Características do PUT

* ✅ Atualiza recurso existente
* ✅ É idempotente
* ❌ Pode sobrescrever dados se esquecer algum campo
* ❌ Não é para criar novo (normalmente)

---

# 🧠 O que é Idempotente?

Significa que:

👉 Se você enviar a mesma requisição PUT 10 vezes, o resultado final será o mesmo.

Diferente do POST, que pode criar 10 registros diferentes.

---

# 🧪 Exemplo de Teste no Postman

```javascript
pm.test("Status 200 - Atualizado", function () {
    pm.response.to.have.status(200);
});
```

---

# 🔥 Diferença entre PUT e PATCH

| PUT                               | PATCH                       |
| --------------------------------- | --------------------------- |
| Atualiza tudo                     | Atualiza parte              |
| Envia todos os campos             | Envia só o que quer alterar |
| Pode apagar dados se faltar campo | Não substitui tudo          |

---

# 🎯 Resumo Final

👉 **PUT substitui completamente um recurso existente.**
👉 É usado para atualização total.
👉 É idempotente.

---

Desafio:

* 🔥 Qual a diferença real entre PUT e POST
* 🔥 PATCH na prática
* 🔥 Erros comuns usando PUT
* 🔥 Exemplo completo no Postman com token
