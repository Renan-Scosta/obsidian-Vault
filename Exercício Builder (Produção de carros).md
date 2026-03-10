
**Data:** 2025-10-22
**keyboards:** 
**links internos:** 
___

# Produção de um automóvel passo a passo

Neste exemplo, o padrão Builder permite a construção passo a passo de diferentes modelos de carros.

O exemplo também mostra como o Builder produz produtos de diferentes tipos (manual do carro) usando as mesmas etapas de construção.

O diretor controla a ordem da construção. Ele sabe quais etapas de construção chamar para produzir este ou aquele modelo de carro. Ele funciona com builders apenas por meio de sua interface comum. Isso permite passar diferentes tipos de builders para o diretor.

O resultado final é recuperado do objeto builder porque o diretor não pode saber o tipo de produto resultante. Somente o objeto builder sabe o que exatamente ele cria.


# Código:

https://refactoring.guru/pt-br/design-patterns/builder/java/example




# Explicando o código:

Este é um exemplo excelente e completo do padrão **Builder** na sua forma "clássica", também conhecida como a versão "Gang of Four" (GoF).

Vamos quebrar o que está acontecendo.

---

### O que esse código faz (em alto nível) 🤖

Este código simula uma **fábrica de automóveis**.

O objetivo é **separar o processo de construção de um carro (ou seu manual) da sua representação final**.

Em vez de criar um carro com um construtor gigante (ex: `new Car(tipo, 2, motorV8, cambio, ...)`), você usa um "construtor" (Builder) passo a passo.

A parte mais legal deste exemplo é que ele usa **exatamente o mesmo processo** (as mesmas "receitas" do Diretor) para construir duas coisas completamente diferentes:

1. Um objeto `Car` (o carro físico).
    
2. Um objeto `Manual` (o manual de instruções do carro).
    

---

### Os 4 Papéis do Padrão Builder (Quem é Quem no Código)

Para entender, olhe para estas 4 funções principais:

#### 1. O "Produto" (Product) 🚗

É o objeto complexo que queremos criar.

- **No código:**
    
    - `cars/Car.java`: Representa o carro em si.
        
    - `cars/Manual.java`: Representa o manual de instruções.
        
- **Observe:** Eles têm construtores cheios de parâmetros. O padrão Builder existe para que _você_ (o cliente) não precise chamar esses construtores complicados diretamente.
    

---

#### 2. A "Planta" (Builder Interface) blueprint

É a interface que define _quais etapas_ são necessárias para construir o produto. É um contrato.

- **No código:** `builders/Builder.java`
    
- **O que faz:** Ela diz: "Qualquer um que queira ser um construtor _deve_ saber como..."
    
    - `setCarType(...)`
        
    - `setSeats(...)`
        
    - `setEngine(...)`
        
    - `setTransmission(...)`
        
    - ...e assim por diante.
        

---

#### 3. A "Linha de Montagem" (Concrete Builder) 🏭

É a classe que _implementa_ a "Planta" (Builder). Ela sabe como executar cada etapa e guardar as peças. É ela quem de fato monta o produto.

- **No código:**
    
    - `builders/CarBuilder.java`: Sabe como montar um objeto `Car`.
        
    - `builders/CarManualBuilder.java`: Sabe como montar um objeto `Manual`.
        
- **O que fazem:**
    
    - Ambas implementam a interface `Builder`.
        
    - Elas têm campos privados (`type`, `seats`, `engine`...) para "guardar as peças" que recebem.
        
    - **O mais importante:** Elas têm um método `getResult()` que pega todas as peças guardadas e cria o produto final (chamando `new Car(...)` ou `new Manual(...)`).
        

---

#### 4. O "Gerente de Produção" (Director) 🧑‍💼

É uma classe **opcional**, mas central neste exemplo. O Diretor sabe a _ordem_ das etapas (a "receita") para construir uma _versão específica_ do produto.

- **No código:** `director/Director.java`
    
- **O que faz:**
    
    - Ele **não sabe** qual produto final está sendo construído. Ele só conhece a interface `Builder` (a "Planta").
        
    - Ele tem "receitas" prontas:
        
        - `constructSportsCar(Builder builder)`: "Para fazer um carro esportivo, chame `builder.setCarType(SPORTS_CAR)`, depois `builder.setSeats(2)`, depois `builder.setEngine(new Engine(3.0, 0))...`"
            
        - `constructCityCar(Builder builder)`: "Para um carro urbano, chame `builder.setCarType(CITY_CAR)`, `builder.setSeats(2)`, `builder.setEngine(new Engine(1.2, 0))...`"
            

---

### A "Mágica" deste Exemplo (A Análise do `Demo.java`)

Vamos ver o fluxo no `Demo.java`, que é onde tudo se junta:

**Parte 1: Construindo o Carro**

1. `Director director = new Director();`
    
    - Cria o "Gerente de Produção" (que sabe as receitas).
        
2. `CarBuilder builder = new CarBuilder();`
    
    - Cria a "Linha de Montagem de Carros".
        
3. `director.constructSportsCar(builder);`
    
    - **Este é o passo crucial!** O "Gerente" é chamado para executar a receita "constructSportsCar".
        
    - Ele pega a "Linha de Montagem de Carros" (`builder`) e diz:
        
        - "Ei, `builder`, `setCarType(SPORTS_CAR)`!"
            
        - "Ei, `builder`, `setSeats(2)`!"
            
        - "Ei, `builder`, `setEngine(...)`!"
            
    - O `CarBuilder` vai guardando todas essas peças (`this.type = SPORTS_CAR`, `this.seats = 2`, ...).
        
4. `Car car = builder.getResult();`
    
    - Agora que o "Gerente" terminou de dar as ordens, pedimos à "Linha de Montagem" (`builder`): "Me dê o resultado".
        
    - O `CarBuilder` executa seu método `getResult()`, que faz: `return new Car(this.type, this.seats, this.engine, ...);`.
        
    - Você recebe um objeto `Car` pronto, sem nunca ter chamado o construtor `new Car(...)` diretamente.
        

**Parte 2: Construindo o Manual (Usando a MESMA receita)**

1. `CarManualBuilder manualBuilder = new CarManualBuilder();`
    
    - Cria uma _outra_ "Linha de Montagem", desta vez a "Linha de Montagem de Manuais".
        
2. `director.constructSportsCar(manualBuilder);`
    
    - **Esta é a mágica!** Você chama o **mesmo Gerente** (`director`) para executar a **mesma receita** (`constructSportsCar`).
        
    - O Gerente, que não sabe a diferença, faz as **mesmas chamadas**:
        
        - "Ei, `manualBuilder`, `setCarType(SPORTS_CAR)`!"
            
        - "Ei, `manualBuilder`, `setSeats(2)`!"
            
        - "Ei, `manualBuilder`, `setEngine(...)`!"
            
    - O `CarManualBuilder` agora guarda essas mesmas informações.
        
3. `Manual carManual = manualBuilder.getResult();`
    
    - Pedimos o resultado à "Linha de Montagem de Manuais".
        
    - O `CarManualBuilder` executa seu `getResult()`, que faz: `return new Manual(this.type, this.seats, this.engine, ...);`.
        
    - Você recebe um objeto `Manual` pronto.
        

### Conclusão

O padrão Builder aqui permitiu:

1. **Abstrair a construção:** O cliente (`Demo.java`) não precisa saber _como_ um carro é montado, apenas pede um.
    
2. **Construir objetos complexos passo a passo:** O `Director` faz isso, chamando um método de cada vez.
    
3. **Reutilizar a lógica de construção:** O `Director` usou a **mesma lógica** (`constructSportsCar`) para criar dois objetos totalmente diferentes (`Car` e `Manual`), apenas trocando o `Builder` que foi passado para ele.