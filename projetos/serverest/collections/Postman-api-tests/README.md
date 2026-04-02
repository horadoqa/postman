# 🧪 Testes de API - ServeRest

Este projeto tem como objetivo validar e automatizar testes de API REST utilizando o Postman, abrangendo autenticação, testes de endpoints e execução de fluxo completo de CRUD.

---

## 🚀 Tecnologias utilizadas

- Postman
- API REST (ServeRest)
- JavaScript (scripts de testes no Postman)

---

## 🔐 Autenticação

A autenticação da API é realizada utilizando *Bearer Token*.

- O token é obtido através do endpoint de login
- O token é armazenado dinamicamente em variável de ambiente
- Todas as requisições protegidas utilizam o token automaticamente

📌 O token *não é fixo no projeto*, sendo gerado a cada execução para garantir boas práticas de segurança.

---

## 📁 Estrutura do projeto

📁 Server Rest

┣ 📁 Usuários

┃ ┣ 📁 Criação (POST)

┃ ┃ ┣ Criar usuário com sucesso

┃ ┃ ┣ Nome vazio

┃ ┃ ┣ E-mail vazio

┃ ┃ ┣ Senha vazia

┃ ┃ ┣ Administrador inválido

┃ ┃ ┣ E-mail duplicado

┃ ┃ ┗ E-mail inválido

┃ ┣ 📁 Login (POST)

┃ ┃ ┣ Login com sucesso

┃ ┃ ┣ Login com e-mail errado

┃ ┃ ┣ Login com senha errada

┃ ┃ ┗ Login com campos vazio

┃ ┣ 📁 Listagem (GET)

┃ ┃ ┣ Listar todos os usuários

┃ ┃ ┣ Buscar usuário por ID

┃ ┃ ┗ Buscar usuário com ID inválido

┃ ┣ 📁 Atualização (PUT)

┃ ┃ ┣ Atualizar com sucesso

┃ ┃ ┗ Atualizar com e-mail inválido

┃ ┗ 📁 Remoção (DELETE)

┃ ┃ ┣ Remover com sucesso

┃ ┃ ┗ Remover com ID inexistente

┃
┣ 📁 Produtos

┃ ┣ 📁 Campos obrigatórios (POST)

┃ ┃ ┣ Nome

┃ ┃ ┣ Preço

┃ ┃ ┣ Quantidade

┃ ┃ ┗ Descrição

┃ ┣ 📁 CRUD (Fluxo automatizado)

┃ ┃ ┣ POST - Criar produto

┃ ┃ ┣ GET - Buscar produto (antes)

┃ ┃ ┣ PUT - Editar produto

┃ ┃ ┣ GET - Validar edição

┃ ┃ ┣ DELETE - Deletar produto

┃ ┃ ┗ GET - Validar exclusão

┃ ┣ Criar produto duplicado (POST)

┃ ┣ Buscar produto com ID inexistente (GET)

┃ ┣ Deletar produto com ID inexistente (DELETE)

┃ ┣ Cadastro de produto com sucesso (POST)

┃ ┣ Buscar produto por ID (GET)

┃ ┣ Buscar todos os produtos (GET)

┃ ┣ Editar produto (PUT)

┃ ┣ Deletar produto (DELETE)

┃ ┣ Criar produto com preço inválido (POST)

┃ ┣ Tentar criar produto sem token de admin (POST)

┃ ┗ Criar produto com sucesso (POST)

---

## 🔄 Fluxo automatizado (CRUD completo)

A pasta *Fluxo Produto* representa o principal cenário automatizado do projeto.

### Etapas executadas:

1. Login e geração de token
2. Criação de um novo produto
3. Busca do produto criado
4. Edição do produto
5. Validação da alteração
6. Exclusão do produto
7. Validação de remoção (produto não encontrado)

📌 O ID do produto é capturado automaticamente e reutilizado entre as requisições.

---

## 🧪 Tipos de testes implementados

- ✅ Validação de status code (200, 201, 400, etc.)
- ✅ Validação de mensagens da API
- ✅ Validação de estrutura da resposta (JSON)
- ✅ Testes de fluxo completo (CRUD)
- ✅ Testes negativos (ex: produto não encontrado)
- ✅ Validação de dados após edição
- ✅ Reutilização de variáveis dinâmicas

---

## ⚙️ Automação

- Uso de scripts em JavaScript no Postman
- Armazenamento dinâmico de variáveis (token e productId)
- Execução automatizada via Collection Runner
- Encadeamento de requisições

---

## 📊 Variáveis utilizadas

| Variável    | Descrição |
|------------|----------|
| baseUrl    | URL base da API |
| token      | Token Bearer gerado dinamicamente |
| productId  | ID do produto criado durante os testes |

📌 Todas as variáveis dinâmicas são geradas automaticamente durante a execução.

---

## ▶️ Como executar o projeto

1. Importar a collection no Postman
2. Importar o environment
3. Executar o login (ou usar fluxo automatizado)
4. Rodar a pasta *Fluxo Produto* no Runner

---

## 💼 Objetivo do projeto

Este projeto foi desenvolvido com o objetivo de demonstrar conhecimentos em:

- Testes de API REST
- Automação de testes com Postman
- Boas práticas de validação
- Organização de cenários de teste
- Execução de fluxos completos de negócio

---

## 🚀 Próximos passos

- Execução via linha de comando com Newman
- Integração com CI/CD (GitHub Actions)
- Geração de relatórios automatizados

---

## 📌 Considerações finais

Este projeto simula um cenário real de testes de API, validando não apenas endpoints isolados, mas também o comportamento completo da aplicação através de fluxos automatizados.

---

💡 Projeto desenvolvido para fins de estudo, prática e composição de portfólio.
