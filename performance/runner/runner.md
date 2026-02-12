# RUNNER

O Postman **não é uma ferramenta de teste de carga “de verdade”**, mas permite realizar **testes básicos de carga e desempenho** usando alguns recursos adicionais.
A seguir, explico **o que é possível e o que não é possível fazer**, além de um **passo a passo prático**.

---

## ⚠️ Antes de começar (importante)

* O Postman é indicado para **testes funcionais** e **testes simples de performance**.
* Para **carga pesada** (milhares de usuários simultâneos), o ideal é usar ferramentas como **JMeter**, **k6** ou **Gatling**.
* Ainda assim, o Postman é muito útil em **ambientes de estudo**, **APIs pequenas** ou **validações iniciais de desempenho**.

---

## ✅ Opção 1: Teste de carga simples no Postman (Collection Runner)

### 1️⃣ Crie sua requisição

* Configure o método (GET, POST, etc.).
* Defina headers, body e autenticação.
* Verifique se a requisição funciona corretamente.

### 2️⃣ Salve a requisição em uma Collection

* Clique em **Save**.
* Salve a requisição dentro de uma **Collection**.

### 3️⃣ Use o Collection Runner

* Clique em **Runner** (ou no botão **Run** da collection).
* Configure:

  * **Iterations** → número de vezes que a requisição será executada.
  * **Delay** → intervalo entre requisições (em milissegundos).
  * **Environment** → se utilizar variáveis.

**Exemplo:**

* Iterations: 100
* Delay: 0 (envia as requisições o mais rápido possível)

👉 Isso simula **várias requisições sequenciais**, não exatamente simultâneas, mas já ajuda a avaliar o desempenho.

### 4️⃣ Meça o tempo de resposta

No Postman, você pode analisar:

* **Response Time**
* **Status Code**
* **Erros**

Também é possível criar testes automáticos na aba **Tests**, por exemplo:

```javascript
pm.test("Resposta em menos de 500ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});
```

---

## ✅ Opção 2: Teste de carga usando Newman (mais poderoso)

O **Newman** é o executor de collections do Postman via **linha de comando**.

### 1️⃣ Instale o Newman

É necessário ter o **Node.js** instalado.

```bash
npm install -g newman
```

### 2️⃣ Exporte sua Collection

No Postman:

* Collection → **Export**
* Salve o arquivo `.json`.

### 3️⃣ Execute múltiplas requisições

Exemplo simples:

```bash
newman run collection.json -n 100
```

Isso executa a collection **100 vezes**.

### 4️⃣ Simule concorrência (paralelismo)

Com ferramentas externas (como scripts shell, pipelines de CI ou múltiplas instâncias do Newman), é possível rodar várias execuções em paralelo, simulando **múltiplos usuários**.

---

## 📊 O que é possível medir com Postman / Newman

✅ Tempo médio de resposta
✅ Erros (4xx / 5xx)
✅ Falhas sob carga
✅ Validação de regras de negócio

---

## ❌ Limitações do Postman

❌ Simulação realista de milhares de usuários simultâneos
❌ Controle preciso de ramp-up e ramp-down
❌ Relatórios avançados de teste de carga
❌ Testes de estresse realistas

---

## 🚀 Quando usar outra ferramenta?

Use **JMeter** ou **k6** quando precisar:

* Concorrência real
* Simular picos de acesso
* Gerar relatórios detalhados
* Testar APIs em produção (com cuidado!)

---
