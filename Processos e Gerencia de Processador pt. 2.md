
**Data:** 2026-03-16
**keyboards:** 
**links internos:** 
___

# SUBPROCESSO

Quando um processo cria outro Processo, esse outro processo é chamado de **Subprocesso** ou **Processo filho**.

A utilização de Subprocessos permite dividir uma aplicação em partes que podem trabalhar de forma concorrente.


**Exemplo:**
Um servidor Web que aceite requisições de clientes da internet e coloque as requisições em uma fila. Uma forma simples de implementar esse servidor seria criar um processo que pegue a primeira requisição da fila, processe a requisição e devolva o resultado do processamento ao cliente que solicitou. Após isso, ele pegaria a próxima requisição e faria o mesmo trabalho.


O problema com essa solução é que ela não aproveita a capacidade de multiprocessamento dos sistemas atuais. Como existe apenas um processo em execução, somente um dos processadores do sistema é utilizado para atendimento das requisições. Além disso, se houver várias requisições complexas e demoradas e uma requisição simples, como uma pequena página HTML, entrar no final da fila, esta requisição mais simples, que poderia responder rapidamente, será atendida somente depois que todas as demais forem processadas.

A utilização de subprocessos resolve bem estes probblemas. Se o servidor, no lugar de responder sequencialmente a cada requisição, criar um subprocesso para cada uma delas, tirará o proveito da capacidade de multiprocessamento do sistema. Como *cada requisição será tratada por um processo diferente*, as requisições serão espalhadas pelos processadores do sistema, aproveitando a sua capacidade de multiprocessamento. Além disso, como as requisições serão tratadas por diferentes processos, elas serão tratadas concorrentemente.

Dessa forma, uma requisição simples, como a solitação de uma página HTML, poderá ser iniciada e respondida rapidamente, ainda que existam outras requisições complexas solicitadas anteriormente e que elas ainda estejam sendo processadas.

O trecho de código abaixo em C exemplifica a parte de um servidor web simples que criar subprocessos para atendimentos de requisições:

![[image-39.png]]


![[image-40.png]]


O uso de Subprocessos demanda consumo de diversos recursos do sistema. Sempre que uum novo processo é criado, o sistema deve alocar recursos (contexto de hardware, contexto de software e espaço de endereçamento) para ele, além de consumir tempo de CPU. Além disso, cada processo possui seu pŕoprio [[BCP]].

---
---

# THREADS

Na tentativa de diminuir tempo gasto na criação e eliminação de processos, bem como economizar recursos do sistema, foi introduzido o conceito de **thread**. Em um ambiente com múltiplos threads, não é necessário haver vários processos para implementar aplicações concorrentes.

Threads compartilham o processador da mesma maneira que um processo. cada thread possui seu próprio conjunto de registradores (contexto de hardware), porém compartilha o mesmo espaço de endereçamento com os demais threads do processo. No momento em que uma thread perde a utilização do processador, o sistema salva suas informações. threads passam pelos mesmo estados que um processo.

A grande diferença entre subprocessos e threads é em relação ao espaço de endereçamento.

![[image-41.png]]


A mudança de contexto (**Context switching**) entre threads em um mesmo processo exige uma alteração de um conjunto de registradores, mas não é necessário nenhum outro trabalho, como gerenciamento de memória, por exemplo, tornando-a mais leve que a mudança de contexto entre processos.

![[image-42.png]]

Quando múltiplos thrads estão presentes no mesmo processo, alguns campos da tabela de processo não ocorrem por processo, mas por thread.

Em alguns sistemas, os threads são gerenciados no espaço do usuário, sem o conhecimento do sistema operacional. É o caso do pacote **P-threads (POSIX)**. A comutação de threads é muito mais rápida quando é feita no espaço do usuário pelo fato de não precisar fazer uma chamada ao Kernel. Porém, quando os thrads são executados no espaço do usuário e um thrad bloqueia, todo o processo é bloqueado pelo kernel. Threads no nível de usuário também fazem com que o tempo dedicado a threads de diferentes processos não seja distribuido de forma justa.

##### Atenção!!!

>Threads são muito úteis em sistemas com múltiplas CPU, nos quais o paralelismo real é possível. Elas permitem que ocorram múltiplas execuções no mesmo ambiente, fazendo com que várias partes de um mesmo processo estejam em execução concorrente em diferentes processadores (núcleos).


O termo **multithread** também é usado para descrever a permissão de múltiplos threads no mesmo processo. Algumas CPU oferecem suporte de hardware direto para multithread e permitem que chaveamentos de threads aconteçam em uma escala de tempo de nanossegundos.

Processos com apenas uma thread são conhecidos como **monothread** 

Além de compartilhar o espaço de endereçamento, os threads podem compartilhar o mesmo conjunto de arquivos abertos, processos filhos, alarmes e sinais.

##### Atenção!!!

>É importante perceber que cada thread tem a sua própria pilha, que contém uma estrutura para cada rotina chamada, mas ainda não retornada. Essa estrutura contém as variáveis locais da rotina e o endereço de retorno para serem usados quando a chamada de rotina for encerrada.


No Linux, os threads são criados com a chamada de sistema **clone()**. Sua sintaxe é:

![[image-43.png]]



**Tipos de processos:**

Existem basicamente dois tipos de processos relacionados ao tipo de processamento que executam. nos cards a seguir, entenda cada um deles:



