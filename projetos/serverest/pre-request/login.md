# Para realizar um login

```bash
// OBJETO
const postRequest = {
    url: pm.environment.get("url-serverest") + "/login",
    method: "POST",
    body: {
        mode: "raw",
        options: {
            raw: {
                language: "json"
            }
        },
        raw: JSON.stringify({
            email: "horadoqa@gmail.com",
            password: "1q2w3e4r"
        })
    }
}

// Função que trata o token e envia para uma variável GLOBAL
pm.sendRequest(postRequest, function(err, res){
    console.log(res.json())

    // let responseJson = res.json()
    // let auth = responseJson["authorization"].split(" ")
    // console.log(auth)
    // console.log(auth[1])
    // pm.globals.set("token", auth[1])
})
```