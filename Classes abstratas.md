
**Data:** 2025-03-13
**keyboards:** 
**links internos:** 
___

# Classes abstratas 

Uma classe abstrata é uma classe que serve de modelo para outras classes (subclasses). 
Ela sempre será uma superclasse genérica, e suas subclasses serão
mais especificas. Além disso, ela não pode ser instanciada e pode conter ou não métodos abstratos, podendo ser implementados nas classes descendentes.

- São classes que não podem ser instanciadas

- É uma forma de garantir herança total: somente subclasses não abstratas podem ser instanciadas, mas nunca a superclasse abstrata

### Exemplo

Suponha que em um negócio relacionado a banco, apenas contas poupança e contas para empresas são permitidas.
não existem conta comum.

Para garantir que contas comuns não possam ser instanciadas, basta acrescentarmos a palavra ==abstract== na declaração da classe.

![[Pasted image 20250313152915.png]]

Notação UML: itálico

![[Pasted image 20250313152955.png]]


# Questionamento

- Se a classe Account não pode ser instanciada, por que simplesmente não criar somente SavingsAccount e BusinessAccount?

- Resposta: 
	- **Reuso**
	- **Polimorfismo**: a superclasse genérica nos permite tratar de forma fácil e uniforme todos os tipos de conta, inclusive com polimorfismo se for o caso. Por exemplo, você pode colocar todos tipos de contas em uma mesma coleção.


- **Demo: Suponha que você queira**:
	- Totalizar o saldo de todas as contas.
	- Depositar 10.00 em todas as contas.