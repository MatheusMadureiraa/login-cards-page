# Testes API

Após criar as collections e publicar os itens no ***Strapi*** utilizei o ***Insomnia*** para:
- Testes unitários
- Testar caminhos de *GET* e *GET/id*
- Validar se as permissões configuradas no *Strapi* (permiti apenas find e findOne) funcionavam
- Garantir funcionalidade para iniciar desenvolvimento front-end

## Testes GET na rota */comidas*
<img src="../assets/comidas-test.png" alt="Teste GET na rota comidas" width="70%">

## Testes GET na rota */pessoas*
<img src="../assets/pessoas-test.png" alt="Teste GET na rota pessoas" width="70%">

## Testes GET na rota */locais*
<img src="../assets/locais-test.png" alt="Teste GET na rota locais" width="70%">


### Testando se GET/ID funciona também (já que permiti findOne no *Strapi*)
<img src="../assets/locaisById-test.png" alt="Teste GET/id na rota locais" width="70%">

### Testando se outros tipos de requisições não são aceitas (é o esperado)
<img src="../assets/post-test.png" alt="Teste POST na rota locais" width="70%">

#### Conclusão
A api faz o que é esperado, permitindo acesso a GET para users logados e bloqueando outros tipos de rotas (como o POST testado acima).




