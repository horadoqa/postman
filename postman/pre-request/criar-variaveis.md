# para criar Variáveis

## Local

```bash
// Criar variáveis

pm.environment.set('nome da variável', 'valor')

pm.environment.set('randomProduct', 'product ${Math.floor(Math.random() * 101)}')
```

Global

```bash
pm.globals.set("token", auth[1])
```
