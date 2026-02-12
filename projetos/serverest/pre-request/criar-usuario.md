# Para criar um usuário

```bash
// Email a ser verificado
const email = "horadoqa@gmail.com";

// URL da API para verificar se o usuário já existe
const checkUserUrl = pm.environment.get("url-serverest") + "/usuarios";

// Faz uma requisição para verificar se o usuário já existe
pm.sendRequest({
    url: checkUserUrl,
    method: 'GET',
    params: {
        email: email  // Supondo que a API tenha um parâmetro para filtrar pelo email
    }
}, function (err, res) {
    if (err) {
        console.log("Erro ao verificar o usuário: ", err);
        pm.environment.set("userExists", false);  // Define como false se ocorrer erro na requisição
    } else {
        // Verifica a estrutura da resposta
        let users = res.json();

        // Se a resposta não for um array, tenta acessar os usuários de uma chave específica
        if (!Array.isArray(users)) {
            // Exemplo: se os usuários estão dentro de uma chave chamada 'data'
            if (users.data) {
                users = users.data;  // Ajuste conforme a estrutura real da resposta da sua API
            } else {
                console.log("Resposta inesperada. Estrutura de usuários não encontrada.");
                return;
            }
        }

        // Agora verificamos se o usuário existe no array
        const userExists = users.some(user => user.email === email);

        // Armazena o resultado de verificação na variável de ambiente
        pm.environment.set("userExists", userExists);

        if (!userExists) {
            // Se o usuário não existir, cria um novo usuário
            const createUserUrl = pm.environment.get("url-serverest") + "/usuarios";
            const newUser = {
                nome: "horadoqa",
                email: email,
                password: "1q2w3e4r",
                administrador: true
            };

            // Faz a requisição para criar o novo usuário
            pm.sendRequest({
                url: createUserUrl,
                method: 'POST',
                body: {
                    mode: 'raw',
                    raw: JSON.stringify(newUser)
                }
            }, function (err, res) {
                if (err) {
                    console.log("Erro ao criar o usuário: ", err);
                } else {
                    console.log("Usuário criado com sucesso:", res.json());
                }
            });
        } else {
            console.log("Usuário já existe.");
        }
    }
});

```