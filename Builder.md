
**Data:** 2025-10-21
**keyboards:** 
**links internos:** 
___

# Builder 

O Builder é um padrão de projeto criacional que permite a você construir objetos complexos passo a passo. O padrão permite que você produza diferentes tipos e representações de um objeto usando o mesmo código de construção.

![[Pasted image 20251021184312.png]]



## Problema 

Imagine um objeto complexo que necessite de uma inicialização passo a passo trabalhosa de muitos campos e objetos agrupados. tal código de inicialização fica geralmente enterrado dentro de um construtor monstruoso com vários parâmetros. Ou pior: espalhado por todo o código cliente.


![[Pasted image 20251021203058.png]]


Por exemplo, vamos pensar sobre como criar um objeto `Casa`. Para construir uma casa simples, você precisa construir quatro paredes e um piso, instalar uma porta, encaixar um par de janelas, e construir um teto. Mas e se você quiser uma casa maior e mais iluminada, com um jardim e outras miudezas (como um sistema de aquecimento, encanamento, e fiação elétrica)?

A solução mais simples é estender a classe base Casa e criar um conjunto de subclasses para cobrir todas as combinações de parâmetros. Mas eventualmente você acabará com um número considerável de subclasses. Qualquer novo parâmetro, tal como o estilo do pórtico, irá forçá-lo a aumentar essa hierarquia cada vez mais.

Há outra abordagem que não envolve a propagação de subclasses. Você pode criar um construtor gigante diretamente na classe Casa base com todos os possíveis parâmetros que controlam o objeto casa. Embora essa abordagem realmente elimine a necessidade de subclasses, ela cria outro problema.


![[Pasted image 20251021203142.png]]

Na maioria dos casos a maioria dos parâmetros não será usada, tornando as chamadas do construtor em algo feio de se ver ([[Problema da lista de parâmetros longa]]). por exemplo, apenas algumas casas tem piscinas, entâo os parâmetros relacionados a piscinas serão inúteis nove em cada dez vezes.


# Solução 

O padrão Builder sugere que você extraia o código de construção do objeto para fora de sua própria classe e mova ele para objetos separados chamados *builders*.

![[Pasted image 20251021203901.png]]

O padrão organiza a construção de objetos em uma série de etapas. (construirParedes, construirPorta, etc) para criar um objeto você executa uma série de etapas em um objeto builder. A parte importante é que você não precisa chamar todas as etapas. Você chama apenas aquelas etapas que são necessárias para a produção de uma configuração específica de um objeto.

Algumas das etapas de construção podem necessitar de implementações diferentes quando você precisa construir várias representações do produto. Por exemplo, paredes de uma cabana podem ser construídas com madeira, mas paredes de um castelo devem ser construídas com pedra.

Nesse caso, você pode criar diferentes classes construturas que implementam as mesmas etapas de construção, mas de maneira diferente. Então você pode usar esses builders no processo de construção (i.e, um pedido ordenado de chamadas para as etapas de construção) para produzir diferentes tipos de objetos.


![[Pasted image 20251021215738.png]]


Por exemplo, imagine um builder que constrói tudo de madeira e vidro, um segundo builder que constrói tudo com pedra e ferro, e um terceiro que usa ouro e diamantes. Ao chamar o mesmo conjunto de etapas, você obtém uma casa normal do primeiro builder, um pequeno castelo do segundo, e um palácio do terceiro. Contudo, isso só vai funcionar se o código cliente que chama as etapas de construção é capaz de interagir com os builders usando uma interface comum.



# diretor

Voê pode ir além e extrair uma série de chamadas para as etapas que você usa para construir um produto em uma classe separada chamada **Diretor**. A classe diretor define a ordem na qual executar as etapas de construção, enquanto o builder provê a implementação dessas etapas


![[Pasted image 20251021220123.png]]



Ter uma classe diretor em seu programa não é estritamente necessário. Você sempre pode chamar as etapas de construção em uma ordem específica diretamente do código cliente. Contudo, a classe diretor pode ser um bom lugar para colocar várias rotinas de construção para que você possa reutilizá-las em qualquer lugar do seu programa.

Além disso, a classe diretor esconde completamente os detalhes da construção do produto do código cliente. O cliente só precisa associar um builder com um diretor, inicializar a construção com o diretor, e então obter o resultado do builder.


# Estrutura 


![[Pasted image 20251021220230.png]]


1. A interface **Builder** declara etapas de construção do produto que são comuns a todos tipos de builder.

2. **Builders Concretos** provém diferentes implementações das etapas de construção. Builders concretos podem produzir produtos que não seguem a interface comum.

3. **Produtos** são objetos resultantes. produtos construídos por diferentes builders não precisam pertencer a mesma interface ou hierarquia de classe

4. A classe **Diretor** define a ordem na qual as etapas de construção são chamadas, então você pode criar e reutilizar configurações específicas de produtos.

5. O **Cliente** deve associar um dos objetos builders com o diretor. Usualmente isso é feito apenas uma vez, através de parâmetros do construtor do diretor. O Diretor então usa aquele objeto builder para as futuras construções.  contudo, há uma abordagem alternativa para quando o cliente passa o objeto builder ao método de produção do diretor. Nesse caso, você pode usar um builder diferente a cada vez que você produzir alguma coisa com o diretor.


# Prós e contra


## Prós:

- Você pode construir objetos passo a passo, adiar as etapas de construção ou rodar etapas recursivamente.

-  Você pode reutilizar o mesmo código de construção quando construindo várias representações de produtos.

- Princípio de responsabilidade única. Você pode isolar um código de construção complexo da lógica de negócio do produto.


## Contra: 

-  A complexidade geral do código aumenta uma vez que o padrão exige criar múltiplas classes novas.





# [[Exercício Builder (Produção de carros)]] 