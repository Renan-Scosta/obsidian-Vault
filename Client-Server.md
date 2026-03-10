
**Data:** 2026-02-25
**keyboards:** 
**links internos:** 
___


O conceito de Client-Server no REST é o princípio da separação de procupações.

Em uma arquitetura RESTful, o cliente e o servidor são entidades completamentes independentes que se comunicam apenas através de requisições e respostas.


# 1. Quem é quem?

- **O Cliente (Client):** É quem inicia a conversa. Ele é responsável pela **interface do usuário** e pela experiência do usuário (UX). Ele não se preocupa com como os dados são salvos no banco de dados.

- **O Servidor (Server):** É quem guarda os dados e processa a lógica de negócio. Ele não se preocupa com a aparência do botão na tela ou se o usuário está usando um celular ou um computador.


# 2. Por que essa separação é importante?

Essa divisão traz três vantagens principais para o desenvolvimento:

1. **Portabilidade (Evolução Independente):** Você pode ter um frontend feito em Angular, um aplicativo Android e um sistema de relatórios em Python, todos consumindo a mesma API Java no backend. Se você decidir mudar o design do site, o servidor nem precisa saber.

2. **Escalabilidade:** Como o servidor não cuida da interface, ele fica "mais leve" para processar apenas dados. Você pode aumentar a capacidade do servidor sem precisar mexer em nada no código do cliente.

3. **Simplicidade de Manutenção:** Se houver um bug na forma como os dados são validados, você mexe apenas no backend. Se for um erro de cor ou layout, mexe apenas no frontend.


# 3. O "contrato" entre eles

Para que essa separação funcione, ambos precisam concordar em um formato de comunicação. No REST, isso geralmente acontece via HTTP usando JSON ou XML.

- O Cliente diz: "Ei, servidor, me dê os dados do usuário 10." (request HTTP GET)

- O Servidor Responde: "Aqui estão os dados em formato JSON." (Response HTTP 200 OK)

Resumo: O clinete foca na apresentação e o servidor foca no armazenamento e processamento. Eles são "caixas pretas" um para o outro; só importa o que entra e o que sai pela API.