
**Data:** 2025-10-21
**keyboards:** 
**links internos:** 
___


# Singleton

O **Singleton** (conhecido também como: carta única) é um padrão de projeto criacional que permite você garantir que uma classe tenha apenas um instância, enquanto provê um ponto de acesso global para essa instância.

![[Pasted image 20251021085942.png]]


## Problema

O padrão Singleton resolve dois problemas de uma só vez, violando o *pincípio de responsabilidade única*:

1) **Garantir que uma classe tenha apenas uma única instância**. por que alguém iriar querer controlar quantas instâncias uma classe tem? A razão mais comum para isso é pra controlar o acesso a algum recurso compartilhado - por exemplo, uma base de dados ou arquivo.

	Funciona assim: imagine que você criou um objeto, mas depois de um tempo você decidiiu criar um novo. Ao invés de receber um objeto fresco, você obterá um que já foi criado.
	
	Observe que esse comportamento é impossível implementar com um construtor regular uma que uma chamada do construtor deve sempre retornar um novo objeto por design.


	![[Pasted image 20251021090602.png]]


2) **Fornece um ponto de acesso global para aquela instância**. Se lembra daquelas variáveis globais que você usou para guardar alguns objetos essenciais? Emborar sejam muito úteis, elas também são muito inseguras uma vez que qualquer código pode potencialmente subscrever os conteúdos daquelas variávei e quebrar a aplicação.

	Assim como um variável global, o padrão singleton permite que você acesse algum objeto de qualquer lugar do programa. contudo, ele também protege aquela instância de ser sobrescrita por outro código.



## Solução

Todas as implementação de Singleton tem esses dois passos em comum:

- Fazer o construtor padrão privado, para prevenir que outros objetos usem o operador new com a classe singleton.

- Criar um método estático de criação que age como um construtor. Esse método chama o construtor privado por debaixo dos panos para criar um objeto e o salva em um campo estático. Todas as chamadas seguintes para esse método retornam o objeto em cache.

Se o seu código tem acesso à classe singleton, então ele será capaz de chamar o método estático da singleton. Então sempre que aquele método é chamado, o mesmo objeto é retornado.



# Analogia com o mundo Real

O governo é um excelente exemplo de um padrão Singleton. Um país pode ter apenas um governo oficial. Independentemente das identidades pessoais dos indivíduos que formam governos, o título, “O Governo de X”, é um ponto de acesso global que identifica o grupo de pessoas no comando.



# Estrutura


![[Pasted image 20251021092322.png]]



1. A classe **Singleton** declara o método estático ==getInstance== que retorna a mesma instância de sua prórpia classe.

	O construtor da Singleton deve ser escondido no código cliente. Chamando o método ==getInstance== deve ser o único modo de obter o objeto singleton.




# Aplicabilidade

**Utilize o padrão Singleton quando uma classe em seu programa deve ter apenas uma instância disponível para todos seus clientes; por exemplo, um objeto de base de dados único compartilhado por diferentes partes do programa**. 

O padrão Singleton desabilita todos os outros meios de criar objetos de uma classe exceto pelo método especial de criação. Esse método tanto cria um novo objeto ou retorna um objeto existente se ele já tenha sido criado.


**Utilize o padrão Singleton quando você precisa de um controle mais estrito sobre as variáveis globais**.

Ao contrário das variáveis globais, o padrão Singleton garante que há apenas uma instância de uma classe. Nada, a não ser a própria classe singleton, pode substituir a instância salva em cache.

Observe que você sempre pode ajustar essa limitação e permitir a criação de qualquer número de instâncias singleton. O único pedaço de código que requer mudanças é o corpo do método ==getInstance==.


# Prós e constras


## Pró

- Você pode ter certeza que uma classe só terá uma única instância.
- Você ganha um ponto de acesso global para aquela instância
- O objeto singleton é inicializado somente qunado for pedido pela primeira vez.


## Contra

- Viola o *príncipio de responsabilidade única*. O padrão resolve dois problemas de uma vez
- O padrão singleton pode mascarar um design ruim, por exemplo, quando os componentes do programa sabem muito sobre cada um,
- O padrão requer tratamento especial em um ambiente multithreaded para que múltiplas threads não possam criar um objeto singleton várias vezes.
- Pode ser difícil realizar testes unitários do código cliente do Singleton porque muitos frameworks de teste dependem de herança quando produzem objetos simulados. Já que o construtor da classe singleton é privado e sobrescrever métodos estáticos é impossível na maioria das linguagem, você terá que pensar em uma maneira criativa de simular o singleton. Ou apenas não escreva os testes. Ou não use o padrão Singleton.



