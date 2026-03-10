
**Data:** 2025-11-21
**keyboards:** 
**links internos:** 
___

# entendendo backend: 


**1**
## [[Hardware, Compilador, Interpretador, Sistema operacional, Processos, Threads, forks etc...]]

Aqui é uma breve introdução sobre CPU, Sistema operacional, processos, forks e threads.
abordo também sobre a JVM e como ele nasceu com a ambição de abstrair o sistema operacional e toda a máquina por baixo dela. 

---

**2**

## [[Gerenciamentos de dependências um pouco mais profundo e surgimento de novas linguagens...]]

Aqui eu voltei à década de 90 e dei uma breve introdução da evolução das arquiteturas de desenvolvimento de software, retornei mais ao mundo Java e entendemos mais sobre a longa e inacabada novela chamada gerenciamento de dependências, uma praga que vai te perseguir por toda sua carreira de programação e finalmente começamos a ter um gosto das novas linguagens, começando com Groovy, Scala, Erlang, Elixir, e um pouco do Go.

---

**3** 

## [[Concorrência e paralelismo]]

Aqui falei também sobre concorrência e paralelismo e como os sistemas foram evoluindo pra resolver esse problema.

Concorrência e paralelismo. simplificando, Lembram dos computadores até os anos 90? Você podia ter tarefas que pausam e deixam outras executarem no seu lugar e ficam trocando de lugar, fazendo o tal **Context switching**. Elas são **concorrentes** mas não paralelas. Quando você tem dois ou mais cores na CPU ai sim, você realmente tem paralelismo, porque duas tarefas concorrentes, por exemplo threads, podem ser executadas verdadeiramente em paralelo. Seja em uma CPU com capacidade pra somente uma thread ou uma CPU com capacidade pra múltiplas threads, ainda assim você precisa de um **Scheduler**, porque seu programa pode modelar e gerenciar mais threads concorrentes do que existem cores físicas para executar.

---

**4**

## [[Coordenação de Concorrência]] 

Aqui eu exploro a evolução da coordenação de tarefas, demonstrando que a eficiência depende de como processos e threads se comunicam via **pipes**, **sockets** ou memória compartilhada. Discute as limitações de linguagens **mono-thread** e com travas globais (**GIL**), como Node.js e Python, que dependem de **reactors** e **I/O assíncrono** para simular concorrência. Em contraste, apresenta as **Green Threads** e o modelo de Atores (Erlang/Scala) como soluções leves que utilizam schedulers em user-land para gerenciar milhares de tarefas paralelas com baixo custo. Enfatizo que o uso de abstrações como **courotines**, **pools** e **Filas** é essencial para evitar sobrecarga de memória e o custo de chamadas de sistemas (**Syscalls**). No fim, conclui que o verdadeiro desafio da computação moderna não é o silício disponível, mas sim encontrar a maneira mais simples e barata de coordenar o trabalho concorrente.

---
