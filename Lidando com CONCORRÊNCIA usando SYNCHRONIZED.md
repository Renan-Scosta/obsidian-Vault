
**Data:** 2026-03-04
**keyboards:** 
**links internos:** 
___


# Synchronized

O `synchronized` é uma palavra reservada do Java para garantir que apenas uma Thread por vez acesse um trecho de código específico (um Recurso).


## 1. O problema: Concorrência

Quando duas ou mais threads tentam alterar a mesma variável ao mesmo tempo, os valores podem se perder ou ficar errados.

- **Exemplo**: Se a Thread-0 e a Thread-1 somarem 1 a um contador que vale 0, o resultado deveria ser 2. Sem sincornização, as duas podem ler 0 ao mesmo tempo e gravarem "1", causando um erro de cálculo.


## 2. A solução: O "Lock" (trava)

O Java utiliza um mecanismo chamado **monitor** (ou Lock).

- Quando uma thread entra em um trecho `synchronized`, ela "pega a chave" de um objeto.

- Enquanto ela estiver lá dentro, nenhuma outra thread consegue entrar naquele código (ou em qualquer outro código que usa a mesma chave)

- Ao sair, ela devolve a chave e a próxima thread da fila pode entrar.


## 3. Formas de usar:


- **Método sincronizado**

você coloca a palavra na declaração do método. A "chave" usada é o próprio objeto onde o método está

![[image-17.png]]


- **Bloco sincronizado**

Você escolhe exatamente qual a parte do código quer proteger e qual objeto será a "chave". É mais eficiente porque não trava o método inteiro

![[image-18.png]]



## 4. Resumo técnico

- **Garante Atomicidade**: A operação é feita do início ao fim sem interrupções de outras threads.
- **Garante Visibilidade**: Garante que a alteração feita por uma thread seja vista imediatamente pelas outras.
- **Custo**: Usar `synchronized` deixa o programa um pouco mais lento, pois as threads precisam esperar em fila.


---

# Diferença entre sincronizar um método estático (da classe) e um método comum (do objeto)

No Java, toda sincornização precisa de um objeto como referência.


### 1. Sincronização de Instância (Objeto)

Quando você usa `synchronized` em um método comum, a trava é o objeto específico que você criou (o `this`).

- **Como funciona**: Se você tem dois objetos (objA e objB), a thread 1 pode mexer no objA enquanto a Thread 2 mexe no objB simultaneamente.

- **O bloqueio**: A trava só acontece se duas threads tentarem acessar o mesmo objeto ao mesmo tempo.

![[image-19.png]]



### 2. Sincronização Estática (Classe)

Quando o método é `static synchronized`, a trava é a **classe** (o arquivo `.class` na memória), e não um objeto individual.

- **como funciona**: Não importa quantos objetos você crie; existe apenas um "chave" para a classe inteira.

- **O bloqueio**: Se a thread 1 estiver executando esse método, **nenhuma outra thread** poderá executá-lo em nenhum objeto daquela classe até que a primeira termine.


![[image-20.png]]
