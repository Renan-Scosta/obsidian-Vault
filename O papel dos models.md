
**Data:** 2026-03-05
**keyboards:** 
**links internos:** 
___

No contexto do meu projeto (todosimple), o pacote models e as classes User e Task representam a camada de dados e a lógica da aplicação.


Os principais papéis que esses models exercem:

# 1. Representação do Objeto (POJO)

No mundo da POO, o model é a definição de "coisas" do seu sistema.

- **User**: Define o que é um usuário (id, nome, senha)

- **Task**: Define o que é uma tarefa (id, descrição) e a quem ela pertence. Nessa 


camada, você define as regras de básicas: "um usuário não pode ter nome vazio" ou "a senha deve ter no mínimo 8 caracteres.


# 2. Entidade de banco de dados (JPA/Hibernate)

Como você usou a anotação `@Entity`, essas classes deixam de ser apenas objetos Java comuns e passam a ser **Entidades**.

- O papel aqui é o **Mapeamento Objeto-Relacional (ORM)**.

- A Classe **User** diz ao Hibernete: "Crie uma tabela chamada "users" com estas colunas

- As annotations como @Id, @Column e @JoinColumn são as instruções de como transformar o código Java em tabelas, colunas e relacionamento (como chaves estrangeiras) no seu banco MariaDB


# 3. O "M" do padrão MVC

O Spring Boot geralmente segue o padrão **MVC** (Model-View-Controller).

- **Model (Modelo):** É onde os dados moram. Ele não sabe como os dados serão exibidos (View) nem como eles chegaram lá (Controller); ele apenas guarda a informação e garante que ela seja válida.
 
- Quando você buscar um usuário no banco, o Spring vai instanciar essa classe `User` e preencher os dados para você usar no restante do código.


## Próximo passo: Repository

Vai usar esses modelos para salvar e buscar no banco.

