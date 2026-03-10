
**Data:** 2026-02-26
**keyboards:** 
**links internos:** 
___

## Origem do Padrão MVC

O padrão MVC foi criado por Trygve Reenskaug na década de 1970. Ele foi desenvolvido para enfrentar a complexidade que surgia ao criar interfaces gráficas interativas para os sistemas da época. A ideia principal por trás do MVC era separar a representação interna dos dados (**Model**) de forma como ele eram apresentados ao usuários (**View**), além de introduzir um componente que controlasse a interação entre eles (**Controller**).


## Entendendo o Padrão MVC

Imagine uma orquestras sinfônica. Temos os músicos (**Model**), o público (**View**) e o maestro (**Controller**) - cada um com um papel único que contribui para uma experiência harmoniosa. O padrão MVC traz essa mesma harmonia ao dividir um aplicação em três componentes fundamentais:


**1. Model**: Essa é a parte que gerencia os dados e a lógica de negócios da aplicação. Como os músicos de uma orquestra, ele trabalha nos bastidores para criar a experiência final

**2. View**: A View é a interface com o usuário, apresentando os dados do Modelo de forma compreensiva e agradável. É a parte visível da aplicação, como o palco de um esptáculo.

**3. Controller**: O Contralador age como o maestro, coordenando as ações do usuário e mantendo o Modelo e a View em sincronia. Ele é o cérebro por trás da operação, garantindo uma experiência agradável



# Exemplo correto: Aplicando MVC em Java

Vamos considerar uma aplicação de lsitas de tarefas. Aqui, queremos criar uma maneira eficiente de adicionar, marcar como concluida e visualizar tarefas. Apliquemos o padrão MVC para manter tudo organizado e estruturado.



**1. Model (Modelo)**:


![[Pasted image 20260226172056.png]]


***Por que isso esta correto***?

O Modelo é responsável por armazenar os dados da tarefa (descrição e estado) e fornecer métodos para acessa-los. Ele mantém a lógica de negócios separada da apresentação, garantindo um um código mais organizado e reutilizável.



**2. Visualização (View)**:


![[Pasted image 20260226172335.png]]



***Por que isto está correto***?

A Visualização cuida exclusivamente da apresentação dos dados. Ela recebe informações do controlador e exibe de maneira compreensível para o usuário. Isso também mantém a lógica de apresentação separada da lógica de negócios.



**3. Controlador (Controller)**:


![[Pasted image 20260226172632.png]]



***Por que isto está correto?***

O Controlador atua como intermediário entre o Model e o View. Ele recebe as ações do usuário (como definir a descrição da tarefa ou marcar como concuída), atualiza o Modelo e informa à View para mostrar os resultados. Isso mantém as reponsabilidades bem definidas e evita a mistura de lógicas.




## Por que tudo isso importa?

A aplicação correta do padrão MVC é um jornada rumo a clareza e à modularidade. Essa separação de responsabilidade simplifica a manuntenção e permite que você faça alterações em uma parte sem afetar as outras.