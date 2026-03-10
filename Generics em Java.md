 
**Data:** 2025-09-23
**keyboards:** 
**links internos:** 
___

# Generics:

- Generics permitem que classes, interfaces e métodos possam ser parametrizados por tipo. Seus benefícios são:
	- Reuso
	- Type Safety
	- Performance

- Uso comum: **Coleções**.

![[Pasted image 20250923121342.png]]



### Problemas motivador 1 (reuso)

Deseja-se fazer um programa que leia uma quantidade N, e depois N números inteiros. Ao final, imprima esses números de forma organizada conforme exemplo. em Seguida, informar qual foi o primeiro valor informado.

![[Pasted image 20250923121758.png]]


### Problema motivador 2 (Type safety e performance)

Deseja-se fazer um programa que leia uma qunatidade N, e depois N nomes de pessoas. Ao final, imprima esses números de forma organizada conforme exemplo.
Em seguida, informar qual foi o primeiro valor informado.



### Solução com generics 

Deseja-se fazer um programa que leia qunatidade N, e depois N números inteiros. Ao final, imprima esses números de forma organizada conforme exemplo. Em seguida, informar qual foi o valor informado.

![[Pasted image 20250923185007.png]]


### Resumo: 

Generics permitem reutilização de código + segurança de tipos em tempo de compilação, evitando casts desnecessários e erros em runtime.


# Genericos delimitados (bounded generics)


Quando você cria um tipo genérico (< T >), por padrão ele pode ser qualquer tipo.
mas muitas vezes você quer restringir esses tipos a uma hierarquia ou interface.

pra isso usamos **delimitação (bounds)**, com ==extends== e ==super== 


### 1. Upper bounded (extends)

Significa: "T pode ser esse tipo ou quaquer subtipo dele".

exemplo:

![[Pasted image 20250923194314.png]]

uso:

![[Pasted image 20250923194337.png]]




### 2. Lower bounded (super)

Significa: "T pode ser esse tipo ou qualquer supertipo dele"
esse é usado mais em wildcards (? super tipo) do que em declaração de classe.

Exemplo: 

![[Pasted image 20250923194723.png]]

Uso:

![[Pasted image 20250923194751.png]]

==? super Integer== aceita ==Integer==, ==Number== e ==Object== 



### 3. Multiple bounds (múltiplas restrições)

voce pode combinar restrições


exemplo: 

![[Pasted image 20250923195230.png]]

Uso: 

![[Pasted image 20250923195248.png]]



### 4. Resumo rápido:

- ==T extends Classe== -> limita a subclasse de uma classe
- ==T extends Interface== -> limita a tipos que implementam a interface
- ==? extends Tipo== -> aceita subtipos (bom pra leitura)
- ==? super tipo== -> aceita supertipos (bom pra escrita)
- pode combinar com ==&== -> ==T extends Classe & Interface1 & Interface2== 



# tipos curinga (wildcard types)


### Generics são invariantes 

List< Object > não é o supertipo de qualquer tipo de lista:

![[Pasted image 20250923202411.png]]

**Apesar de Integer ser um Object, List de Integer não é um List de Object!!!!**

O supertipo de qualquer tipo de lista é List< ? >. Este é um tipo curinga:

![[Pasted image 20250923202507.png]]

##### com tipos curinga podemos fazer métodos que recebem um genérico de Qualquer tipo

![[Pasted image 20250923204202.png]]


##### Porém não é possivel adicionar dados a uma coleção de tipo coringa.

![[Pasted image 20250923204517.png]]

O compilador não sabe qual é o tipo específico do qual a lista foi instanciada.



# Curingas delimitados (bounded wildcards)


#### Problema 1

Vamos fazer um método para retornar a soma das áreas de uma lista

![[Pasted image 20250926113537.png]]

![[Pasted image 20250926113550.png]]


