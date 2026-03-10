
**Data:** 2025-10-10
**keyboards:** 
**links internos:** 
___

# Apresentando SQL

SQL é uma Linguagem de Consulta Estruturada (**Structured Query Language**), Ela é a espinha dorsal da gestão e manipulação de dados em praticamente todos os sistemas de informação modernos. Essencial para desenvolvedores, analista de dados, administradores de banco de dadados. O SQL permite uma comunicação fluida com bancos de dados relacionais, o modelo predominante para armazenamento de dados estruturados.

Originalmente desenvolvida pela IBM no inicio dos anos 1970, e depois pela ANSI, a SQL se consolidou como a linguagem universal para interagir com Sistemas de Gerenciamento de Bancos de Dados (SGBDs) como MySQL, PostgreSQL, Microsoft SQL, Oracle, entre outros. Sua natureza declarativa, onde o usuário especifica o que deseja, e não como obter, simplifica a recuperação e manipulação de dados complexos.


# A Arquitetura do SQL: os subconjnuntos da Linguagem

Para organizar suas diversas funcionalidades, a SQL é dividida em subconjuntos de comandos, cada um com um propósito especifico. Essa divisão estrutural facilita o aprendizado e a compreensão da linguagem.


**[[DDL (Data Definition Language) A linguagem de definição de dados]]**:

A DDL é o conjunto de comandos responsável por criar, alterar e excluir a estrutura dos objetos do banco de dados. É com a DDL que se define o "esqueleto" onde os dados serão armazenados.

---
**[[DML (Data Manipulation Language) A linguagem de manipulação de dados]]**:

A DML lida com os dados propriamente ditos. Seus comandos são utilizados para inserir, atualizar, excluir e, mais importante, consultar os registros dentro das tabelas

---

**[[DCL (Data Control Language) A linguagem de Controle de Dados]]**:

A DCL é focada na segurança do banco de dados, gerenciando as permissões de acesso dos usuários ao dados.

---

**[[TCL (Transition Control Language) A linguagem de Controle de Transações]]**

A TCL gerencia as transações no banco de dados, garantindo a integridade dos dados ao agrupar uma sequência de operações em uma única lógica de trabalho. 

---



# Apresentando o SQL:


### Palavras Chaves em SQL:

- **Claúsulas** - FROM, WHERE, ORDER BY, etc.
- **Operadores lógicos** - AND, OR e NOT
- **Operadores relacionais** - <,>,<=,>=, = e <>
- **Funções de agregação** - AVG, COUNT, SUM, MAX MIN, etc.



# Conceitos Avançados: elavando o Nível das consultas

Para além dos comandos básicos, o verdadeiro poder do SQL reside em seus recursos avançados, que permitem a extração de insights complexos e a otimização de operações.


## JOINs: combinando Dados de Múltiplas Tabelas

Os ==JOINs== são fundamentais em bancos de dados relacionais, permitindo a combinação de linhas de duas ou mais tabelas com base em uma coluna relacionada.

- ==INNER JOIN==: Retorna apenas os registros que possuem correspondência em ambas as tabelas.
- ==LEFT JOIN== (ou ==LEFT OUTER JOIN==): Retorna todos os registros da tabela à esquerda e os registros correspondentes da tabela à direita. Se não houver correspondência, os campos da tabela direita apresentarão valores ==NULL==.
- ==RIGHT JOIN== (ou ==RIGHT OUTER JOIN==): O oposto do ==LEFT JOIN==. retorna todos os registros da tabela à direita e os correspondentes à esquerda
- ==FULL OUTER JOIN==: Retorna todos os registros quando há uma correspondência em uma das tabelas (esquerda ou direita)