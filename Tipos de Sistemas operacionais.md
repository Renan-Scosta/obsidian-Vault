
**Data:** 2026-03-03
**keyboards:** 
**links internos:** 
___

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

---
---
---


# Outras classificações dos sistemas operacionais:


