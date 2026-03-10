
**Data:** 2025-11-05
**keyboards:** 
**links internos:** 
___

# Intenção oficial

Fornecer uma interface para a criação de famílias de objetos relacionados ou interdependentes sem especificar suas classes concretas.


- É um padrão de criação, portanto lida com a criação de objetos.
- É uma fabrica assim como o factory method e geralmente é composto por múltiplos Factory methods
- Visa agrupar famílias de produtos compatíveis criando uma fábrica concreta por grupo de objetos compatíveis
- Separa o código que cria do código que usa os objetos ([[Single responsability principle]])
- permite fácil implementação de novas famílias de objetos (OCP).
- Toda programação fica focada nas interfaces e não em implementações.

![[Pasted image 20251105103437.png]]



# Aplicabilidade

**Use o Abstract factory quando seu código precisa trabalhar com diversas famílias de produtos relacionados, mas que você não quer depender de classes concretas daqueles produtos -eles podem ser desconhecidos de antemão ou você simplesmente quer permitir uma futura escalabilidade**.

O abstract factory fornece a você uma interface para a criação de objetos de cada classe das famílias de produtos. Desde que seu código crie objetos a partir dessa interface, você não precisará se preocupar em criar uma variante errada de um produto que não coincida com produtos ja criados por sua aplicação.


Considere implementar o Abstract factory quando você tem uma classe com um conjunto de métodos fábrica que desfoquem sua responsabilidade principal.

em um programa bem desenvolvido *cada classe é responsável por apenas uma coisa*. Quando uma classe lida com múltiplos tipos de produto, pode valer a pena extrair seus métodos fábrica em uma classe fábrica solitária ou um implementação plena do Abstract Factory.


# Consequências

### Bom:

- Os produtos sempre serão compatíveis entre si
- Aplicação clara do Open/Closed principle, é fácil adicionar novas fábricas e produtos.
- aplicação clara do [[Single responsibility principle]], o código que cria está separado do código que usa os objetos.

## ruim:

- Muitas classes e maior complexidade será introduzida no código.



# Como implementar 


1. Mapeie uma matriz de tipos de produtos distintos versus as variantes desses produtos.

2. Declare interfaces de produto abstratas para todos os tipos de produto. Então, faça todas as classes concretas de produtos implementar essas interfaces.

3. Declare a interface da fábrica abstrata com um conjunto de métodos de criação para todos os produtos abstratos.

4. Implemente um conjunto de classes fábricas concretas, uma para cada variante de produto. 

5. crie um código de inicialização da fábrica em algum lugar da aplicação. Ele deve instanciar uma das classes fábrica concretas, dependendo da configuração da aplicação ou do ambiante atual. Passe esse objeto fábrica para todas as classes que constroem produtos.

6. Escaneie o código e encontre todas as chamadas diretas para construtores de produtos. substitua-as por chamadas para o método de criação apropriado no objeto fábrica. 



# [[código exemplo abstract factory]]
