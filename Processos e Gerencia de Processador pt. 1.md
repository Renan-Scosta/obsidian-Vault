
**Data:** 2026-03-10
**keyboards:** #syscalls #Linux #sistemas-operacionais #processos #CPU 
**links internos:** 
___

# Introdução

Neste tema, estudaremos os conceitos de processos e como eles são utilizados para tirar proveito da capacidade de multiprocessamento dos equipamentos atuais. Para isso, veremos a criação de subprocessos e como eles se comunicam. Estudaremos também o funcionamento das threads, que são linhas de execução concorrentes dentro de um processo, fornecendo ao programador os mecanismos necessários para permitir a conccorrência dentro de um processo.

Por fim, destacaremos os cuidados que devemos ter ao desenvolver sistemas que acessam dados compartilhados e os mecanismos que permitem o desenvolvimento seguro de tais aplicações.



# MODELO DE PROCESSO

Os primeiros sistemas permitiam a execução de apenas um programa de cada vez, que deveria ter o controle completo do sistema e acesso a todos os seus recursos. Os sistemas permitem que diversos programa sejam carregados na memória e executados simultaneamente. 

Essa evolução tornou necessário um controle maior na divisão de tarefas dos vários programas, resultando na noção de processo.


> Em um **[[Sistema multiprogramável]]**, a unidade central de processamento (CPU) alterna entre processos, dedicando um pouco de seu tempo a cada um, dando a ilusão de paralelismo. Este esquema costuma ser chamado de pseudoparalelismo.


Neste modelo, todo software executado no computador é organizado em **processos sequenciais**, também chamado de **processos**. O modelo de processos foi desenvolvido para tornar o paralelismo fácil de tratar.

### Processo

Um processo é um programa em execução, incluindo os valores atuais dos registradores e variáveis, assim como seu **[[Espaço de endereçamento]]**. Um programa por si só não é um processo, mas entidade passiva. Um processo é uma entidade ativa, com um **[[Contador de instruções]]** e um conjunto de registradores a ele associado

##### **Atenção**
> Embora dois processos possam estar associados a um mesmo programa, são duas sequências de execução distintas.

---

Conceitualmente, cada processo tem sua própria CPU. Com a CPU alterando entre os processos, a velocidade que um processo executa não será uniforme.

![[image-23.png|586x225]]

Na figura anterior, vemos um exemplo de um sistema no qual são executados os processos A, B, C, D. O processo A é executado até o instante t1, quando para, e o processo B é colocado em execução até o instante t2. Os processos alternam suas execuções até que, no instante t4, o processo D para de executar e o processo A retoma sua execução.

Como os processos alternam suas execuções de forma muito rápida, o usuário tem a ilusão de que os processos estão realmente sendo executados ao mesmo tempo.

---
---


# CRIAÇÃO E ENCERRAMENTO DE PROCESSOS

Sistemas operacionais precisam criar processos durante sua operação.

Quatro eventos principais fazem com que processos sejam criados:

![[image-24.png]]


Quando um sistema operacional é incializado, uma série de processos são criados. Alguns são processos de primeiro plano (interagem com usuários), enquanto outros operam em segundo plano (background) e não estão associados a usuários em particular. Processos que ficam em segundo plano para lidar com algumas atividades, como e-mail, páginas web, noticias, impresão, são chamados de **daemons**.

Além dos processos criados durante a inicialização do sistema, outros também podem ser criados. Muitas vezes, um processo em execução emitirá chamadas de sistemas (**Syscalls**) para criar um ou mais processos para ajuda-lo em seu trabalho. Criar processos novos é particularmente útil quando o trabalho a ser feito pode ser facilmente formulado em termos de vários processos relacionados. Em um **[[multiprocessador]]**, pro exemplo, cada processo pode ser executado em uma CPU, fazendo com que a tarefa seja realizada mais rapidamente.

Em sistemas interativos, os usuários podem começar um programa digitando um comando ou clicando duas vezes sobre um ícone. Cada uma dessas ações inicia um novo processo e executa o programa selecionado.

Tarefas em Lote costuma ser executadas em grandes sistemas. As tarefas são submetidas ao sistema e, quando o sistema operacional tem os recursos necessários para executar outra tarefa, cria um processo e executa a próxima tarefa a partir da fila de enetrada.

### atenção!!

> Em todos esses casos, um novo processo é criado por outro já existente, executando uma chamada de sistema de criação de processo. O que esse processo faz é executar uma chamada de sistema para criar o processo.
---

No **Linux**, a chamada de sistema (**syscall**) mais comum para a criação de processo é a **fork()**. Essa chamada cria um processo idêntico ao processo que a chamou. Após a **fork()**, os dois processos, o pai e o filho, têm a mesma imagem de memória, as mesmas variáveis de ambiente e os mesmos arquivos abertos.

O código a seguir, em Linguagem C, exemplifica a criação de um novo processo com a chamada de sistema **fork()**.

![[image-25.png]]


Quando **fork()** é executada, o resultado do processamento é armazenado na variável "resultado". O processo pai (que fez a chamada) recebrá na variável "resultado" o **[[PID]]**, enquanto o processo filho receberá na variável "resultado" o valor 0. Assim, para saber quem é o processo pai e quem é o processo filho, é necessário verificar o valor me "resultado".


![[image-26.png]]

Quando **fork()** é utilizado para criação de um processo que executará o código de outro programa, a chamada de sistema **execve()** deve ser utilizada para que o processo filho mude sua imagem de memória e execute o novo programa.

O código a seguir ilustra a utilização de **execve()**. Nele, o processo pai cria três processos filhos em sequência. O primeiro coloca em execução uma calculadorea, o segundo, o editor de texto **gedit**, e o terceiro, o utilitário **xeyes**.


![[image-27.png]]

Após ter executado sua tarefa, o novo processo terminará devido a uma das seguintes condições:

![[image-28.png]]

![[image-29.png]]

![[image-30.png]]

![[image-31.png]]


Em alguns sisteams, quando um processo é finalizado, todos os processos que ele criou são finalizados também. Nem o Linux nem o Windows funcionam desta forma.

----
---

# HIERARQUIA DE PROCESSOS



Em alguns sistemas, quando um processo cria outro, o processo pai e o processo filho continuam associados. O filho pode criar mais processos, formando uma hierarquia de processos. No linux, um processo e todos os seus filhos e demais descendentes formam um grupo de processos.

![[image-32.png]] 
No linux, um processo chamado **systemd** (ou **init**, dependendo da versão) está presente na imagem de inicialização do sistema. É o primeiro a ser executado e é responsável por iniciar a execução dos demais processos do sistema operacional. Cada um desses processos pode iniciar mais processos. Desse modo, todos os processo em Linux pertencem a uma única árvore, com o **systemd** (ou **init**) em sua raiz.



A imagem a seguir exemplifica a árvore de processos do meu sistema linux por meio da execução do comando **"pstree"**.



![[image-33.png|666x767]]

![[image-34.png|697|669x487]]

---
---


# ESTADOS DE PROCESSOS

Eventualmente, uum processo que está em execução necessita parar momentaneamente sua execução por estar aguardando uma informação ainda não disponível ou porque já foi executado por muito tempo e precisa libera a CPU para outro processo.

> Um processo pode transitar por diferentes estados, que dependem do sistema operacional. De forma geral, podemos dizer que um processo pode estar nos estado **novo, executando, pronto, bloqueado ou terminado**.


![[image-35.png]]




Quando um processo é criado, ele se inicia no estado **novo**. O processo já existe, mas ainda precisam ser tomadas algumas providências pelo sistema operacional possa iniciar sua execução. Quando tudo está pronto, o processo faz a transição 1 e muda para o estado **pronto**.

O processo reúne todas as condições para ser executado no estado **pronto**, faltando apenas que o processador fique disponível para a sua execução. Quando um processador fica disponível e o processo é selecionado para execução, ele faz a transição 2 e vai para o estado **executando**.

No estado **executando**, o processo tem suas instruções executadas pelo processador e três coisas podem acontecer:


#### etapa 01

- A primera delas é o processo ser executado por muito tempo. Então, o sistema operacional interrompe momentaneamente a execução do processo para colocar outro em seu lugar, ocorrendo a transição 3, que leva o processo de volta ao estado **pronto** no qual aguradará nova oportunidade de execução.


#### etapa 02

- Pode ocorrer ainda de o processo solicitar uma operação de entrada e saída (I/O) e ter de aguardar a conclusão da operação, que costuma ser demorada quando comparada a capacidade de processamento do processador de um computador. Nesse caso, ocorre a transição 4, e o processo vai para o estado **bloqueado**.


#### etapa 03

- Por último, o processo pode encerrar sua execução, realizando a transição 6 e indo para o estado **terminado**.

---

O processo que vai para o estado **bloqueado** permanece nele até que seja concluída a operação que aguardava. Quando isso ocorre, o processo passa pela transição 5 e vai para o estado **pronto** até ser novamente selecionado para a execução.


![[image-36.png]]


Para implementar o modelo de processos, o Linux mantém uma tabela de processos, com uma entrada por processo. Esta entrada é chamada de **Blocos de controle de processo** - BCP (Process Control Block - PCB) e contém todas as informações do processo. Algumas entradas BCP são:


![[image-37.png]]


O nível mais baixo do sistema operacional é o **escalonador** (também conhecido como **agendador**). Ele cuida do gerenciamento de interrupções e dos detalhes de como iniciar e parar processos. Também costuma ser muito pequeno.

Um processo passa pelas várias filas de seleção durante sua execução. Cabe ao escalonador selecionar processos destas filas e decidir qual será o próximo a ser executado.

O escalonador é chamado com muita frequência. Um processo pode ser executado por apenas alguns milissegundos (ms) e ter de esperar por ter feito uma requisição de E/S. O escalonador costuma ser chamado pelo menos uma vez a cada 100ms para realizar a troca de processos. Devido ao pequeno intervalo de tempo entre as chamadas ao escalonador, sua execução deve ser bastante rápida, para que não se gaste muito tempo de CPU com trabalho de gerência.

---
# MUDANÇA DE CONTEXTO (context switching)

Para transferir o controle da CPU de um processo a outro, é necessário guardar o estado do processo em execução e carregar o estado do processo a entrar em execução. Esta tarefa é cnhecida como **Context Switching** (Troca de contexto).

O tempo gasto na mudança de contexto varia, dependendo de fatores como velocidade da memória, quantidade de registradores e existência de instruções especiais. Este tempo costuma variar de 1 a 1000 microssegundos.


O contexto de um processo pode ser dividido em três elementos básicos:


#### Contexto de Hardware:

- O contexto de Hardware constitui-se basicamente do conteúdo dos registradores. No momento em que o processo perde a CPU, o sistema salva suas informações. Ele é fundamental para a implementação dos sistemas multiprogramáveis.

#### Contexto de Software:

- O contexto de software especifica caracteristicas do processo que influenciarão na execução de um programa. Ele define basicamente três grupos de informações sobre um processo: identificação, quotas e privilégios. A **identificação** define o processo para o sistema de forma única, através do seu PID, UID e GID. **Quotas** são os limites de cada recurso que o sistema operacional pode alocar, como número de arquivos abertos, quantidade de memória, quantidade de subprocessos que podem ser criados etc. **Privilégio** é o que o processo pode ou não fazer em relação ao sistema e outros processos.

#### Espaço de Endereçamento:

- O espaço de endereçamento é a area de memória do processo em que o programa será executado e a área de memória onde os dados do processo serão armazenados. Cada processo possui seu próprio espaço de endereçamento, que deve ser protegido dos demais.

---

# PROCESSOS NO LINUX

Os Processos no Linux se comportam como processos sequenciais tradicionais. É um sistema operacional multiUsusário/multiTarefa, que permite a execução simultânea de diversos processos, que podem pertencer a diferentes usuários.

Mesmo que haja apenas um usuário logado no sistema, é comum a existência de diversos daemons em execução.

##### Atenção!!!

>Um exemplo é o daemon de impressão, responsável por fazer a alocação da impressora e controlar o envio de trabalhos de impressão. É uma parte importante do sistema, pois permite o compartilhamento da impressora por diversos processos, possivelmente pertencentes a diferentes usuários.


A forma usual para criação de processos no Linux ocorre por meio da chamada de sistema **fork()**, conforme você já estudou neste tema.

O processo filho recebe uma cópia exata do espaço de endereçamento do processo pai. Todos os valores de variáveis e demais objetos em memória serão idênticos, porém alterações realizadas por um dos processos em qualquer conteúdo de memória não afetarão o outro.

Arquivos que foram abertos antes da chamada **fork()** permanecem abertos para o processo pai e para o processo filho. As alterações realizadas por qualquer um destes processos se tornam imediatamente disponíveis para o outro. Processos são identificados por um número inteiro conhecido como PID (identificação do processo).


Algumas chamadas de sistema do linux para o gerenciamento de procesos são:

- **fork():** Cria um processo filho idêntico ao processo pai. Para o processo pai, retorna o PID do processo filho e, para o processo filho, retorna o valor 0.

- **waitpid():** Espera até que o processo filho passado como parâmetro termine sua execução.

- **execve():** Substitui a imagem de execução de um processo, fazendo com que, no lugar do processo corrente, seja executado o código do programa passado como parâmetro

- **exit()**: Termina a execução do processo e retorna como *status* o valor passado como parâmetro.

