
**Data:** 2026-02-25
**keyboards:** 
**links internos:** 
___


No contexto REST, o conceito de Stateless (sem estado) significa que o **servidor não armazena nenhuma informação sobre as interações anteriores** entre ele e o cliente. Cada requisição HTTP é tratada como um transação isolada e independente.

Para que isso funcione, cada mensagem enviado pelo cliente deve conter todas as informaações necessárias para que o servidor entenda e processe aquele pedido com sucesso.


## 1. Como funciona ná prática?

Imagine que você está fazendo um pedido em um restaurante:

- **Com Estado (Stateful):** Você diz "Eu quero um hambúrguer". O garçom anota. Depois você diz "Sem cebola". O garçom precisa lembrar que o "Sem cebola" se refere ao hambúrguer anterior. Se o garçom mudar no meio do processo, o novo não saberá o que você pediu.

- **Sem Estado (Stateless):** Você diz "Eu quero um hambúrguer". Se quiser mudar, você envia uma nova mensagem: "Eu quero um hambúrguer, mas sem cebola". Não importa qual garçom (servidor) te atenda, a mensagem tem tudo o que ele precisa saber.



## 2. Os pilares do Stateless no REST


- **Independência**: O servidor não guarda "sessões" (sessions) no banco de dados ou na memória para identificar o usuário entre um clique e outro.

- **Autenticação em cada envio**: Em vez de fazer login uma vez e o servidor "lembrar" de você, o cliente geralmente envia um **token** (como JWT) no cabeçalho (Header) de todas as requisições que exigem segurança.

- **Contexto completo**: Se a API filtrar dados de uma página específica, a requisição deve dizer explicitamente: ==GET /produtos?pagina=2==. O servidor não "lembra" de que você já estava na página 1.




***Porque Isso é o padrão hoje em dia?***

O modelo Stateless é o que permite que grandes paltaformas (como netflix ou instagram) aguentem mi;hões de acessos simultâneos. Se o servidor tivesse que manter uma "conversa" aberta com cada celular do mundo, ele travaria rapidamente.

