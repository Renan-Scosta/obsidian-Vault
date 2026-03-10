
**Data:** 2025-10-21
**keyboards:** 
**links internos:** 
___

# O que é um padrão de projeto (design patterns)?

Padrões de projetos são soluções típicas para problemas comuns em projetos de software. Eles são como plantas de obra pré fabricadas que você pode customizar para resolver um problema de projeto recorrente em seu código.

Você não pode apenas encontrar um padrão e copiá-lo para dentro do seu programa, como você faz com funções e bibliotecas que encontra por aí. O padrão não é um pedaço de código específico, mas um conceito geral para resolver um problema em particular. Você pode seguir os detalhes do padrão e implementar uma solução que se adeque às realidades do seu próprio programa.


# Do que consiste um padrão?

A maioria dos padrões são descritos formalmente para que as pessoas possam reproduzi-los em diferentes contextos. Aqui estão algumas seções que são geralmente resentes em uma descrição de um padrão:

- O **Propósito** do padrão descreve brevemente o problema e a solução.

- A **Motivação** explica a fundo o problema e a solução que o padrão torna possivel.

- As **Estruturas** de classe mostram cada parte do padrão e como se relacionam.

- **Exemplos de código** em uma das linguagens de programação populares tornam mais fácil de compreender a ideia por trás do padrão.


# A história dos padrões

A ideia foi seguida por quatro autores: Erich Gamma, John Vlissides, Ralph Johnson, e Richard Helm. Em 1994, eles publicaram Padrões de Projeto — Soluções Reutilizáveis de Software Orientado a Objetos, no qual eles aplicaram o conceito de padrões de projeto para programação. O livro mostrava 23 padrões que resolviam vários problemas de projeto orientado a objetos e se tornou um best-seller rapidamente. Devido a seu longo título, as pessoas começaram a chamá-lo simplesmente de “o livro da Gangue dos Quatro (Gang of Four)” que logo foi simplificado para o “livro GoF”.

Desde então, dúzias de outros padrões orientados a objetos foram descobertos. A “abordagem por padrões” se tornou muito popular em outros campos de programação, então muitos desses padrões agora existem fora do projeto orientado a objetos também.



# Por que devo aprender padrões?


- Padrões de projetos são um kit de ferramentas para **soluções tentadas e testadas** para problemas comuns em projeto de software. mesmo que você nunca tenha encontrado esses problemas, saber sobre padrões é ainda muito útil porque eles ensinam como resolver vários problemas usando princípios de projeto orientado a objetos.

- Os padrões de projeto definem uma linguagem comum que você e seu colegas podem usar para se comunicar mais eficientemente. Você pode dizer, "Oh, é só usar Singleton para isso" e todo mundo vai entender a ideia por trás da sua sugestão. Não é preciso explicar o que é um singleton se você conhece o padrão e seu nome.


# Críticas dos padrões

Parece que apneas uma pessoa preguiçosa ainda não criticou os padrões de projeto. Vamos dar uma olhada aos argumentos mais típicos contra o uso de padrões.

1. **Gabiarras para um linguagem de programação fraca**:

	Geralmente a necessidade de padrões surge quando pessoas escolhem uma linguagem de programação ou um tecnologia que tem uma deficiência no nível de abstração. neste caso, Os padrões se tranformam em gambiarras que dão à linguagem superpoderes muitos necessários.
	
	por Exemplo, o padrão **Strategy** pode ser implementado com uma simples função anônima (lambda) na maioria das linguagens de programação moderna.

2. **Soluções ineficientes**:
	
	Os padrões tentam sistematizar abordagens que já são amplamente usadas. essa unificação é vista por muitos como um dogma e eles implementam os padrões "Direto ao ponto", sem adaptá-lo ao contexto de seus projetos.
	
	 ***Se tudo que você tem (sabe) é um martelo, tudo parece prego***.



# Classificação dos padrões

Padrões de projeto diferem por sua complexidade, nível de detalhes, e escala de aplicabilidade ao sistema inteiro sendo desenvolvido. 

Os padrões mais básicos e de baixo nível são comumente chamados ***idiomáticos***. Eles geralmente se aplicam apenas á uma única linguagem de programação.

Os padrões mais universais e de alto nível são os ***Padrões arquitetônicos***, desenvolvedores podem implementar esses padrões em praticamente em qualquer linguagem . Ao contrário de outros padrões, eles podem ser usados para fazer o projeto da arquitetura de toda uma aplicação.

Além disso, todos os padrões podem ser categorizados por seu *propósito*, ou intenção . Esse livro trata de três grupos principais de padrões: 

- Os **padrões criacionais** forneccem mecanismo de criação de objetos que aumentam a flexibilidade e a reutilização de código.

- Os **padrões estruturais** explicam como montar objetos e classes em estruturas maiores, enquanto ainda mantém as estruturas flexíveis e eficientes.

- Os **padrões comportamentais** cuidam da comunicação eficiente e da assinalação de responsabilidade entre objetos.








