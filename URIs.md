
**Data:** 2026-02-25
**keyboards:** 
**links internos:** 
___

URI (Uniform Resource Identifier) "Identificador Uniforme de Recursos".

Se sua API fosse uma grande biblioteca, a URI seria a etiqueta na lombada do livro ou o endereço da estante. ELa serve para identificar, de forma única, um recurso (um objeto, um dado ou um serviço) dentro do seu sistema.


# 1. A anatomia de um URI

Uma URI não é apenas um link aleatório, ela tem uma estrutura lógica que ajuda o servidor a entender o que você está procurando.

- **Scheme (Protocolo)**: define como os dados serão transmitidos (ex: http, https).

- **Authtority (domínio/Host)**: Onde o recurso está hospedado (ex: apa.suaempresa.com)

- **Path (caminho)**: a hierarquia que aponta para o recurso (ex: /clientes/123/pedidos)

- **Query (Consulta)**: Parâmetros opcionais para filtrar ou ordenar (ex: ?status=pago).


# 2. URI vs URL: qual a diferença?

Muita gente usa os termos como sinônimos, mas há uma nuance importante. Imagine que a URI é o conceito "mãe":

- **URI (Identificador):** O nome ou endereço que identifica o recurso.
 
- **URL (Localizador):** É um tipo de URI que diz **como chegar** lá (o endereço web que você digita no navegador).
 
- **URN (Nome):** É um tipo de URI que dá um nome único, mas não diz onde o recurso está (como o ISBN de um livro).
 

**Dica de ouro:** No mundo das APIs REST, quase todas as URIs que usamos são, na prática, URLs, pois elas identificam o recurso e nos dizem como acessá-lo via HTTP.


# 3. Boas Práticas em APIs REST

Para que suas URIs sejam "profissionais" e fáceis de entender, existem algumas regras não escritas:

1. **Use Substantivos, não Verbos:**
    
    - ❌ Errado: `GET /buscarUsuario/1`
    
    - ✅ Certo: `GET /usuarios/1` (O verbo é o método HTTP, no caso, o GET).
       
2. **Use Plural para Coleções:**
    
    - Fica mais intuitivo: `/produtos` para a lista, `/produtos/42` para um item específico.        

3. **Mantenha a Hierarquia:**
    
    - Se um comentário pertence a um post: `/posts/10/comentarios`.