# Produtos

## Cadastrar Carrinho

```bash
curl -X POST https://serverest.dev/carrinhos -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImhvcmFkb3FhQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoiMXEydzNlNHIiLCJpYXQiOjE3MzEwMjYxMTksImV4cCI6MTczMTAyNjcxOX0.18Pd_EFIdye9tQV_muAlZq05wA2RQFge2LsCmlNgoTM" -H "Content-Type: application/json" -d '{"produtos": [{"idProduto": "U59wcv6IqAx1JLCW","quantidade": 1},{"idProduto": "0HHpyQJRiJduLT1j", "quantidade": 1}]}'
```

## Listar Todos os Carrinhos

```bash
curl https://serverest.dev/carrinhos
```

## Listar por id

Com ID

```bash
curl https://serverest.dev/carrinhos/2qNmxICJTYjyekh9
```

Com `grep`

```bash
curl https://serverest.dev/carrinhos | grep "JBL"
```

Com `JQ`

```bash
curl -s https://serverest.dev/produtos | jq '.produtos[] | select(.descricao == "Fone de Ouvido")'

curl -s https://serverest.dev/produtos | jq '.produtos[] | select(.nome== "JBL, Fone de Ouvido On ear, Tune 720BT - Preto")'
```

## Excluir Carrinho pelo ID

```bash
curl -X DELETE https://serverest.dev/carrinhos/concluir-compra -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImhvcmFkb3FhQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoiMXEydzNlNHIiLCJpYXQiOjE3MzEwMjA2NTUsImV4cCI6MTczMTAyMTI1NX0.SD_ptxmu8v2xoYyHO6JmTjhm7_gxFILJuQ4yPSzoudQ"
```

```bash
curl -X DELETE https://serverest.dev/carrinhos/cancelar-compra -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImhvcmFkb3FhQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoiMXEydzNlNHIiLCJpYXQiOjE3MzEwMjA2NTUsImV4cCI6MTczMTAyMTI1NX0.SD_ptxmu8v2xoYyHO6JmTjhm7_gxFILJuQ4yPSzoudQ"
```
