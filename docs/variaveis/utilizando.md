Claro — abaixo está um README focado somente na utilização de variáveis no Postman, sem explicar como criá-las.

Escrita
Utilizando Variáveis no Postman

As variáveis no Postman permitem reutilizar valores em diferentes partes das requisições, evitando a necessidade de informar o mesmo valor manualmente várias vezes.

Sintaxe

Para utilizar uma variável, informe seu nome entre duas chaves:

{{nome_da_variavel}}


Por exemplo:

{{base_url}}

Utilizando variáveis na URL

Uma variável pode ser utilizada diretamente na URL de uma requisição.

Exemplo:

{{base_url}}/usuarios


Se base_url possuir o valor:

https://api.exemplo.com


O Postman utilizará:

https://api.exemplo.com/usuarios

Utilizando variáveis nos parâmetros

Variáveis também podem ser utilizadas nos parâmetros da requisição.

Exemplo:

?usuario={{username}}


Ou:

?status={{status}}


Isso permite alterar o valor da variável sem precisar modificar a estrutura da requisição.

Utilizando variáveis nos Headers

Uma variável pode ser utilizada no valor de um Header.

Exemplo:

Authorization: Bearer {{token}}


Outro exemplo:

X-API-Key: {{api_key}}


Dessa forma, o valor utilizado no Header pode ser alterado através da variável.

Utilizando variáveis no Body

Variáveis podem ser utilizadas no corpo da requisição.

Exemplo em JSON:

{
  "nome": "{{nome}}",
  "email": "{{email}}"
}


O Postman substituirá {{nome}} e {{email}} pelos respectivos valores das variáveis durante a execução da requisição.

Utilizando variáveis em diferentes requisições

Uma das principais vantagens das variáveis é poder reutilizar o mesmo valor em várias requisições.

Por exemplo, utilizando:

{{base_url}}


Podemos ter:

{{base_url}}/usuarios

{{base_url}}/produtos

{{base_url}}/pedidos


Assim, caso o endereço da API seja alterado, não é necessário modificar cada requisição individualmente.

Utilizando variáveis em Scripts

As variáveis também podem ser acessadas nos scripts do Postman.

Para obter o valor de uma variável:

pm.variables.get("nome_da_variavel");


Exemplo:

const token = pm.variables.get("token");


Para definir uma variável no escopo de variáveis locais:

pm.variables.set("token", "abc123");

Visualizando o valor de uma variável

Para verificar o valor que o Postman está utilizando, passe o cursor sobre:

{{nome_da_variavel}}


O Postman pode exibir o valor associado à variável.

Também é possível utilizar o recurso de visualização de variáveis disponível no ambiente selecionado.

Substituição das variáveis

Durante a execução da requisição, o Postman substitui:

{{nome_da_variavel}}


pelo valor correspondente.

Por exemplo:

{{base_url}}/usuarios/{{user_id}}


Pode resultar em:

https://api.exemplo.com/usuarios/123


A requisição utiliza os valores das variáveis no momento da execução.

Boas práticas
Utilize nomes de variáveis claros e objetivos.
Prefira nomes em snake_case, como base_url e access_token.
Utilize variáveis para valores que aparecem em várias requisições.
Evite colocar valores que mudam frequentemente diretamente nas requisições.
Utilize {{nome_da_variavel}} sempre que precisar referenciar uma variável.
Exemplo completo

Uma requisição pode utilizar várias variáveis:

POST {{base_url}}/usuarios


Header:

Authorization: Bearer {{token}}


Body:

{
  "nome": "{{nome}}",
  "email": "{{email}}"
}


Dessa forma, a mesma requisição pode ser reutilizada alterando apenas os valores das variáveis.

