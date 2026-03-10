
**Data:** 2026-03-04
**keyboards:** 
**links internos:** 
___


Essas duas anotações são fundamentais para o Java entender como transformar sua classe em uma tabela no banco de dados.

A importância de cada uma: 

# 1. @Entity

Essa anotação é obrigatória. Ela avisa ao framework (como o hibernate) que a classe `User` não é apenas uma classe comum, mas sim uma **entidade de banco de dados**.

- **Função**: Diz ao Java "Crie uma tabela para armazenar os dados desta classe".
- **O que acontece se não usar**: O sistema ignorará a classe e nenhuma tabela será criada no banco.


# 2. @Table

Essa anotação é opcional. Ela serve para configurar os datalhes que será criada.

- **Função**: Permite que você que você escolha um nome específico para a tabela. Por padrão, O Java usa o próprio nome da classe (User), mas com `@Table(name = "users")`, você força o banco a usar o nome "users" (no plural).

---

# **Resumindo:**

- **@Entity:** Dá o "status" de tabela para a classe.

- **@Table:** Ajusta o "nome" e detalhes técnicos dessa tabela.