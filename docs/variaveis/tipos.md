# Tipos de Variáveis no Postman

O Postman possui diferentes tipos de variáveis, cada um com um escopo específico. O escopo determina onde a variável pode ser utilizada e qual valor terá prioridade quando existem variáveis com o mesmo nome.

Tipos de Variáveis

Os principais tipos de variáveis no Postman são:

Global
Environment
Collection
Data
Local
1. Variáveis Globais

As variáveis Global ficam disponíveis em todo o workspace do Postman.

São úteis quando um valor precisa ser utilizado em diferentes Collections e ambientes.

Exemplo
{{company_name}}


Valor:

Minha Empresa


Uma variável global pode ser utilizada em diferentes requisições e Collections.

Quando utilizar

Utilize variáveis globais para valores que realmente precisam estar disponíveis de forma ampla.

Exemplo:

{{company_name}}

2. Variáveis de Environment

As variáveis de Environment são associadas a um ambiente específico.

São muito utilizadas quando uma API possui diferentes ambientes, como:

Desenvolvimento
Homologação
Produção


Por exemplo, podemos utilizar a mesma variável:

{{base_url}}


Com valores diferentes em cada ambiente:

Ambiente	base_url
Desenvolvimento	https://dev.api.exemplo.com
Homologação	https://hml.api.exemplo.com
Produção	https://api.exemplo.com

Assim, as requisições podem permanecer iguais:

{{base_url}}/usuarios

Quando utilizar

É o tipo mais indicado para valores que mudam de acordo com o ambiente.

Exemplos:

{{base_url}}
{{client_id}}
{{access_token}}

3. Variáveis de Collection

As variáveis de Collection ficam associadas a uma Collection específica.

Elas podem ser utilizadas pelas requisições pertencentes àquela Collection.

Exemplo

Uma Collection possui:

{{api_version}}


Valor:

v1


Uma requisição pode utilizar:

{{base_url}}/{{api_version}}/usuarios

Quando utilizar

Utilize variáveis de Collection quando o valor estiver relacionado especificamente às requisições daquela Collection.

Exemplos:

{{api_version}}
{{service_name}}
{{default_timeout}}

4. Variáveis de Data

As variáveis de Data são utilizadas principalmente durante a execução de uma Collection com dados externos, como em testes realizados pelo Collection Runner.

Os valores podem ser fornecidos por arquivos de dados, como:

CSV
JSON

Exemplo

Um arquivo de dados pode conter:

username,email
joao,joao@email.com
maria,maria@email.com


Durante a execução, os valores podem ser acessados utilizando:

{{username}}


e:

{{email}}


Cada iteração da execução utiliza uma linha diferente dos dados.

Quando utilizar

Utilize variáveis de Data quando for necessário executar uma mesma requisição várias vezes utilizando diferentes conjuntos de dados.

Exemplo:

{{username}}
{{email}}
{{product_id}}

5. Variáveis Locais

As variáveis Local possuem o menor escopo e são utilizadas apenas durante uma execução específica.

Elas podem ser definidas e utilizadas em scripts.

Exemplo:

pm.variables.set("user_id", "123");


Depois, o valor pode ser recuperado:

const userId = pm.variables.get("user_id");


Também pode ser utilizado em uma requisição:

{{user_id}}

Quando utilizar

Utilize variáveis locais quando o valor não precisa ser persistido ou compartilhado com outros ambientes, Collections ou requisições.

Comparação dos Tipos
Tipo	Escopo	Uso comum
Global	Workspace	Valores compartilhados em todo o workspace
Environment	Ambiente selecionado	URLs, tokens e configurações por ambiente
Collection	Collection	Valores específicos de uma Collection
Data	Iteração	Dados utilizados em execuções automatizadas
Local	Execução/contexto local	Valores temporários
Prioridade entre Variáveis

O Postman possui diferentes níveis de escopo. Quando existem variáveis com o mesmo nome em diferentes escopos, o valor do escopo mais específico tem prioridade.

De forma geral, a prioridade segue:

Global
  ↓
Collection
  ↓
Environment
  ↓
Data
  ↓
Local


Por isso, é importante evitar utilizar o mesmo nome de variável em diferentes escopos sem necessidade.

Exemplo

Imagine que exista:

Global:
base_url = https://global.api.com


e:

Environment:
base_url = https://dev.api.com


Ao utilizar:

{{base_url}}


o Postman utilizará o valor correspondente ao escopo de maior prioridade.

Qual tipo utilizar?

Uma forma simples de escolher é:

Global: valor compartilhado por todo o workspace.
Environment: valor que muda entre Desenvolvimento, Homologação e Produção.
Collection: valor específico de uma Collection.
Data: valor fornecido para cada iteração de uma execução.
Local: valor temporário utilizado durante uma execução ou contexto específico.
Exemplo de organização

Para uma API, uma organização comum seria:

Environment
├── base_url
├── client_id
└── access_token

Collection
├── api_version
└── service_name

Data
├── username
├── email
└── product_id

Local
└── temporary_id


Essa separação ajuda a manter as requisições organizadas e facilita a reutilização dos mesmos testes em diferentes ambientes.