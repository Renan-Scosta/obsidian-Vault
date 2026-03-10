
**Data:** 2025-04-08
**keyboards:** 
**links internos:** 
___

# Coleções - Collections

É um conjunto bem definido de interfaces e classes para representar e tratar grupos de dados como uma única unidade, que pode ser chamada de coleção, ou collection. A Collections contém os seguintes elementos:

![[Pasted image 20250415092007.png]]



___
### Interfaces:

- Tipos abstratos que representam as coleções. Permitem que coleções sejam manipuladas tendo como base o conceito "Programar para interfaces e não para implementações", desde que o acesso aos objetos se restrinja apenas ao uso de métodos definidos nas interfaces.

#### [[Iterator em Java]]

- está no topo da hierarquia e possibilita percorrer uma coleção e remover seus elementos;
#### Collection:

- Não existe implementação direta dessas interface, mais ela define as operações básicas para as coleções, como adicionar, remover, esvaziar, etc.; 

##### [[List - listas]]

- Define uma coleção ordenada, podendo conter elementos duplicados. Em geral, o usuário tem controle total sobre a posição onde cada é inserido e pode recuperá-los através de seus índices. Prefira esta interface quando precisar de acesso aleatório, através do índice do elemento.

##### [[Queue - Filas]]

- um tipo de coleção para mantes uma lista de prioridades, onde a ordem dos seus elementos, definida pela implementação de **Comparable** ou  **Comparator**, determina essa prioridade. Com a interface fila, pode-se criar filas e pilhas.

##### [[Map]]

- mapeia chaves para valores. cada elemento tem na verdade dois objetos: uma chave e um valor. Valores podem ser duplicados, mas chaves não. ***SortedMap*** é uma interface que estende ***Map***, e permite classificação ascendente das chaves. Uma aplicação dessa interface é a classes **Properties**, que é usada para persistir propriedades/configurações de um sistema, por exemplo


#### [[Set]]:

- Interface que define uma coleção que não permite elementos duplicados. A interface **SortedMap**, que estende Map, possibilita a classificação natural dos elementos, tal como a ordem alfabética;


___


### Implementações:

- São as implementações concretas das interfaces.

### Algoritmos:

- São os métodos que realizam as operações sobre os objetos das coleções tais como busca e ordenações.


