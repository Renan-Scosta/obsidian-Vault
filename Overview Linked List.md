
**Data:** 2025-08-23
**keyboards:** #Linked-list #listas-ligadas 
**links internos:** 
___

##### **O que é uma Linked List** 

É uma **estrutura de dados dinâmica**, formada por uma sequência de **Nós (nodes).**

Cada nó contém:

1. **O valor (dados)**.
2. **Um ponteiro(referência)** para o próximo nó.

Em uma **Doubly Linked List**, cada nó tembém aponta para o anterior.


##### Como funciona na memória

Diferente do array que é contíguo, a linked list não precisa de memória contínua.

- cada nó pode estar em qualquer lugar da RAM.
- A ligação é feita pelos ponteiros que conectam os nós entre si.

Exemplo de uma **Syngle linked list** com valores ==[10 -> 20 -> 30]==:

em rust:
Nó1: [10 | ref -> 0x2000]   (endereço 0x1000)
Nó2: [20 | ref -> 0x3000]   (endereço 0x2000)
Nó3: [30 | ref -> NULL]     (endereço 0x3000)

- o "head" da lista guarda o endereço do primeiro nó (0x1000).
- Cada nó aponta para o próximo.
- O ultimo nó aponta para ==Null==.

##### **Propriedades importantes**:

1. **Alocação dinâmica**. 
	- Cresce ou diminui de tamanho sem precisar realocar tudo.
	- Inserir/remover nós é eficiente (O(1)) se você já tiver a referencia do ponto certo
2. **Não contíguo na memória
	- Pode aprovietar espaços livres espalhados na RAM.
	- Diferente do aray que exige bloco contínuo
3. **Acesso sequencial**
	- Para acessar list[5], você precisa percorrer do comço até quitno nó -> O(n).
	- Não existe acesso direto com o array.
4. **Custo extra de memoria** 
	- Cada nó precisa guardar, alem do valor, pelo menos um ponteiro (ou doi, na double linked list)

### **Resumo final**:

- **Linked list** = sequência de nós ligados por ponteiros.
    
- **Na memória**, cada nó pode estar em qualquer lugar, não precisa ser contínuo.
    
- É ótima para inserções/remoções, mas ruim para acesso direto a elementos.