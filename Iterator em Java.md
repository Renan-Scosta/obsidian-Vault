
**Data:** 2025-04-25
**keyboards:** 
**links internos:** 
___
# O que é Iterator?

Em essência, um Iterator em Java é um objeto que permite percorrer os elementos de uma coleção (como lists, sets, maps e etc.) de forma sequencial, sem a necessidade de expor a estrutura interna dessa coleção. Pense nele como um cursor ou um ponteiro que se move atrás dos elementos.

# Por que usar Iterators?

Você pode estar se perguntando: "Porque não usar um simples loop for com indicies?". Boa pergunta! Os iterators oferecem várias vantagens importantes:

1. **Abstração da implementação**: O Iterator fornece uma maneira uniforme de acessar os elementos, independentemente de como a coleção está implementado internamente. Você não precisa se preocupar se é um ==ArrayList== com acesso por índice ou um ==LinkedList== com nós encadeados. O Iterator cuida dos detalhes de como avançar para o próximo elemento.
___

2. **Remoção Segura de elementos**: Uma das maiores vantagens é a capacidade de remover elementos da coleção durante a iteração de forma segura, utilizando o método remove() do próprio Iterator. Tentar remover elementos de uma coleção usando loop ==for== tradicional enquanto itera pode levar erros de ==ConcurrentModificationException== ou comportamentos inesperados.
___
3. **Suporte para diferentes tipos de coleções**: A interface ==Iterator== é amplamente utilizada na API de coleções do Java. isso significa que você pode usar a mesma lógica de iteração básica para percorrer diferentes tipos de coleções, tornando seu código mais genérico e reutilizável. 


# Métodos principais:

A interface `java.util.Iterator` define três métodos principais:

- **`hasNext()`:** Retorna `true` se ainda houver mais elementos a serem percorridos na coleção e `false` caso contrário. É essencial chamar este método antes de tentar acessar o próximo elemento.
    
- **`next()`:** Retorna o próximo elemento na sequência. Se `hasNext()` retornar `false`, chamar `next()` lançará uma exceção `NoSuchElementException`.
    
- **`remove()`:** Remove o último elemento retornado por `next()` da coleção subjacente. Este método só pode ser chamado uma vez por chamada de `next()`. Se `next()` não tiver sido chamado ainda ou se `remove()` já tiver sido chamado após a última chamada de `next()`, uma `IllegalStateException` será lançada. Este método é opcional e algumas implementações de `Iterator` podem não suportá-lo (lançando `UnsupportedOperationException`).