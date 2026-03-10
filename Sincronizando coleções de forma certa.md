
**Data:** 2026-03-05
**keyboards:** 
**links internos:** 
___


# Não use SYNCHRONIZED com List ou Map!

Quando você trabalha com concorrência em Java, usar coleções padrão (como `ArrayList` ou `HashMap`) com múltiplas threads ao mesmo tempo vai gerar inconsistência de dados (erro silencioso) ou o erro `ConcurrentModificationException` 
A Sincronização em coleções serve para garantir que a coleção seja **thread-safe** (segura para uso por várias threads). Em Java, existem formas de lidar com isso:



# 1. Wrappers Sincronizados (não muita utilizada)

Você pega uma coleção normal e a "envolve" com uma camada de sincronização usando a classe utilitária `Collections`.

- **Exemplos**: `Collections.synchronizedList()`, `Collections.synchronizedMap()` 

- **Como funciona**: List< String > listaSegura = Collections.synchronizedList(new ArrayList< >()).  

- **Problema**: Assim como as classes legadas, isso trava a coleção inteira a cada operação. Se um thread está lendo, outra não pode escrever e nem ler ao mesmo tempo.

- **Atenção**: Se você for iterar (usar um `for` ou `Iterator`) sobre uma coleção desse tipo, você precisa colocar o bloco de iteração dentro de um bloco `synchronized` manualmente, senão o código quebra.



# 2. Coleções Concorrentes (A melhor abordagem)

Disponível no pacote `java.util.concurrent`. Elas foram desenhadas do zero para alta performance em ambiente multithread, usando algoritmos que evitam bloquear a coleção inteira.


#### `CopyOnWriteArrayList` (alternativa ao ArrayList)


- **Como funciona**: Toda vez que ocorre uma operação de escrita (adicionar, remover, alterar), ele criar uma cópia exata do array interno, faz a modificção na cópia e depois substitui o original. As operações de leitura não usam nenhum tipo de bloqueio.

- **thread-safe**: ser thread-safe (segura para threads) significa que um trecho de código, objeto ou estrutura de dados garante que as informações permanecerão consistentes e o comportamento será correto, mesmo se várias threads tentarem acessá-lo modificá-lo exatamente ao mesmo tempo.  

- **Quando usar**: Apenas quando você tem um cenário de **muitas leituras e raríssimas escritas**. Se você escrever muito, os custo de copiar o array o tempo todo vai destruir o desempenho da sua aplicação.



# `ConcurrentHashMap` (alternativa ao HashMap)


- Em vez de bloquear o map inteiro, ele bloqueia apenas a "fatia" (bucket) do map que está sendo modificada.

- Múltiplas threads podem ler e escrever ao mesmo tempo em partes diferentes do map sem esperar umas pelas outras.



# `LinkedBlockingQueue` (talvez alternativa a lista)


A LinkedBlockingQueue é uma fila (estrutura FIFO: o primeiro a entrar é o primeiro a sair) thread-safe . O grande diferencial dela está na palavra "**Blocking**" (bloqueante)


Ela é desenhada específicamente para resolver clássico da concorrência: o **padrão-consumidor**, onde uma ou mais threads geram dados e outras threads processam esses dados.


#### 1. O Comportamento Bloqueante

Ela gerencia automaticamente o estado de espera das threads dependendo da capacidade da fila, utilizando dois métodos principais:

- **`put(elemento)` (Inserir):** Se você criar a fila com um limite máximo de tamanho e ela estiver cheia, a thread que tenta inserir um novo elemento será pausada (bloqueada) automaticamente. Ela só volta a executar quando outra thread retirar um elemento, abrindo espaço.
    
- **`take()` (Remover):** Se a fila estiver vazia, a thread que tenta remover e processar um elemento será pausada automaticamente. Ela só volta a executar quando alguma thread inserir um novo item.



#### 2. Desempenho e os "Dois Bloqueios" (Two-Lock Queue)

A `LinkedBlockingQueue` é baseada em nós encadeados (Linked List). O motivo dela ser excelente para alta concorrência é a sua arquitetura de bloqueio interno.

Ela utiliza **dois locks (bloqueios) independentes**:

- Um lock exclusivo para a operação de inserção (no final da fila).

- Um lock exclusivo para a operação de remoção (no início da fila).


**O resultado prático:** Uma thread produtora pode estar adicionando um item no final da fila exatamente no mesmo milissegundo em que uma thread consumidora está retirando um item do início da fila. Elas não competem pelo mesmo bloqueio, o que reduz drasticamente o gargalo de performance.




---


# Resumo para o seu código:


- Precisa de uma lista com muita leituras e poucas escritas em paralelo? Use `CopyOnWriteArrayList`. 

- Precisa de um Mapa chave-valor rápido e acessado por várias threads? Use `ConcurrentHashMap`.

- Fugir sempre que possível de `Vector`, `Hashtable` e `Collections.synchronized...` devido ao bloqueio total da estrutura.