# 📌 API de Usuários – ServeRest

Esta documentação descreve como **cadastrar, listar, filtrar, consultar, atualizar e excluir usuários** utilizando a API do **ServeRest**, com exemplos em `curl`.

---

## 🔹 Cadastrar Usuário

### Requisição

```bash
curl -X POST https://serverest.dev/usuarios \
  -H "Content-Type: application/json" \
  -d '{
    "nome": "Hora do QA",
    "email": "horadoqa@gmail.com",
    "password": "1q2w3e4r",
    "administrador": "true"
  }'
```

### Resposta esperada

```json
{
  "message": "Cadastro realizado com sucesso",
  "_id": "yGrOocbNdUJ5INSm"
}
```

---

## 🔹 Listar Todos os Usuários

```bash
curl -s https://serverest.dev/usuarios
```

Essa requisição retorna:

* Lista de usuários (`usuarios`)
* Quantidade total de registros (`quantidade`)

---

## 🔹 Filtrar Usuários

### 🔸 Usando `grep` (filtragem simples)

> ⚠️ O `grep` apenas procura texto bruto. Não é indicado para validações estruturadas de JSON.

```bash
curl -s https://serverest.dev/usuarios | grep "horadoqa@gmail.com"
```

Saída:

```text
"email": "horadoqa@gmail.com"
```

---

### 🔸 Usando `jq` (recomendado)

O **jq** é uma ferramenta de linha de comando usada para **ler, filtrar e manipular dados JSON**, funcionando como um `sed/awk` para JSON.

---

## 🔹 Buscar Usuário por Email

```bash
curl -s https://serverest.dev/usuarios \
  | jq '.usuarios[] | select(.email == "horadoqa@gmail.com")'
```

### Resposta

```json
{
  "nome": "Hora do QA",
  "email": "horadoqa@gmail.com",
  "password": "1q2w3e4r",
  "administrador": "true",
  "_id": "yGrOocbNdUJ5INSm"
}
```

---

## 🔹 Buscar Usuário por Nome

```bash
curl -s https://serverest.dev/usuarios \
  | jq '.usuarios[] | select(.nome == "Hora do QA")'
```

---

## 🔹 Obter Quantidade Total de Usuários

```bash
curl -s https://serverest.dev/usuarios | jq '.quantidade'
```

### Exemplo de retorno

```text
95
```

---

## 🔹 Buscar Usuário pelo ID

```bash
curl -s https://serverest.dev/usuarios/yGrOocbNdUJ5INSm
```

### Resposta

```json
{
  "nome": "Hora do QA",
  "email": "horadoqa@gmail.com",
  "password": "1q2w3e4r",
  "administrador": "true",
  "_id": "yGrOocbNdUJ5INSm"
}
```

---

## 🔹 Atualizar Dados do Usuário (PUT)

### Exemplo: alterar o nome do usuário

```bash
curl -X PUT https://serverest.dev/usuarios/yGrOocbNdUJ5INSm \
  -H "Content-Type: application/json" \
  -d '{
    "nome": "Hora do QA",
    "email": "horadoqa@gmail.com",
    "password": "1q2w3e4r",
    "administrador": "true"
  }'
```

### Resposta esperada

```json
{
  "message": "Registro alterado com sucesso"
}
```

---

## 🔹 Excluir Usuário pelo ID

```bash
curl -X DELETE https://serverest.dev/usuarios/yGrOocbNdUJ5INSm
```

### Resposta esperada

```json
{
  "message": "Registro excluído com sucesso"
}
```

---

## 🧠 Observações Importantes

* Utilize `jq` para validações estruturadas de dados JSON.
* O email deve ser único para cada usuário.
* Essa API é ideal para **estudos, testes e automação de QA**.
