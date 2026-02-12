# Patch

O **PATCH** serve para **atualizar parcialmente um recurso já existente**.

👉 Diferente do **PUT**, ele altera **apenas os campos que você enviar**, sem substituir tudo.

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

# 🎯 Quando usar PATCH?

Use PATCH quando quiser:

✔ Alterar apenas o preço de um produto
✔ Atualizar somente o nome do usuário
✔ Mudar apenas o status de um pedido
✔ Atualizar um único campo

---

# 🛒 Exemplo Prático (Serverest)

Suponha que o produto seja:

```json
{
  "nome": "Mouse Gamer",
  "preco": 200,
  "descricao": "Mouse RGB",
  "quantidade": 50
}
```

---

## 🔹 Atualizar apenas o preço

```
PATCH https://serverest.dev/produtos/ID_DO_PRODUTO
```

### Headers:

```
Authorization: SEU_TOKEN
```

### Body:

```json
{
  "preco": 250
}
```

👉 Apenas o campo **preco** será alterado.
👉 Os outros campos continuam iguais.

---

# ⚠️ Diferença visual PUT vs PATCH

### 🔴 PUT (substitui tudo)

Se você esquecer um campo, pode apagar informação.

```json
{
  "preco": 250
}
```

👉 Pode sobrescrever o restante dependendo da API.

---

### 🟢 PATCH (altera só o enviado)

```json
{
  "preco": 250
}
```

👉 Só atualiza o preço.

---

# 🧠 PATCH é idempotente?

Depende da implementação.

* Se for atualização simples → geralmente sim.
* Se for operação incremental (ex: +10 estoque) → não.

---

# 🧪 Teste no Postman

```javascript
pm.test("Status 200 - Atualizado parcialmente", function () {
    pm.response.to.have.status(200);
});
```

---

# 🎯 Resumo Final

👉 **PATCH altera apenas parte de um recurso.**
👉 É mais seguro quando você quer mudar só um campo.
👉 Evita sobrescrever dados desnecessariamente.

---

Desafio:

* 🔥 Quando usar PUT e quando usar PATCH em projetos reais
* 🔥 Exercício comparando todos os métodos
* 🔥 Fluxo completo com POST + PATCH + GET
* 🔥 DELETE na prática

