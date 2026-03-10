
**Data:** 2026-03-10
**keyboards:** 
**links internos:** 
___

# O que são os Services?

No padrão de arquitetura que estou usando (Spring boot com camadas), o **Service** é a camada responsável por guardar a lógica de negócio da minha aplicação.

Imagine que o controller é apenas a porta de entrada que recebe as requisições (pedidos) da internet. O Service é o cérebro que processa esses pedidos antes de salvar qualquer coisa no banco de dados.

### Qual o papel dele?


##### 1. Regras de negócio:

- Se você precisar validar se um e-mail já existe, calcular um desconto ou verificar se um usuário tem permisão para deletar um tarefa, isso deve ser feito no service.

##### 2. Mediação:

- Ele fica entre o Controller (que lida com a web) e o Repository (que lida com o banco de dados).

##### 3. Transações (@Transactional):

- Como usado no meu código, o Service garante que uma operação seja concluida por inteiro. Por exemplo: se você criar um usuário e várias tarefas ao mesmo tempo (como seu método `create`) O service garante que ou tudo é salvo com sucesso ou nada é salvo (evitando dados incompletos se houver um erro no meio do processo).

##### 4. Reutilização:

- Vários Controllers podem chamar o mesmo Service, evitando que você repita o mesmo código em vários lugares.


---

### Resumo do fluxo

1. **Controller:** Recebe o JSON da requisição e chama o Service.
2. **Service:** Valida as regras e decide o que fazer com os dados.
3. **Repository:** Executa o comando SQL no banco de dados.