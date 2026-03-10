
**Data:** 2025-10-09
**keyboards:** 
**links internos:** 
___

# 🗄️ O que é um Banco de dados ralacional?

Em essência, um banco de dados relacional é um tipo de banco de dados que organiza dados em tabelas.
pense nele como uma coleção de planilhas (como o excel), onde cada planilha é uma tabela, e as planilhas podem ser vinculadas umas às outras.

A "Parte" relacional advém do fato de que os dados em diferentes tabelas estão estão **relacionados**, e esses relacionamentos são definidos explicitamente. Essa estrutura facilita o armazenamento, o gerenciamento e a consulta de dados de forma eficiente.


## Os blocos de construção

Todo banco de dados relacional é construído com base em alguns conceitos-chave:

- **Tabelas (ou Relações)**: Os dados sãoarmazenados em tabelas. Cada tabela representa um tipo específico de entidade, como ==Customers==, ==Products==, ou ==Orders==.
- **Linhas (ou Registros/Tuplas)**: Cada linha em uma tabela representa uma única instância daquela entidade. Por exemplo, uma linha na ==Customer== tabela representaria um cliente específico.
- **Colunas (ou Atributos/Campos)**: Cada caluna em uma tabela representa um atributo específico daquela entidade. Por exemplo, a ==Customers== tabela pode ter colunas como ==CustomerID==, ==FirstName==, ==LastName== e ==Email==.
- **Chaves**: Chaves são colunas especiais usadas para impor regras e criar relacionamentos entre tabelas.
	- **Chave primária ( ==PRIMARY KEY== )**: Esta é uma coluna (ou conjunto de colunas) que identifica exclusivamente cada linha em uma tabela. A ==CustomerID== é um exemplo perfeito de chave primária, pois não há dois clientes com o mesmo ID.
	- **Chave Estrangeira ( ==FOREIGN KEY== )**: Esta é uma coluna em uma tabela que faz referência à coluna ==PRIMARY KEY== em outra tabela. É assim que você cria um **vínculo** ou **Relacionamento** entre tabelas.



## O que o torna "Relacional"? A magia das chaves

Vamos usar um exemplo simples para ver como a "relação" funciona. Imagine que você tem duas tabelas: `Customers`e `Orders`.

**`Customers`Tabela** | **ID do Cliente (PK)** | Nome | Sobrenome | | :------------------ | :-------- | :------- | | 101 | John | Doe | | 102 | Jane | Smith |

**`Orders`Tabela** | **OrderID (PK)** | **CustomerID (FK)** | OrderDate | Valor | | :--------------- | :------------------ | :--------- | :----- | | 5001 | 102 | 2025-10-08 | $55,00 | | 5002 | 101 | 2025-10-09 | $120,00| | 5003 | 102 | 2025-10-09 | $25,00 |


Na ==Orders== tabela, a ==CustomersID== clonua é uma **Chave estrangeira**. Ela não armazena o nome do cliente diretamente. em vez disso, ela "Aponta" para a linha na ==Custmers== tabela com essa chave ==CustomerID==.

Dessa forma, você pode facilmente consultar qual cliente fez qual pedido sem duplicar as informações do cliente na ==Orders== tabela. Isso evita inconsistências de dados e economiza espaço.


## A linguagem [[SQL]]

Para interagir com um banco de dados relacional (para criar, ler, atualizar ou excluir dados), você usa uma linguagem padrão chamada **SQL ( Structured Query Language )**.

Por exemplo, para obter uma lista de todos os pedidos feitos por Jane Smith, você escreveria uma consulta como esse: 

```
SELECT
	o.OrderID,
	o.OrderDate,
	o.Amount
FROM
	Customers c
JOIN
	Orders o ON c.CustomersID = o.CustomersID		
WHERE
	c.FirstName = 'Jane' AND c.LastName = 'Smith'
```


