
**Data:** 2026-03-17
**keyboards:** 
**links internos:** 
___

# O que é o pacote config?

Na arquitetura em camadas do Spring Boot, o pacote `config` funciona como a **Central de comando** do seu projeto

Enquanto outros pacotes tem funções específicas para os dados (Models, services, Controllers), o config serve para ***Customizar o comportamento global do framework***:

- **Models/Entities:** Definem o que o Dado é.
- **Services:** Definem o que o sistema faz.
- **Configs**: Definem como o Spring se comporta perante o mundo exterior.

---

![[image-44.png]]

# O que o WebConfig esta realizando?

Esse Config específico é um "contrato" de regras de rede. Ao implementar `WebMvcConfigurer`, eu estou dizendo ao Spring: "Eu quero usar suas regras padrão da web, mas quero adicionar um detalhe meu".


O código que escrevi faz o seguinte:

- `@Configuration`: Avisa ao Spring que, assim que o projeto ligar, ele deve ler esta classe primeiro para configurar o ambiente.

- `@EnableWeb`: Ativa os recursos avançados de Web do Spring

- `addCorsMapping`: Essa é a parte mais importante. Ela resolve o problema de **CORS** (Croos-origin Resource Sharing)


#### Porque isso é necessário no meu caso?

O navegador tem uma trava de segurança: ele proíbe que um site (meu `index.html` abrindo via arquivo ou outra porta) peça dados para uma API (meu backend na porta 8080) sem permisão explícita.

Ao colocar `registry.addMapping("/**")`, eu estou criando uma **"Passagem livre"**. eu estou dizendo para o backend:

"Aceite requisições de qualquer lugar (origem) para qualquer caminho (endpoint) da minha API."

Sem isso, o meu JavaScript no frontend receberia um erro de bloqueio e não conseguiria listar as tarefas, mesmo que o Backend estivesse funcionando perfeitamente.