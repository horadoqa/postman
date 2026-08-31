Claro — abaixo está um README focado exclusivamente em como criar variáveis no Postman, sem abordar outros recursos.

Escrita
Criando Variáveis no Postman

As variáveis no Postman permitem armazenar valores que podem ser reutilizados nas requisições, facilitando a configuração e a manutenção dos testes.

1. Criar uma variável em um Environment

No Postman:

Abra o Postman.
No menu superior, selecione Environments.
Clique em Create Environment.
Dê um nome para o ambiente.
Adicione uma variável na tabela.
Informe:
Variable: nome da variável.
Initial value: valor inicial da variável.
Current value: valor atualmente utilizado pelo Postman.
Clique em Save.
Exemplo

Crie uma variável chamada:

base_url


Com o valor:

https://api.exemplo.com


A variável poderá ser utilizada como:

{{base_url}}


Por exemplo:

{{base_url}}/users

2. Criar uma variável diretamente em uma requisição

Também é possível criar uma variável diretamente durante a edição de uma requisição.

Abra uma requisição.
Digite a variável utilizando {{ }}.

Exemplo:

{{base_url}}/users

Se a variável ainda não existir, o Postman poderá indicar que ela não foi definida.
Crie ou associe a variável ao ambiente desejado.
Informe o valor correspondente.
3. Criar uma variável de Collection

Para criar uma variável associada a uma Collection:

Localize a Collection no painel lateral.
Clique nos três pontos (...).
Selecione Edit.
Acesse a seção Variables.
Adicione a variável.
Informe o valor.
Salve as alterações.

Exemplo:

Variable: api_key
Value: 123456


A variável pode ser utilizada nas requisições da Collection como:

{{api_key}}

4. Criar uma variável global

Variáveis globais ficam disponíveis em diferentes contextos do Postman.

Para criar:

Abra Environments ou a área de variáveis globais disponível na versão do Postman utilizada.
Localize a seção de Globals.
Adicione o nome da variável.
Informe o valor.
Salve.

Exemplo:

Variable: token
Value: abc123


Utilização:

{{token}}

5. Sintaxe para utilizar uma variável

Depois de criada, uma variável é referenciada utilizando duas chaves:

{{nome_da_variavel}}


Exemplo:

{{base_url}}


Outro exemplo:

{{username}}

Resumo
Tipo	Onde é criada
Environment	Environments
Collection	Configurações da Collection → Variables
Global	Globals
Variável utilizada na requisição	{{nome_da_variavel}}

A forma mais comum para configurar valores específicos de um ambiente é criar um Environment e utilizar as variáveis com a sintaxe {{nome_da_variavel}}.

