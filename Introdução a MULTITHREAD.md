
**Data:** 2026-03-03
**keyboards:** 
**links internos:** 
___

# O que é uma Thread?

Em termos simples, uma Thread é uma "linha de execução"ou um caminho de passos que o seu programa segue.


## 1. Execução Monothread (Single-thread) 

Na execução monothread, o seu programa possui apenas **uma única linha de execução principal** (Em Java, geralmente chamada de ==main== thread). Isso siginfica que as tarefas são executadas de forma estritamente **sequencial**: uma instrução só começa depois que a anterior termina. pode ser chamado também de apenas programação sequencial.


## 2. Execução Multithread

Na execução multithread, o seu programa é dividido em **duas ou mias threads que rodam concorrentemente** (ao mesmo tempo). O Java permite que você crie várias threads dentro de um mesmo processo, e elas compartilham a mesma memória, mas executam blocos de código diferentes de forma independente.


# Paralelismo x Concorrência



#### Paralelismo:

O paralelismo requer suporte de hardware (processadores com múltiplos núcleos - multi-core). Significa que duas ou mais tarefas estão sendo executadas ao **exato mesmo instante físico**.

foco: acelerar o tempo de execução dividindo o trabalho através do hardware.

#### Concorrência: 

A concorrência é um conceito de arquitetura ou design software. Significa que o seu programa consegue gerenciar e **lidar com várias tarefas sobrepostas no tempo**, mas elas não estão, necessariamente, rodando no exato mesmo millisegundo.

Se o seu computador tiver apenas um núcleo (core) no processador, ele usará uma técnica chamada "**Context swing**" (*troca de contexto*). A CPU executa um pedacinho da Thread A, pausa, executa um pedacinho da thread B, pausa, e volta pra thread A. Isso acontece tão rápido que, para nós humanos, parece que estão rodando juntas.

foco: Estruturação do programa. Não deixar uma tarefa bloquear a outra.



# Quando usar o Multithread?


- Processos batch (em lote)

- Aplicações que executam no cliente


