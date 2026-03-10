
**Data:** 2026-01-08
**keyboards:** 
**links internos:** 
___

No contexto do **JDBC (Java Database Connectivity)**, a ==Statement== e o ==ResultSet== são duas das interfaces mais fundamentais. Elas trabalham em conjunto para enviar comandos SQL para o banco de dados e processar as respostas.

Imagine o seguinte fluxo: Você precisa de uma **Conexão** (estrada), um **Statement** (veículo) para levar seu pedido, e um **ResultSet** (pacote) que traz a resposta de volta.


## API Connection

A interface `Connection` (`java.sql.Connection`) é o ponto de partida de qualquer operação com banco de dados em Java. Ele representa uuma **sessão ativa** estabelecida entre a sua aplicação Java e o Banco de dados.



## API Statement

A interface Statement (java.sql.Statement) atua como o mensageiro. É o objeto responsável por enviar comando SQL estáticos para o banco de dados.

Você cria um objeto ==statement== a parti de uma **conexão aberta**.


**Principais características**: 

- **Execução de consultas**: Usada para rodar comandos como ==SELECT==, ==INSERT==, ==UPDATE==, e ==DELETE==.

- **Não parametrizadas**: Geralmente usada para queries onde valores são fixos ou concatenados diretamente na String (o que exige cuidado na questão de segurança).

**Métodos essenciais**:

- ==executeQuery(String sql)==: Usa-se para **consultas** (SELECT). retorna um objeto **ResultSet**.

- ==executeUpdate(String sql)==: Usa-se para **alterações** (INSERT, UPDATE, DELETE). Retorna um número inteiro indicando quantas linhas foram afetadas. 


***Nota de Segurança***:
Embora o ==Statement== seja a base, em aplicaações reais recomenda-se fortemente o uso de ==PreparedStatement==. o Statement simples é vulnerável a ataques de SQL injection porque concatena strings diretamente. O PreparedStatement **pré-compila** o SQL e trata os parâmetros de forma segura.



## API ResultSet

A interface ==ResultSet== (java.sql.ResultSet) representa o **resultado** da sua consulta. Pense nele como uma tabela de dados (planilha) virtual que foi retornada pelo banco de dados após a execução de um ==Statement==.


#### Como funciona: 

- **O cursor**: O ResultSet mantém um "cursor" (ponteiro) que aponta para a linha atual de dados.

- **Posição inicial**: Inicialmente, o cursor está posicionado **antes** da primeira linha.

- **Navegação**: Você deve mover o cursor para próxima linha para ler os dados.


#### Métodos essenciais

- `next()`: Move o cursor para a próxima linha. Retorna **true** se houver uma linha válida e **false** se não houver mais dados. É usado frequentemente dentro de um loop **while**.

- `getString()`, `getInt()`, `getDate()`: Métodos "getters" usados para extraair o valor de uma coluna na linha atual. Você pode pedir pelo nome da coluna ou pelo índice. (começando em 1).

