
**Data:** 2025-09-01
**keyboards:** 
**links internos:** 
___




# [[Conceito básico de Sistema Computacional]]


Antes de definir o OS (Operational System), precisamos saber o que é um Sistema Computacional..

1) Um ou mais processadores (cores)
2) Memória principal
3) Discos, impressoras, teclados, monito, interfaces de redes e outros dispositivos de Entrada e saída.

***Programas precisam saber lidar com todos esses elementos***.


# Componentes básicos de SC


![[Pasted image 20260303091520.png]]


O sistema computacional é um sistema complexo demais. Não apenas para ser entendido nos mínimos detalhes, como também para realizar a gerência de todos os seus componentes e usá-los de modo otimizado. Por esse motivo é que os computadores possuem um software denominado sistema operacional.

---


# [[Conceitos básicos de SO]]


## Introdução

Uma das definições possiveis para um sistema operacional (SO ou S.O) é ser constituído por um conjunto de rotinas de computação elaborado para propósitos específicos, de forma semelhante com o que ocorre com um aplicativo que utilizamos no dia a dia, por exemplo, uma planilha eletrônica (Excel).

Uma particularidade do sistema operacional é que ele se diferencia de um aplicativo de usuário ao atuar como um intermediário entre o usuário e o hardware de um computador, tornando a utilização destes mais simples

## Atenção!!!

> O programa que serve para a interação dos usuários na realidade não faz parte do sistema operacional em si, embora use o SO para realizar o seu trabalho. Na realidade, o que o usuário utiliza diretamente é uma interface de ***acesso*** ao sistema operacional. Essa interface pode ser baseada em texto (shell, ou interpretador de comandos), ou baseada em interface gráfica com icones (GUI - Graphical User Interface)


Em um computador, os programas podem ser executados em modo usuário ou kernel. Conheça a diferença entre eles:


### Modo usuário:

- Os Softwares tem acesso limitado ao hardware e normalmente os programas e aplicativos são utilizados diretamente pelos usuários.

### Modo kernel:

- O SO é o único programa executado em modo núcleo, ou kernel. Significa que o So possui o acesso completo ao hardware e consegue executar qualquer instrução possivel.



Além disso, o Sistema operacional é um **programa de controle que coordena** a execução dos programas do usuário e as operações dos dispositivos de E/S (entrada e saída); e também é um **gerenciador de recursos** de hardware, que gerencia e aloca as partes de todo um sistema complexo.


O uso de software, incluindo o sistema operacional, possibilita oferecer ao usuário uma visão daquilo que interessa a ele, ou seja, o software modulariza aquilo que o usuário vê e usa.

O uso de um SO também permite **abstrair** não apenas o hardware como também rotinas de outros softwares, ou seja, é possivel representar o funcionamento daquilo que está "abaixo" de um determinado aplicativo ou Sistema operacional


![[Pasted image 20260303092651.png|306x334]]
Essas visões de usuário, abaixo ou acima, que representam conjuntos de serviços ou funções, podem ser representadas em um modelo chamado **máquina de níveis**, ou **máquina de camadas**, conforme mostrados na imagem ao lado.

Particularmente, a abstração do hardware, ou seja, qualquer camada acima do hardware, pode ser chamada de máquina virtual.

---


# [[Evolução histórica dos sistemas operacionais]]


# Primeira geração


O período entre aproximadamente 1945 até 1955 corresponde ao surgimento da primeira geração dos computadores. Nessa época, a programação era feita em painéis de programação, e os componentes de hardware eram mais primitivos, por exemplo, empregando válvulas na composição dos circuitos lógicos.


![[image-2.png]]



# Segunda Geração


Na segunda geração de computadores, compreendida entre aproximadamente 1955 até 1965, houve a adoção dos transistores no lugar das válvulas para a composição dos circuitos lógicos, e a aplicação de sistemas de computação em lote, como exemplificado na imagem a seguir:


![[image-3.png]]


As etapas da imagem representam o seguinte:

- (a) Os programadores levavam os cartões para o leitor de cartões.  
 
- (b) O leitor de cartões gravava o lote de tarefas em fita.  

- (c) O operador levava a fita para o computador (7094) processar as informações.  

- (d) O computador executava o processamento.  

- (e) O operador levava a fita de saída para um dispositivo capaz de ler o conteúdo e enviar para a impressora.  
 
- (f) A impressora gerava as saídas.



# Terceira geração


![[image-4.png]]
Foi na terceira geração entre 1965 a 1980, que o conceito de sistema operacional foi amplamente estabelecido, trazendo inovações como multi processamento, multiprogramação, time-sharing, spooling e memória virtual.

Foi nessa geração que surgiram também circuitos integrados (CIs) e o sistema operacional **UNIX**.



# Quarta geração

Pode-se dizer que estamos na quarta geração de computadores, iniciada 1980 e durando até o momento atual no qual esta material foi escrito. Entretanto, alguns autores podem chamar os sitemas atuais de quinta geração. 

![[image-5.png|601]]

---


# MS windows e UNIX


Historicamente, há diversos tipos e denominações de sistemas operacionais. Dentre esses vários, dois se destacam por serem bastante conhecidos e utilizados, e por ainda exercerem uma grande influência na evolução de todo o contexto tecnológico relacionado aos computadores: Windows e Unix.


## Windows

Vamos, a seguir, conhecer a história do Windows, um dos sistemas operacionais mais conhecidos:

###### MS-DOS:

A história do Windows começa com o MS-DOS (Disk Operating System), um sistema operacional de 16 bits monoprogramável, monousuário e com interface de linha de comando, lançado pela Microsoft em 1981 para o IBM-PC.

###### MS Windows 1.0:

Em 1985, foi lançado o MS Windows 1.0, introduzindo uma interface gráfica para o MS-DOS. As versões seguintes continuaram mantendo o MS-DOS como núcleo de SO (tais como Windows 3.0, Windows 95, Windows 98 e Windows Me).


###### Windows NT:

Paralelamente às versões baseadas no MS-DOS, o Windows NT foi lançado em 1993. Com sistema de 32 bits, possuía multitarefa preemptiva, multithread (SO executa threads (tarefas) de forma simultânea, sem uma interferir na outra), memória virtual e suporte a múltiplos processadores simétricos, nas versões desktop e servidores. Possuía um núcleo completamente novo, mas com compatibilidade parcial com aplicações legadas dos sistemas MS-DOS, além de mesma interface gráfica das versões existentes.


###### Windows 2000:

O Windows 2000 foi uma evolução do Windows NT 4. Sua versão utilizava a mesma arquitetura interna do Windows NT4, apresentando, entretanto, algumas novas funções, tais como o plug and play e o serviço de diretórios Active Directory.


###### Windows XP:

O Windows XP foi lançado no ano de 2001. A partir do seu lançamento, a Microsoft começou a descontinuar as famílias DOS-Windows e Windows NT/2000, integrando as duas linhas de sistemas operacionais.


##### Versões recentes:

Desde então, outras versões foram lançadas direcionadas para desktops (Windows Vista, Windows 7, Windows 8, Windows 10) e servidores (Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2016, Windows Server 2019).



## Unix


##### 1965:

O MIT, a Bell Labs e a General Electric se uniram para desenvolver o MULTICS (MULTiplexed Information and Computing Service), um esforço para desenvolver um verdadeiro sistema operacional de tempo compartilhado.


##### 1969:

Após a Bell Labs se retirar do projeto, Ken Thompson, pesquisador envolvido no projeto do MULTICS, desenvolveu sua própria versão em Assembly para um minicomputador PDP-7, chamada de UNICS (UNiplexed Information and Computing Service) e, mais para frente, de Unix. Para torná-lo mais fácil de ser portado para outras plataformas, Thompson desenvolveu a linguagem B e reescreveu o código do sistema nessa nova linguagem. Thompson e Dennis Ritchie evoluíram a linguagem, criando o C.


##### 1973:

O Unix foi reescrito em C e portado para um minicomputador PDP-11. Depois disso várias universidades começaram a licenciar o Unix, como a Universidade de Berkeley, na Califórnia, que desenvolveu sua própria versão do sistema, chamada BSD (Berkeley Software Distribution), com várias melhorias, tais como a memória virtual, C shell, Fast File System, sockets, e o protocolo TCP/IP.


##### 1991 (Linux):

O finlandês Linus Torvalds iniciou o desenvolvimento do Linux, baseado no Minix, que correspondia a uma variante do Unix. O Minix foi desenvolvido pelo professor Andrew Tanenbaum, da Holanda, com finalidade educacional.



> A mais importante tentativa de unificação das diversas versões do Unix foi feita pelo IEEE através do seu comitê POSIX (Portable Operating System Unix), que resultou em uma biblioteca padrão de chamadas e um conjunto que todo sistema unix deveria oferecer.


---


# [[Tipos de Sistemas operacionais]]

# Características

Cada sistema operacional possui características únicas que influenciam diretamente o seu desempenho e eficiência. A clissficiação em sistemas monoprogramáveis, multiprogramáveis e com múltiplos processadores ajuda a entender como os recursos de hardware são gerenciados.


Na imagem a seguir, veremos como os sistemas operacionais podem ser classificados:

![[image-6.png]]


---


![[image-7.png|361x279]]
Os sistemas **monoprogramáveis** também são chamados de sistemas **monotarefa**. Nesses sitemas, os principais módulos computacionais (processador, memória e periféricos) ficam alocados exclusivamente exclusivamente para a execuçAo de um único programa, sendo que qualquer outra aplicação deve esperar para poder ser processada. Veja a configuração desse tipo de sistema na imagem ao lado.

---

Já nos **sistemas multiprogramáveis** ou **multitarefa**, os recursos computacionais passar a ser compartilhados entre usuários e aplicações, permitindo que muitas aplicações compartilhem os mesmos recursos.

Por exemplo, alguns aplicativos podem usar o processador enquanto um determinado programa aguarda o desfecho de um comando de leitura/gravação em mídia de armazenamento. Veja, na imagem a seguir, como esse sistema funciona:


![[image-8.png]]


Vamos conhecer a seguir como os sistemas multiprogramáveis pode ser classificados. Na imagem, podemos notar que o sistema operacional é responsável por gerenciar vários desses programas ao mesmo tempo:


![[image-9.png]]

---

Um dos problemas que ocorriam nos sistemas monoprogramáveis é que havia um desperdício na utilização do processador, o que não ocorre nos sistemas multiprogramáveis. Veja a seguir, a difereça:

### Monoprogramável

![[image-10.png|415x260]]
Neste sistema, enquanto uma leitura em disco era realizada, o processador permanecia ocioso, e o tempo de espera até que a leitura em disco fosse realizada era relativamente longo, pois as operações com dispositivos E/S são muito lentas quando comparadas com a velocidade do processador para a execução de instruções.

### Multiprogramável

![[image-11.png|403x234]]Já neste sistema, o processador é utilizado por diversos programas, ou processos, de forma concorrente, ou seja, quando tem um processo tem uuma operação de E/S, outro processo pode utilizar o processador.



---

A utilização da CPU como função da quantidade de processos carregados na memória simultâneamente é chamada grau de multiprogramação. A imagem a Seguir apresenta um gráfico representando a utilização da CPU *versus* o grau de multiprogramação

![[image-12.png]]

Pode-se perceber, pela imagem anterior, que, para a curva de "80% de espera de E/S" , se os processos pararem 80% do seu tempo esperando por dispositivos de E/S, pelo menos 10 processos devem esttar na memória simultaneamente, para que a CPU desperdice menos de 10%.

![[image-13.png]]

---

Por fim, os **sistemas com múltiplos processadores** possuem dois ou mais processadores atuando juntos, oferecendo vantagens como:


### Escalabilidade:

- Aumenta a capacidade de processamento


### Disponibilidade:

- Se um processador falhar, outro pode assumir a carga de trabalho.

## Balanceamento de carga:

- Distribui a carga de trabalho entre os processadores.

---

Em sistemas com múltiplos processadores, os processadores podem se comunicar de duas maneiras: 

- Nos sistemas ***fortemente*** acoplados

- Nos sistemas ***fracamente*** acoplados


### Sistemas fortemente acoplados:

Nos sistemas fortemente acoplados, os processadores compartilham somente a memória principal e os periféricos são gerenciados por um único sistema operacional. Veja como esse sistema funciona:


![[image-14.png]]


Os Sistemas fortemente acoplados ainda podem ser dividos em:


**SMP - Symmetric Multiprocessors** 

- Os processadores acessam a memória uniformemente ao longo do tempo


**NUMA - Non-Uniform Memory Access**

- Como existem conjuntos de processadores e memória principal, e um conjunto se conecta aos outros por meio de uma rede de interconeção, o tempo de acesso dos processadores à memória varia conforme a localização física.
---


### Sistemas fracamente acoplados


Ja nos sistemas fracamente acoplados, dois ou mais sistemas computacionais independentes (cada um possui seu próprio sistema operacional e gerencia seus próprios recursos, como processador, memória e periféricos) estão conectados por linha de comunicação. Veja como isso acontece:


![[image-15.png]]

---

Os sistemas com múltiplos processadores também podem ser chamados de sistemas avançados de processamento. Eles podem ser constituídos de computadores com vários processadores, processadores com vários núcleos e sistemas distribuídos. O SO deve estar adptado para operar esses sistemas.