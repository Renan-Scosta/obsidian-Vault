
**Data:** 2025-04-15
**keyboards:** 
**links internos:** 
___

# Implementações - Set


## HashSet:

**O acesso aos dados é mais rápido que em um TreeSet, mas nada garante que os dados estarão ordenados. Escolha este conjunto quando a solução exigir elementos únicos e a ordem não for importante**.

### Exemplo de aplicação:

**Poderíamos usar esta implementação  para criar um catálogo pessoal das canções da nossa discografia**. (não deixa adicionar uma música já existente na playlist)


## TreeSet:

**Os dados são classificados, mas o acesso é mais lento que um HashSet. Se a necessidade for um conjunto com elementos não duplicados e acesso em ordem natural, prefira o TreeSet. É recomendado utilizar esta coleção para as mesmas aplicações de HashSet, com a vantagem dos objetos estarem em ordem natural**.


## LinkedHashSet:

**É derivada de HashSet, mas mantém uma lista duplamente ligada através de seus itens. Seus elementos são iterados na ordem em que forem inseridos. Opcionalmente é possivel criar um LinkedHashSet que seja percorrido na ordem em que os elementos foram acessados na ultima iteração**.

### Exemplo de aplicação:

Poderíamos usar esta implementação para registrar a chegada dos corredores de uma maratona.



# Diferença entre os Set´s:


### HashSet: 

O HashSet é o mais rápido de todos e seus elementos não são ordenados e não importa o quanto você adicione, remova, retire, o tempo de execução será sempre o mesmo. 

Por outro lado, a garantia de continuidade na ordem dos elementos inseridos é zero, ou seja, esse tipo de estrutura é indicada se você precisa apenas garantir a alta performance sem se importar com a ordem com que os elementos estão ordenados.


### TreeSet:

Sua principal Características é que ele é o único Set que implementa a interface SortedSet em vez de Set diretamente, mas que de qualquer forma SortedSet implementa Set, assim continuamos tendo os mesmos métodos no TreeSet. Pelo fato de ele implementar o SortedSet, ele possui elementos ordenados automaticamente, ou seja, independentemente da ordem que você inserir os elementos, eles serão ordenados. Mas isso tem um custo, a complexidade para os métodos add, remove e contains são bem maiores que a do HashSet, são elas O(log(n)), não é bem um complexidade exponencial, mas é bem maior que O(1) que tem seu tempo inalterado.

### LinkedHashSet:

É um meio termo entre HashSet e TreeSet, ou seja, ela nos proporciona um pouco da performance do HashSet e um pouco do poder de ordenação do TreeSet. O LinkedHashSet faz uso também do Hashtable com LinkedList, ou seja, temos aqui a seguinte situação: Os elementos continuam na ordem que são inseridos, diferente do HashSet que "embaralha" tudo.



# Resumo Set

- É uma interface genérica
- Representa um conjunto de elementos (similar ao da algebra)
- Não admite repetições
- Elementos não possuem posições 
- Acesso, inserção e remoção de elementos são rápidos
- Oferece operações eficientes de conjuntos: interseção, união, diferença.
- Principais implementações:
	- **HashSet** - mais rápidos (operações O(1) em tabela hash) e não ordenado
	- **TreeSet** - mais lento (operações O(log(n)) em árvore rubro-negra)  e ordenado pelo CompareTo do objeto (ou comparator)
	- **LinkedHashSet** - velocidade intermediária e elementos na ordem em que são adicionados.




# Como as coleções Hash testam igualdade?

- Se HashCode e equals estiverem implementados:
	- primeiro HashCode. se der igual, use equals pra confirmar.

	- Lembre-se: String, Integer, Double etc. já possuem equals e hashcode.

- Se HashCode e equals não estiverem implementados:
	- compara as referências (ponteiros) dos objetos. 




# como TreeSet compara os elementos?


#### Recordando implementações:

- **HashSet** - mais rápidos (operações O(1) em tabela hash) e não ordenado
- **TreeSet** - mais lento (operações O(log(n)) em árvore rubro-negra)  e ordenado pelo CompareTo do objeto (ou comparator)
- **LinkedHashSet** - velocidade intermediária e elementos na ordem em que são adicionados.


#### Exemplo:


**Classe Product**:
![[Pasted image 20251007111130.png]]


**Program**:

![[Pasted image 20251007111232.png]]


