
**Data:** 2026-03-04
**keyboards:** 
**links internos:** 
___


Essas anotações servem para configurar como cada atributo da sua classe vai se comportar dentro das colunas do banco de dados.

A importância de cada uma:


# 1. @Id

Essa anotação define qual campo será a **chave primária - (Primary Key)** da sua tabela.

- **Função**: identificar de forma única cada registro. Sem ela, o JPA não consegue diferenciar um usuário de outro.

- **Regra**: Toda classe `@Entity` precisa de obrigatoriamente de um `@Id`.

---
# 2. @GeneratedValue

Ela trabalha junto com o `Id` para definir **quem cria o valor do ID**.

- **Função**: automatizar a numeração dos IDs (1, 2, 3..) para que você não precisa fazer isso manualmente no código.



#### Os principais GenerationsTypes:

| **Tipo**     | **O que faz**                                                                                        |
| ------------ | ---------------------------------------------------------------------------------------------------- |
| **IDENTITY** | O banco de dados cria o número sozinho (auto-incremento). É o mais usado em MySQL e PostgreSQL.      |
| **SEQUENCE** | Usa um objeto do banco chamado "Sequence" para gerar o próximo número. Comum em Oracle e PostgreSQL. |
| **AUTO**     | O framework (Hibernate) escolhe a melhor estratégia baseada no banco de dados que você está usando.  |
| **TABLE**    | Cria uma tabela separada apenas para guardar o último ID gerado. É o mais lento e pouco usado.       |

---
# 3. @Column

Serve para costumizar a coluna no banco de dados. Se você não colocar nada, o Java cria a coluna com o nome do atributo e configuração padrão.

- **Função**: Ajustar detalhes técnicos do campo:

#### Principais parâmetros do @Column:

- `name` : Muda o nome da coluna do banco (ex: `name = "user_email"`)
- `nullable = false`: Garante que o campo nunca seja vazio (NOT NULL)
- `unique = true`: Garante que não existam dois registros com o mesmo valor (ex: e-mail único)
- `length`: Define o tamanho máximo de caracteres (ex: `length = 100`)