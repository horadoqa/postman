# CICD

É possível disparar testes de performance do Postman Cloud a partir do GitHub Actions. O caminho é usar a **API do Postman** para iniciar o teste.

Em outras palavras:

**GitHub Actions → chama API do Postman → inicia teste de performance na cloud.**

---

## 🧩 Componentes envolvidos

* Postman (onde o teste de performance roda)
* GitHub (pipeline CI/CD)
* GitHub Actions (workflow)

---

# ⚙️ Fluxo geral

```text
GitHub Actions
      │
      │ HTTP request
      ▼
Postman API
      │
      ▼
Postman Cloud
      │
      ▼
Inicia Performance Test
```

---

# 🔑 Passos necessários

### 1️⃣ Criar um API Key no Postman

No Postman:

```
Settings → API Keys → Generate API Key
```

Depois salve essa chave como **secret no GitHub**:

```
POSTMAN_API_KEY
```

em:

```
Repo → Settings → Secrets → Actions
```

---

### 2️⃣ Criar um workflow que chama a API do Postman

Exemplo simples usando `curl`.

```yaml
name: Start Postman Performance Test

on:
  workflow_dispatch:

jobs:
  run-test:
    runs-on: ubuntu-latest

    steps:
      - name: Start performance test
        run: |
          curl --request POST \
          --url https://api.getpostman.com/performance-tests/YOUR_TEST_ID/run \
          --header "X-Api-Key: ${{ secrets.POSTMAN_API_KEY }}"
```

Esse endpoint **dispara o teste na infraestrutura do Postman Cloud**.

---

# 📊 O que acontece depois

Quando o teste inicia:

* Postman executa o **load test**
* gera métricas
* salva resultados

Exemplo de métricas:

* latency
* throughput
* error rate
* requests/sec

---

# 💡 Arquitetura comum em empresas

Pipeline típico:

```text
GitHub Actions
      │
Build + Deploy
      │
Start Postman Performance Test (API)
      │
Wait for results
      │
Fail pipeline if SLA broken
```

---

# ⚠️ Limitações

* requer **Postman Performance Testing habilitado**
* precisa de **workspace com permissão**
* testes são executados **na infraestrutura do Postman**

---

✅ **Resumo**

| Ação                                      | Possível |
| ----------------------------------------- | -------- |
| Rodar performance test Postman via Newman | ❌        |
| Rodar performance test Postman via API    | ✅        |
| Disparar via GitHub Actions               | ✅        |
| Executar teste na cloud do Postman        | ✅        |

---

💡 Próximos passos com métodos bem mais avançados (e usado em DevOps):

* pipeline que **dispara o teste**
* **espera terminar**
* **analisa as métricas**
* **falha o deploy se a API ficar lenta**

Isso é um **pipeline de performance gate** (muito usado em fintechs e big tech).
