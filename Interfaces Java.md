           
**Data:** 2025-04-25
**keyboards:** 
**links internos:** 
___

# O que são?

Pense nelas como um contrato ou um conjunto de regras que uma classe se compromete a seguir. Em vez de dizer _como_ algo deve ser feito, uma interface diz _o que_ precisa ser feito.

Imagine um controle remoto universal para diferentes aparelhos eletrônicos, como uma TV, um DVD player e um sistema de som. Cada aparelho tem suas próprias maneiras de executar certas ações (a TV muda de canal de um jeito, o DVD player de outro), mas o controle remoto oferece uma interface comum com botões como "Ligar/Desligar", "Aumentar Volume" e "Diminuir Volume". Cada aparelho "implementa" essa interface, fornecendo sua própria maneira de realizar essas ações quando os botões são pressionados.

Em Java, uma interface é definida usando a palavra-chave `interface`, e ela pode conter apenas declarações de métodos abstratos (métodos sem corpo) e constantes (campos `static` e `final`).


# Pontos chaves sobre Interfaces:

- **Contratos, não implementações**: Interfaces definem um contrato que as classes devem seguir. Elas especificam quais métodos uma classe deve implementar, mas não como esses métodos devem ser implementados.
___
- **Abstração**: Interfaces ajudam a alcançar a abstração, separando a especificação do comportamento de sua implementação concreta. Isso permite que diferentes classes implementem a mesma interface de maneiras distintas.
___
- **Múltipla herança de tipos**: Uma classe pode implementar múltiplas interfaces. Isso permite que uma classe adote múltiplos "Tipos" ou "Papéis". Por exemplo, uma classe carro pode implementar interfaces como movível, parável e Barulhento.
___
- **Acoplamento fraco**: O uso de interfaces promove o acoplamento fraco entra as classes. As classes que dependem de uma interface não precisam conhecer os detalhes de implementação das classes concretas que a implementam. Isso torna o código mais flexível e fácil de manter.



# Código-exemplo:

Uma implementação simples de um interface "carro"

![[Pasted image 20250425141610.png]]


Onde duas classes implementam essa interface ("carro de passeio" e "Caminhão"):

![[Pasted image 20250425141739.png]]


![[Pasted image 20250425141807.png]]


---

# Inversão de controle, injecão de dependência:


- Acoplamento forte.
- A classe Rental service conhece a dependência concreta.
- Se a classe concreta mudar, é preciso mudar a classe RentalService

![[Pasted image 20250918103403.png]]



- Acoplamento fraco.
- A classe RentalService não Conhece a dependência concreta
- Se a classe concreta mudar, a classe RentalService não muda.

![[Pasted image 20250918103556.png]]



# Injeção de dependência por meio de construtor:

![[Pasted image 20250918110108.png]]


# Inversão de controle:


- **Inversão de controle**:
Padrão de desenvolvimento que consiste em retirar da classe a responsabilidade de instanciar suas dependências.

- **Injeção de dependência**: 
É uma forma de realizar a inversão de controle: um componente externo instância a dependência, que é então injetada no objeto "Pai". pode ser implementada de várias formas:

- Construtor
- Classe de instanciação (builder/factory)
- Conteiner / framwork


# Herdar vs Comprir contrato:


**Aspectos comum entre herança e interfaces**:

- Relação é-um
- Generalização/especialização
- Polimorfismo



![[Pasted image 20250918111448.png]]


**Diferença fundamental**:

- Herança => reuso
- Interface => contrato a ser cumprido



E se eu precisar implementar Shape como interface, porém também quiser definir uma estrutura comum reutilizável para todas figuras?


fica desse jeito:

![[Pasted image 20250918111730.png]]


Outro exemplo: 

![[Pasted image 20250918111815.png]]


# Herança múltipla e o problema do diamante 


![[Pasted image 20250919110704.png]]


A herença múltipla pode gerar o problema do diamante: uma ambiguidade causada pela existência do mesmo método em mais de uma superclasse.

Herança múltipla não é permitida na maioria das linguagens!


**Porém, uma classe pode implementar mais de uma interface**.

![[Pasted image 20250919110954.png]]


**ATENÇÃO!!!!**

Isto acima NÃO é uma herança múltipla, pois NÃO HÁ REUSO na relação entre entre ComboDevice e as interfaces Scanner e Printer

ComboDevice não herda, mas sim implementa as interfaces (Cumpre contrato).


# Interface Comparable

Em Java, a interface ==Comparable< T >== é uma interface genérica da biblioteca padrão (java.lang) usada para definir uua ordem natural entre objetos de uma classe.

Ela serve para que objetos de uma mesma classe possam ser comparados entre si, geralmente para ordenação em estruturas de dados (como List, árvores ou Arrays).

![[Pasted image 20250923082323.png]]

- O método ==compareTo(T o)== precisa ser implementado pela classe 
- O retorno deve ser: 
	- **Negativo** -> se o objeto atual for menor que ==o==.
	- **Zero** -> se forem iguais.
	- **Positivos** -> se o objeto atual for maior que ==o==.

![[Pasted image 20250923082640.png]]


# Default Methods (defender methods)


- A partir do Java 8, interfaces podem conter métodos concretos.

- A intenção básica é prover implementação padrão para métodos, de modo a evitar:
	- 1) Repetição de implementação em todo a classe que implemente a interface
	- 2) a necessidade de ser criar classes abstratas para prover reuso de implementação


- Outras vantagens: 
	- Manter a retrocompatibilidade com sistemas existentes
	- permitir que "Interfaces funcionais" (que devem conter apenas um método) possam prover outras operações padrão reutilizáveis.


**Exemplos**:

![[Pasted image 20250923100055.png]]


![[Pasted image 20250923100107.png]]

![[Pasted image 20250923100117.png]]

![[Pasted image 20250923100137.png]]


**Considerações Importantes**:

- Sim: agora as interfaces podem prover reuso
- Sim: agora temos uma forma de herança múltipla
	- Mas o compilador reclama se houver mais de um método com a mesma assinatura, obrigando a sobrescrve-lo
- Interfaces ainda são bem diferentes de classes abstratas. Interfaces não possuem recursos tais como construtores e atributos.




# Significado de "DAO" em interfaces:


**DAO** é a sigla para **Data Acess Object** (Objeto de Acesso a Dados).
em resumo, é um padrão de projeto (Design Pattern) que isola a lógica de acesso a dados do resto da aplicação. pense nele como um gerente do banco de dados para um tiupo específico de informação.



## Para o que serve? 

Imagine que sua aplicação precisa salvar, buscar, atualizar e deletar clientes no banco de dados.

Sem o padrão DAO, você provavelmente escreveria o código SQL diretamente nas suas telas, regras de negócio, etc. isso gera um grande problema:

- **Acoplamento**: Se você mudar de banco de dados ( de MySQL para PostgreSQL, por exemplo), terá que "Caçar" e reescrever o código SQL em vários lugares da sua aplicação
- **Repetição de código**: Você acabaria escrevendo os mesmo comando ==SELECT==, ==INSERT==, ==UPDATE== várias vezes.
- **Dificuldade de Testes**: testar sua ;ógica de negócio se torna difícil, pois ele depende diratamente de uma conexão ativa com o banco de dados.

**Com o padrão DAO**, você cira uma camada de abstração. A sua lógica de negócio não fala mais com o banco de dados, ela fala com o DAO.

- **Analogia:** Pense no DAO como um **bibliotecário**. Você (sua lógica de negócio) não entra no acervo gigante para procurar um livro (um dado). Você vai até o balcão e pede ao bibliotecário (o DAO): "Por favor, me traga o livro sobre Clientes com o ID 123". O bibliotecário sabe exatamente em qual prateleira (tabela do banco de dados) procurar e como pegar o livro (executar o SQL).  

## Principais reponsabilidades de um DAO (CRUD)

Um DAO geralmente possui métodos para as quatros operações básicas de persistência, conhecidadas como **CRUD**:

- **Create**: Salvar um novo objeto no banco. Ex: ==void salvar(Cliente cliente)==.
- **Read**: Buscar um ou mais objetos. Ex: ==void buscarPorId(int id);== ou ==List< Cliente > listarTodos();
- **Update**: Atualizar/Modificar um objeto existente. Ex: ==void atualizar(Cliente cliente);
- **Delete**: Remover um objeto. Ex: ==void excluir(int id);==



## Vantagens de usar o Padrão DAO:

- **Separação de Responsabilidades**: A lógica de negócio (o que fazer com o cliente) fica separada da lógica de persistência (como salvar o cliente).
- **Flexibilidade**: Se amanhã você decidir usar um banco de dados Oracle, basta criar uma nova classe `ClienteDAOOracle` que implementa `IClienteDAO` e trocar a implementação, sem mexer no resto do sistema.
- **Facilita Testes**: Você pode criar um "DAO de mentira" (Mock) para testar sua aplicação sem precisar de um banco de dados real.
- **Código mais Limpo e Organizado**: Centraliza todo o código de acesso a dados em um único lugar, facilitando a manutenção.

