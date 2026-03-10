
**Data:** 2026-03-05
**keyboards:** 
**links internos:** 
___

# O que são os repositories?

A camada de repositories é a responsável direta por "conversar" com o banco de dados.

O Repository é uma interface que serve como um mediador entre a sua aplicação (o código em java) e o banco de dados (as tabelas).

Quando você estende `JpaRepository< User, Long >`, o Spring Data JPA gera automaticamente para você todos os métodos básicos de manipulação de dados, como:

- `save()`: Para inserir ou atualizar.

- `findById()`: Para buscar por id. 

- `findAll()`: Para listar tudo.

- `deletedById()`: Para excluir.


**O papel principal deles**: Abstrair a complexidade. Você não precisa escrever comandos SQL para as operações básicas; você apenas chama um método Java e o Spring cuida da tradução para o banco de dados.

---

# JQPL vs SQL puro


#### 1. JPQL (Java Persistence Query Language)

O JPQL é a linguagem de consula do JPA. A grande diferença é que ela **foca nas classes Java (Entidades)** e não nas tabelas dos bancos


***Exemplo no meu código***:

![[image-22.png]]

Nota que você usa `Task` (o nome da classe) e `t.user.id = :id` (o atributo dentro da sua classe).

**Vantagem**: Se você mudar o banco de mariaDB para PostgreSQL, o código continua funcionando, pois ele é independente do banco de dados. 


#### 2. SQL Puro (Native Query)

É o comando enviado exatamente como o seu banco de dados (MariaDB) entende.

- **Exemplo no seu código:** `SELECT * FROM tasks t WHERE t.user_id = :id`

- **Como funciona:** Você usa `tasks` (o nome da tabela no banco) e `user_id` (o nome real da coluna).
 
- **Vantagem:** Útil para consultas muito complexas ou funções específicas que só existem em um determinado banco de dados.


