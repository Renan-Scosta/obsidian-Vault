
**Data:** 2025-09-01
**keyboards:** 
**links internos:** 
___




# [[Conceitos básicos de Sistemas Operacionais]] 

- **O que é:** O Sistema Operacional (SO) é o gerente do computador. Ele controla o hardware para que você consiga usar os programas sem complicação.
 
- **História:** Evoluiu de máquinas gigantes com válvulas para os sistemas modernos (Windows e Linux) que usamos hoje.
 
- **Eficiência:** Antigamente, o computador fazia uma coisa por vez (**monotarefa**). Hoje, ele é **multitarefa**, rodando vários programas ao mesmo tempo para não deixar o processador parado.

- **Processadores:** O sistema pode usar um ou vários processadores trabalhando juntos, seja compartilhando a mesma memória ou conectados por rede.

---
---

# [[Processos e Gerencia de Processador pt. 1]]

### 1. Conceitos de Processos

- **Definição de Processo:** O programa em execução (entidade ativa) e seu espaço de endereçamento.
- **Pseudoparalelismo:** A rápida alternância da CPU entre processos que cria a ilusão de execução simultânea.
- **Diferença Programa vs. Processo:** O programa é uma entidade passiva; o processo possui contador de instruções e registradores ativos.

### 2. Ciclo de Vida do Processo

- **Criação:** Ocorre na inicialização (daemons), por chamadas de sistema (syscalls), por ação do usuário ou tarefas em lote.
- **Encerramento:** Pode ser voluntário (saída normal ou por erro) ou involuntário (erro fatal ou interrupção por outro processo).

### 3. Hierarquia de Processos

- **Árvore de Processos:** Relação pai e filho; no Linux, todos derivam do processo raiz `systemd` (ou `init`).
- **Grupos de Processos:** Organização de um processo e todos os seus descendentes.
### 4. Estados e Transições

- **Estados Principais:** Novo, Pronto, Executando, Bloqueado e Terminado.
- **Mecânica de Troca:** Transições baseadas em disponibilidade de CPU, interrupções do SO ou espera por operações de Entrada/Saída (I/O).

### 5. Mecanismos de Gerência

- **Bloco de Controle de Processo (PCB):** Tabela contendo informações vitais como PID, registradores e privilégios.
- **Escalonador:** Componente responsável por decidir qual processo será o próximo a ocupar a CPU.
- **Troca de Contexto (Context Switching):** Ato de salvar o estado do hardware, software e memória de um processo para carregar outro.

### 6. Implementação no Linux (Syscalls)

- **`fork()`:** Cria um processo filho idêntico ao pai.
- **`execve()`:** Substitui a imagem de memória para executar um novo programa.
- **`waitpid()`:** Sincroniza o pai com o término do filho.
- **`exit()`:** Finaliza a execução e retorna o status.

---

# [[Processos e Gerencia de Processador pt. 2]]

