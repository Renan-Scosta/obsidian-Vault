
**Data:** 2026-03-02
**keyboards:** 
**links internos:** 
___

# Explicação sobre as configurações inicias


![[Pasted image 20260302142815.png]]

Na configurção inicial eu fiz essa separação entre pastas, respeitando o **SRP (Single Responsability principle)** que é o princípio de responsabilidade única, essa divisção é fundamental para garantir que cada parte do meu código faça apenas uma coisa e faça bem.


Vou explicar a função de cada uma delas abaixo:


## 1. models 

Esta pasta contém o "blueprint" (projeto) dos seus dados.

- **Função**: É nela que você define suas classes de entidade (com a anotação *@Entity*) que o hibernate transforma em tabelas no seu banco de dados.

- **Razão**: Representar os objetos do mundo real (como uma Task ou User) e definir como eles serão estruturados no banco de dados.


## 2. repositories

Aqui fica o "bibliotecário" do seu sistema.

- **Função**: São interfaces que estendem o JpaRepository. Elas contêm os métodos para prontos para salvar, deletar, buscar e atualizar dados no banco.

- **Razão**: Isolar o SQL ou as chamadas de banco dados do resto da aplicação. você não precisa escrever consultas complexas, o Spring Data JPA faz isso por você.


## 3. services

Esta é a camada do "cérebro" ou da lógica de negócio.

- **Função**: Aqui você coloca as regras. Por exemplo: "uma tarefa só pode ser marcada como concluída se o usuário for o dono dela.

- **Razão**: Evitar que o controller fique sobrecarregado. o Service serve de ponte entre o Controller e o Repository , garantindo que os dados sejam validados antes de chegarem no banco.


## 4. controllers

O "Porteiro" da sua API.

- **Função**: responsável por expor o endspoints (URLs) que o seu navegador ou o posting vão acessar (ex: ==GET== /tasks). ele recebe as requisições HTTP e devolve as repostas JSON.

- **Razão**: Tratar apenas da entrada e saida de dados. Ele recebe o que o usuário enviou , "pergunta" para o service o que deve ser feito e devolve o resultado final.



## O fluxo de dados

Para você visualizar como essas pastas conversam no seu dia a dia de estudos, o caminho que um dado percorre é geralmente este:

1. **Usuário** faz um pedido (HTTP Request) -> **Controller**.
2. **Controller** chama o **Service** para processar a lógica.
3. **Service** usa o **Repository** para persistir o **Model**.
4. **Repository** salva no **MariaDB**.

