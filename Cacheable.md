
**Data:** 2026-02-25
**keyboards:** 
**links internos:** 
___


Dando continuidade aos pilares de REST, o conceito de **Cacheable** (Cacheável) dita que as respostas de uma API devem, explicitamente, dizer aos clientes se aquela informação pode ser "guardada" e por quanto tempo ela é válida.

Em termos práticos: Se o cliente (seu navegador ou app angular) já pediu uma lista de produtos há 5 segundos, ele não precisa gastar internet e processamento do servidor pedidno a mesma coida de novo se a API avisou que aquele dado "vale por 1 hora. 


## 1. Como a API avisa que algo é cacheável? 

No REST, usamos os **cabeçalhos HTTP (Headers)** para enviar essas instruções. Os principais são:

- **Cache-control**: É o mestre. Ele diz coisas como ==public== (qualquer um pode cachear), ==private== (só o navegador do usuário) ou ==max-age=3600== (isso vale por 1 hora).

- **ETag (Entity Tag)**: É como uma "impressão digital"do dado. Se o dado não mudaou no banco, a ETag é a mesma. O cliente pergunta: Ä ETag ainda é "xyz?". Se for, o servidor responde apenas um código **304 Not Modified** (sem enviar o corpo JSON), economizando muita banda.

- **Expires**: Uma data de validade fixa (ex: "válido até 31 de dezembro") 



## 2. Por que isso é vital no REST? 

O objetivo principal é a eficiência. Imagine uma API de clima: a temperatura de uma cidade não muda a cada milissegundo.

- **Redunção de latência**: O usuário receb a resposta instantaneamente (já esta no disco dele)

- **Economia de processamento**: Seu backend em Spring Boot não precisa bater no banco PostgreSQL toda hora para buscar algo que não mudou.

- **Escalabilidade**: Sua API aguenta muito mais acessos, já que boa parte das requisições nem chega a "acordar" o servidor.



## 3. O cuidado necessário: Dados "estragados"

O maior desafio do cache é a invalidação. Se você cacheou o preço de um produto por 24h e o gerente alterou o preço agora, o cliente continuará vendo o preço antigo até o cache expirar.


**Regra de bolso**: 

- **Dados que mudam pouco (CEP, lista de países, categorias)**: cache alto.

- **Dados que mudam sempre (saldo bancário, estoque em tempo real, chat)**: cache zero ou muito baixo.

---


***Onde isso encaixa no seu dia a dia?***

Como uso angular, o navegador já faz muito desse trabalho de cache automaticamente se você configurar os headers corretamente no seu backend Java. Além disso, você pode usar a ferramentas como o **Redis** para fazer cache dentro do seu próprio servidor, acelerando ainda mais as respostas.

