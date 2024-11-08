# Usuários


## Cadastrar Usuário

```bash
curl -X POST https://serverest.dev/usuarios -H "Content-Type: application/json" -d '{"nome": "Hora do qa", "email": "horadoqa@gmail.com","password": "1q2w3e4r", "administrador": "true"}'
```

## Listar Todos os Usuários

```bash
curl -s https://serverest.dev/usuarios
```

## Listar Usuários e filtrar

Com `grep`

```bash
curl -s https://serverest.dev/usuarios | grep "horadoqa@gmail.com"
```

Com `JQ`

```bash
curl -s https://serverest.dev/usuarios | jq '.usuarios[] | select(.email == "horadoqa@gmail.com")'

curl -s https://serverest.dev/usuarios | jq '.usuarios[] | select(.email == "horadoqa@gmail.com")'

curl -s https://serverest.dev/usuarios | jq '.quantidade'

curl -s https://serverest.dev/usuarios | jq '.usuarios[] | select(.nome == "Hora do QA")
```

Por ID

```bash
curl https://serverest.dev/usuarios/Ea74b1mMhtPfDrzE
```

## Alterar dados de um usuário

```bash
curl -X PUT https://serverest.dev/usuarios/cI32w3ylgrT9HLiI -H "Content-Type: application/json" -d '{"nome": "Hora do QA", "email": "horadoqa@gmail.com","password": "1q2w3e4r", "administrador": "true"}'
```

## Excluir Usuário pelo ID

```bash
curl -X DELETE https://serverest.dev/usuarios/FV39P9Hcpj8736gq
```





