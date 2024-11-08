# Produtos

## Cadastrar Produtos

```bash
curl -X POST https://serverest.dev/produtos -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImhvcmFkb3FhQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoiMXEydzNlNHIiLCJpYXQiOjE3MzEwMjA2NTUsImV4cCI6MTczMTAyMTI1NX0.SD_ptxmu8v2xoYyHO6JmTjhm7_gxFILJuQ4yPSzoudQ" -H "Content-Type: application/json" -d '{"nome": "JBL, Fone de Ouvido On ear, Tune 720BT - Preto", "preco": 320, "descricao": "Fone de Ouvido", "quantidade": 381}'
```

```bash
curl -X POST https://serverest.dev/produtos -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImhvcmFkb3FhQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoiMXEydzNlNHIiLCJpYXQiOjE3MzEwMjA2NTUsImV4cCI6MTczMTAyMTI1NX0.SD_ptxmu8v2xoYyHO6JmTjhm7_gxFILJuQ4yPSzoudQ" -H "Content-Type: application/json" -d '{"nome": "Apple 2024 MacBook Air (de 13 polegadas, Chip M3 da Apple com CPU de oito núcleos e GPU de oito núcleos, 8GB Memória unificada, de 256 GB) - Cinza-espacial", "preco": 9700, "descricao": "Apple 2024 MacBook Air", "quantidade": 18}'
```

## Listar Todos os Produtos

```bash
curl https://serverest.dev/produtos
```

## Listar Produtos e filtrar

Com ID

```bash
curl https://serverest.dev/produtos/5YSkZrzmYFfLqCrw
```

Com `grep`

```bash
curl https://serverest.dev/produtos | grep "JBL"
```

Com `JQ`

```bash
curl -s https://serverest.dev/produtos | jq '.produtos[] | select(.descricao == "Fone de Ouvido")'

curl -s https://serverest.dev/produtos | jq '.produtos[] | select(.nome== "JBL, Fone de Ouvido On ear, Tune 720BT - Preto")'

curl -s https://serverest.dev/produtos | jq '.quantidade'
```

## Alterar dados de um produto

```bash
curl -X PUT https://serverest.dev/produtos/5YSkZrzmYFfLqCrw -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImhvcmFkb3FhQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoiMXEydzNlNHIiLCJpYXQiOjE3MzEwMTc4OTAsImV4cCI6MTczMTAxODQ5MH0.dAIduqXqCEx0qYpXRShVC734sgpKDWq3qbSUzXCmddc" -H "Content-Type: application/json" -d '{"nome": "JBL, Fone de Ouvido On ear, Tune 720BT - Preto", "preco": 320, "descricao": "Fone de Ouvido", "quantidade": 381}'
```

## Excluir Produto pelo ID

```bash
curl -X DELETE https://serverest.dev/produtos/8rmVy8X40dxQlDpo -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImhvcmFkb3FhQGdtYWlsLmNvbSIsInBhc3N3b3JkIjoiMXEydzNlNHIiLCJpYXQiOjE3MzEwNjA1ODQsImV4cCI6MTczMTA2MTE4NH0.xRFl-hNtXUjFv3PDA0RMu6PXezo_iV3rawyQ-xJzWdg"
```
 