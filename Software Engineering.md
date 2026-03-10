
**Data:** 2025-08-27
**keyboards:** 
**links internos:** 
___

# Fundamentals Software Engineering 



.
# 1. Software

É importante destacar que o desenvolvimento tecnológico do hardware nos ultimos anos permitiu que o desenvolvimento de softaware cada vez mais complexos, tendo um forte impacto na indústria de software, Como exemplo, podemos apresentar a substituição do paradigma estruturado pelo paradigma orientado a objetos (OO/OO) baseado na programaçao orientada a objetos (POO/OOP) que permite o reuso intensivo de esoecificação, bem como uma melhor manuntenibilidade e, como consequência, o desenvolvimento de softwares mais complexos.

Vamos enfatizar uma das principais finalidades do software: a **Geração de informação**.

A figura 1. ilustra de forma implícita os principais componentes tecnológicos de um sistema de informaçao, i.e., hardware, software, sistema gerenciador de banco de dados, redes de comunicaçao e serviços, sendo os referidos componente interdependentes. O ambiente empresarial está representado pela respectiva pirâmide funcional cabendo ao componente software, o importante papel de agregar valor aos dados quando da geraçao de informaçoes ao diferentes níveis de gestão – operacional, gerencial e estratégico, pois  essa pode ser utilizada em um proceso de tomada de decisão ou no controle de funções empresariais, tais como financeiro, recursos humanos e outras.

![[Pasted image 20250826200918.png]]


Um segundo exemplo, vamos considerar a complexidade do desenvolvimento de um software embarcado em uma aeronave com 500 pessoas abordo e que realiza o seu controle total, em que um defeito pode ter um impacto altamente negativo.

vamos imaginar o que seria do piloto sem as informações do voo no painel de controle.

Em ambos exemplos, observamos que o software apresenta dois papéis distintos, o primeiro como um produto a ser utilizado pelos usuários, o segundo como veículo que distribui o produto, pois a comunicação entre os diversos componentes de um sistema de informação ocorre por meio de sistemas operacionais, software de comunicação entre outros.

Você consegue imaginar quais os desafios atuais de um engenheiro de software?

Destacamos que os desafios incluem sete grandes categorias:


### Software de sistema:

- Camadas de software que atendem a outros softwares, tais como, **sistemas operacionais, drivers** e outros

### Software de aplicação:

- Inclui software com escopo específico, tais como, sistema de gestão empresarial (**ERP**). 

### Software de engenharia/científico:

- Inclui software aplicado às áreas de engenharia e científica, tal como, software para cálculo estrutural na área de engenharia civil ou processamento de imagem.

### Software embarcado:

- Instalado em produtos com funções específicas, tal como, o controle de um veículo com informaçoes disponiveis no painel digital

### Software para linha de produtos:

- projeto com determinado conjunto de funcionalidades e utilizado por diferentes clientes, por exemplo, sistema emissor de nota fiscal.

### Aplicações Web/aplicativos móveis:

-  Software específico para dispositivo móvel ou desktop.

### Software de inteligência artificial:

- Utilizam técnicas de inteligência artificial, tais como, sistema especialistas, rede neurais, apendizado de maquina e outros.
# .
____


# 2. Engenharia de software

Vimos nos exemplos do software embarcado em uma aeronave ou controlando o tráfego aéreo uma caracteristica comum: a **Complexidade**. ==A melhor tratativa para a **complexidade** é a aplicação de metodologia que permita a decomposição do problema em problemas menores de forma sistemática==, cabendo à engenharia essa sistematização.

Uma premissa básica é que a engenharia permite a solução de problemas e, quanto mais complexo um produto a ser gerado, mais a engenharia se faz necessária.

Vamos ver no caso da construção de uma simples casa, talvez um engenheiro resolva o problema; e no caso de um edifício inteligente com vários andares? Neste caso, o problema tornou-se multidisciplinar, ou seja, serão necessários vários profissionais de várias áreas, e.g., arquiteto, engenheiros civis, mecânicos, elétricos, de software etc. A construção do prédio torna-se inviável caso não haja uma tratativa sistemática por meio da aplicação das melhores práticas da engenharia.
![[Pasted image 20250826201024.png]]



A mesma correlação pode ser aplicada quando o produto a ser gerado é o software. no caso do Software, aplica-se a Engenharia de Software.

O desenvolvimento de software deve submeter-se aos mesmo principios aplicado nas engenharias tradicionais, sendo um produto distinto em função da sua intangibilidade que o associa, muitas vezes, somente aos códigos dos programas de computador. Entretanto, diferentemente de outros produtos de outras engenharias em produção, possui alta volatilidade em função das constantes evoluções na tecnologia e nos requisitos, agregando ao software um complexidade adicional.



A primeira referência ao termo "Engenharia de Software" foi em 1968, em uma conferência sobre o tema, sob responsabilidade do comitê de ciência de NATO (north atlantic treaty organization). Nesse contexto, o Guide to the Software Engineering Body of Knowledge Version 3.0 (SWEBOK Guide V3.0) apresenta a seguinte definição para a Engenharia de Software:

![[Pasted image 20250826205650.png]]
___


# 3. Tecnologia em Camadas


A Engenharia de Software é uma tecnologia em camadas, como ilustra a figura 2. Vejamos as descrições das referidas camadas:

### Camada de Qualidade:

- Garante que os requisitos que atendem às expectativas do usuário serão cumpridas 

### Camada de processo:

- Determina as etapas de desenvolvimento do software.

### Camada de métodos:

- Define, por exemplo, quais as técnicas de elicitação de requisitos, os artefatos gerados em função da técnica de modelagem adotada, tal como, modelo de casos de uso ou de classes

### Camada de ferramentas:

- Estimula a utilização de ferramentas "CASE" (Computer-Aided Software Engeneering) no desenho dos diversos artefatos ou memso na geração automática de código, entre outras aplicações'a tecnologia CASE está disponível para o uso em todas as etapas do processo de desenvolvimento de software.


# .
![[Pasted image 20250826211321.png]]


Considerando um produto tangível para todos nós, você poderia imaginar que um dia construirá sua casa própria? Vamos imaginar que sim.
O que você precisa para levar em frente esta contrução? um processo?

Certamente, pois terá que organizar as etapas da construção: Fundação, estrutura, cobertura, alvenaria, instalações etc. Agora a contrução da casa fica mais fácil.

Da mesma maneira, a contrução de um software necessita de processo;
esse deverá  ocorrer de acordo com as melhores práticas estabelecidas pela engenharia de software

É importante destacar que a base da Engenharia de Software é a **Camada do processo**.


___

# 4. Processo de Software

Processo é uma sequência de etapas que permitem a geração de um produto, no nosso caso, o Software. O processo permite uma melhor tratativa em relação à complexidade de obtenção de um determinado produto, pois, na maioria das vezes, é um trabalho multidisciplinar realizado por analistas, programadores, gerentes de projeto, gerentes de testes e outros profissionais.

Assim como em todas as engenharias, a engenharia de Software possui uma diversidade de modelos para processos de desenvolvimento de software que atendem a diferentes problemas.

Um requisito importante na seleção de um processo de software é a complexidade. Basicamente, quanto maior a complixade de um sistema, mais formal deve ser o processo adotado. Importante: a qualidade é a camada base que sustenta a camada processo.

Uma metodologia de processo genérica compreende cinco atividades (figura 3)

![[Pasted image 20250826212744.png]]


### Comunicação:

- As primeira atividades de um processo de software requerem uma comunicação intensiva com os usuários, buscando o entendimento do rpoblema, a definição de objetivos para o projeto, bem como a identificação de requisitos.

### Planejamento:

- Destaca-se nesta atividade a área de conhecimento **Gerenciamento de projeto**, que permitirá a elaboração de um planode gerenciamento do projeto de forma sistemática, tendo como entrega importante o cronograma que inclui as atividades a serem desenvolvidas no referido projeto, comtenplando diferentes áreas de conhecimento.

o processo de desenvolvimento disponibiliza as principais atividades que irão compor o Plano de Gerenciamento do projeto, sendo esse plano executado e monitorado.

### Modelagem:

- A engenharia tem como melhor prática a geração de modelos, tal como uma planta baixa de uma casa. A maioria desses modelos gráficos, denominados de diagramas na enegenharia de software, podem ser complementados por descrições textuais. como exemplo, apresentamos o modelos de casos de uso que inclui diagramas de caso de uso, artefatos gráficos e descrições de cenários dos casos de uso, artefatos textuais.

### Construção:

- A partir dos modelos gerados, é realizada a construção ou implementação do software, portanto, os modelos determinam o comportamento do software. Essa atividade inclui a codificação e os teste de software de acordo com o planejamento.

### Entrega:

- Ao final ocorre o objetivo de um plano de projeto de Software, i.e, a esntrega do produto em produção de acordo com o planejado.
# .
----


# 5. Atividades de Apoio

As atividade Básicas apresentadas são complementadas pelas denominadas "Atividades de apoio", que incluem:

### Controle e acompnahmento de projeto:

- Dentro do princípio de que "não se controla o que não se mede", a etapa de gerenciamento de projeto **monitoramento e controle** permite verificar se a execução está de acordo com o planejado, pois, caso seja identificada alguma não conformidade, ações corretivas devem ser implementadas.

### Administração de riscos:

- Ênfase à área de Gerenciamento de risco, de modo que qualquer evento, positivo ou negativo que possa impactar o desenvolvimento do projeto, seja tratado.

### Garantia de qualidade do software:

- Ênfase à área de gerenciamento da Qualidade, a fim de garantir que os requisitos do projeto sejam atendidos.

### Revisões Tecnicas:

- Atividade intríseca da qualidade, pois todos os artefatos devem ser testados, inclusive, processos, modelos, código do software e outros.

### Medição:

- Outra atividade da qualidade que permite a definição de métricas para avaliar as várias atividades durante o desenvolvimento de softaware 

### Gerenciamento da configuração de software:

- Inclui os efeitos das mudanças, por exemplo o gerenciamento de versionamento do software em um processo iterativo e incremental, onde um defeito em produção pode surgir em uma versão anterios e propagada para a versão atual. Esta procedimento, muitas vezes, exige uma ferramenta que automatize a solução desse problema, que pode ser bem complexo.


### Gerenciamento da capacidade de reutilização:

- O reuso de softaware deve ser um bjetivo persistido por quem desenvolve o software. No paradigma estruturado, existem as bibliotecas de funções que permitem a reutilização do código em várias aplicações com possiblidades bem limitadas e com o advento do paradigma orientado a objetos, o reuso ficou mais sofisticados em função de macanismos, e.g, herança, que possibilitam uma melhor componentização do software.

### Preparo e produção de artefatos de software:

- Um processo de software encadeia uma série de atividades, sendo que estas atividades possuem métodos própios para a geração de artefatos que necessitam ser documentados, e.g., modelo de casos de uso.

# . 

![[Pasted image 20250826222242.png]]


---


# Resumo deste "dump":


Neste dump, podemos destcar a importância do software atualmente, bem como da complexidade no seu desenvolvimento. A aplicação da Engenharia de Software permite lidar com a referida complexidade, pois melhores práticas podem ser aplicadas de forma a gerar um produto “software” que atenda às necessidades para as quais foi projetado.

Destacamos que a Engenharia de Software é uma tecnologia em camadas, ou seja, com foco na qualidade, processo, métodos e ferramentas. Cabe enfatizar que a base da Engenharia de Software é a camada de processo, por isso foram descritas as principais atividades genéricas que devem compor um processo de software: comunicação, planejamento, modelagem, construção e entrega.
