
**Data:** 2025-08-22
**keyboards:** 
**links internos:** 
___
# Overview do conteudo:

- **Componentes de um computador**
- **Arquiteturas de CPU**
- **Memoria**
- **Entrada e saida de dados**
- **Arquitetura de computadores** 

# Componentes de um computador

![[Pasted image 20250822182224.png]]

- the Central Processing Unit (CPU) pode ser considerado o cerébro do computador;
- Responsável pela execução de todas as tarefas e pelo processamentoa de dados;
- Todas as operações aritméticas e lógicas de um programa são executadas na cpu

# CPU


## estrutura

- Unidade de controle (**UC**) -> coordena instruções 
- ULA (unidade lógica e aritmética) -> cálculos e operações lógicas
- Registradores -> memoria ultrarrapida interna.
- Clock -> frequencia que dita a velocida da CPU

## Ciclo de instrução

- **Fetch** - busca da instrução na memoria
- **Decode** - decodifição 
- **Execute** - execução da operação.
- **Write-back** - gravação do resultado.

## Arquiteturas de CPU

- **CISC** (Complex instruction set computer): mais instrucoes, execucao mais complexa (ex: Intel, AMD).
- **RISC** (Reduced Instruction set computer): Instrucoes mais simples, maior eficiencia (ex:ARM).
- **Pipeline:** permite paralelismo nas instrucoes. 
- **Multicore**: Multiplos nucleos executando tarefas em parelelo.




# Memorias


## Hierarquia de memoria:

Registradores -> Cache -> L1, L2, L3 -> RAM -> mamoria secundaria

- Cache: Memoria ultra rapida, proxima ao processador
- RAM: Volatil, armazenamento temporario.
- ROM/EPROM/EEPROM: permanentes, usadas no firmware 
- memoria virtual: paginacao, uso do HD/SSD para simular memoria RAM.



![[Pasted image 20250822200352.png]]

- Quanto mais alto na piramide -> mais caro e mais rapido
- Quanto mais baixo - > maior capacidade, mas mais lento.



- Memorias sao componentes utilizados para armazenar dados e instrucoes em um sistema computacional.
- as memorias podem apresentar propriedades distintas, de acordo com tecnologia com que sao fabricadas



## Memoria volatil

- As memorias volateis sao aquelas que mantem o seu conteudo apenas enquanto ha alimentacao eletrica. uma vez que a alimentacao se desliga, o conteudo se perde.

![[Pasted image 20250822201729.png]]


## Memoria principal:

- Dispositivos que permite armazenamento de dados e instrucoes;
- memoria de acesso aleatorio, tambem chamada de memoria **RAM**.
- fornece espaco de armazenamento temporario para os dados e programas que estao sendo usados ativamente

![[Pasted image 20250822201757.png]]


## memoria secundaria

- memoria para armazenamento de longa duracao de dados e programa.

![[Pasted image 20250822201812.png]]


## HD X SDD


### Disco rigido (HD):

- Mais barato
- maior capacidade basica de armazenamento
- velocidade de leitura e gravacao mais lenta 
- produz som mecanico
- menos duravel que o sdd
- forma fisica maior

### Solid state disk ou disco de estado solido (SSD):

- Utilizaz uma placa eletronica com os chips de armazenamento semlhante de um pendrive
- gravacao rapida de dados
- sao silenciosos
- consomem menos energia e estao menos suscetiveis a erro de gravacao.


## Diferentes tipos de memoria RAM


![[Pasted image 20250822201913.png]]


### **Double-Data-Rate (DDR)**.

- Com a evolucao dos processadores, os fabricante precisamprojetar memorias que atendessem a demanda de processamento
- foi nos anos 2000 que surgiu o DDR

![[Pasted image 20250822202132.png]]

### Double-Date-Rate (DDR2)

- Foi lancado em 2003, permitiu na teoria que a velocidade de transmissao dobrasse, se comparado ao DDR.

![[Pasted image 20250822202331.png]]


### Double-Date-Rate (DDR3)

- foi lancada em 2007;
- o ganho de desempenho nao chegava a ser o dobro da DDR2, mas passou a ser o modelo mais utilizado.

![[Pasted image 20250822202458.png]]


### Double-Date-Rate (DDR4):

- Foi lancada em 2014.
- o ganho de desmepenho aumentou em 50% em relacao a sua anterios
- reduziu o consumo de energia


![[Pasted image 20250822202624.png]]



### Double-Date-Rate(DDR5):

- Foi lancada em 2021
- E a geracao mais recente de tecnologia de memoria e o ganho de desempenho aumentou em 50% em relacao a sua anterior.

![[Pasted image 20250822204718.png]]


1

# Componentes de Entrada e Saida de dados 

Sao Componentes que permitem interacao entra maquina e usuario.



## Primordios da computacao

- nao existia programas armazenado
- memoria em formas de linha de retardo de mercurio.


![[Pasted image 20250822205035.png]]



## [[Von Neumann]]

- Matematico de origem judaica.
- Escreveu um relatorio com 101 paginas, descrevendo formalmente o conceito de armazenamento.
- teoria dos conjuntos e logica matematica
- um dos responsaveis pela criacao do eniac.
- Responsavel pela introducao da progrmacao por software


## Arquitetura Havard:

- Separacao entre memeoria e instrucoes de dados
- mais rapida em sistemas embarcados e microcontroladores.


## Von neumann x Havard:

![[Pasted image 20250822210413.png]]


## Arquiteturas modernas 

- Multicore e Hyperthreading -> execucao paralela
- GPUs: processadores graficos usados em IA e simulacoes
- Arquitetura ARM: eficiencia energitica, usada em celulares e IoT.
- Computacao quantica (Introducaod): usa qubits, ainda experimental, potencial para revolucionar processamento


![[Pasted image 20250822210433.png]]







