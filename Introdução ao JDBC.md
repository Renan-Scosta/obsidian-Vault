
**Data:** 2026-01-08
**keyboards:** 
**links internos:** 
___

# JDBC

O JDBC (Java DataBase Connectivity) é uma API padrão incluída no java que permite que aplicações java se conectem, enviem comandos e recebam dados de **Bancos de dados Relacionais**
Pense no JDBC como uma ponte ou um tradutor.


**Conceito principal**: 

Cada banco de dados (MySQL, Oracle, PostgreSQL, SQL Server) "fala" uma lingua interna diferente. Sem o JDBC, você teria que escrever um código específico para o MySQL, outro complemente para Oracle, e assim por diante.

O JDBC resolve isso criando uma camada de abstração:

1. **Seu código Java**: Fala apenas "Java/JDBC" (métodos parametrizados).
2. **O driver JDBC**: É um pequeno software fornecido pelo fabricante do banco (ex: driver do MySQL). Ele atua como um tradutor que converte os comandos padronizados do JDBC para a linguagem específica daquele banco de dados.

você pode mudar de banco de dados (de postgreSQL para Oracle, por exemplo) trocando apenas o **Driver** (.jar) e a string de conexão, sem precisar reescrever todo seu código Java.

O JDBC é a base de tudo. Frameworks famosos e mais modernos como **Hibernate (JPA)** ou **Spring Data** são construidos em cima do JDBC. Eles facilitam o trabalho, mas por baixo dos panos, é o JDBC que está rodando. 


![[Pasted image 20260108220043.png]]
