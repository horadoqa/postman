# Delete

O **DELETE** serve para **remover (excluir) um recurso do sistema**.

👉 Ele apaga um registro já existente no servidor.

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

# 🎯 Quando usar DELETE?

Use DELETE quando quiser:

✔ Remover um produto
✔ Excluir um usuário
✔ Cancelar um pedido
✔ Apagar um registro

---

# 🛒 Exemplo no Serverest

## 🔹 Deletar Produto

```
DELETE https://serverest.dev/produtos/ID_DO_PRODUTO
```

### Headers:

```
Authorization: SEU_TOKEN
```

---

# 📦 Resposta esperada:

```json
{
  "message": "Registro excluído com sucesso"
}
```

👉 O produto deixa de existir no sistema.

---

# 🧠 O que acontece depois?

Se você tentar fazer:

```
GET /produtos/ID_DO_PRODUTO
```

Provavelmente vai retornar:

```
404 Not Found
```

Porque ele foi removido.

---

# ⚠️ Características do DELETE

* ✅ Remove recurso existente
* ✅ Pode ser idempotente
* ❌ Não deve criar nada
* ❌ Normalmente exige autenticação

---

# 🧪 Teste no Postman

```javascript
pm.test("Status 200 - Deletado com sucesso", function () {
    pm.response.to.have.status(200);
});
```

---

# 🧠 DELETE é idempotente?

Sim.

Se você enviar a mesma requisição DELETE 10 vezes:

* A primeira remove
* As próximas não mudam mais nada

O estado final continua o mesmo: o recurso não existe.

---

# 🎯 Resumo Final

👉 **DELETE serve para remover um recurso existente.**
👉 Ele apaga dados do sistema.
👉 Geralmente retorna 200 ou 204.

---

Desafio:

* 🔥 Fazer um resumo completo de GET + POST + PUT + PATCH + DELETE
* 🔥 Criar exercício prático para você treinar
* 🔥 Simular entrevista técnica sobre métodos HTTP
* 🔥 Montar mapa mental dos métodos
