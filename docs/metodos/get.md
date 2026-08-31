# GET

O **GET** serve para **buscar / consultar informações** de uma API.

Ele **não altera dados**, apenas **retorna informações** do servidor.

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

# 🔎 Exemplo no Serverest

## 🎯 1️⃣ Listar todos os produtos

```
GET https://serverest.dev/produtos
```

👉 Retorna uma lista com todos os produtos cadastrados.

---

## 🎯 2️⃣ Buscar um produto específico

```
GET https://serverest.dev/produtos/ID_DO_PRODUTO
```

👉 Retorna apenas aquele produto.

---

# 📦 Exemplo de Resposta

```json
{
  "_id": "12345",
  "nome": "Produto Teste",
  "preco": 470,
  "descricao": "Produto para teste",
  "quantidade": 381
}
```

---

# 🧠 Quando usar GET?

Use GET quando você quiser:

✔ Listar produtos
✔ Buscar usuário
✔ Ver detalhes de um pedido
✔ Consultar informações
✔ Fazer filtros (ex: ?nome=Mouse)

---

# ⚠️ Regras importantes do GET

* ❌ Não deve modificar dados
* ❌ Não deve criar registros
* ✅ Pode usar Query Params
* ✅ Pode ser cacheado
* ✅ É seguro (safe method)

---

# 🧪 Exemplo no Postman

### URL:

```
{{baseUrl}}/produtos
```

### Test básico:

```javascript
pm.test("Status 200", function () {
    pm.response.to.have.status(200);
});
```

---

# 🎯 Resumo Final

👉 **GET é para ler dados.**
👉 Ele é usado para consulta.
👉 Nunca deve alterar nada no banco.

---

Desafio:

* 🔥 Qual a diferença entre GET e POST na prática
* 🔥 O que são Query Params no GET
* 🔥 Por que GET não deve ter Body
* 🔥 Como usar GET para testes automatizados no Postman
