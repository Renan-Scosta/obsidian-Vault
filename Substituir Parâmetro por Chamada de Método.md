
**Data:** 2025-10-22
**keyboards:** 
**links internos:** 
___

# Substituir parâmetro por chamada de método


## Problema

Chamar um método de consulta e passar seus resultados como parâmetros de outro método, enquanto esse método poderia chamar a consulta diretamente.

```
int  basePrice  =  quantidade  *  itemPrice ;
double seasonDiscount = this . getSeasonalDiscount ( ) ;
double fees = this . getFees ( ) ;
double finalPrice = discountedPrice ( basePrice , seasonDiscount , fees ) ;
```

## Solução

Em vez de passar o valor por meio de um parâmetro, tente colocar uma chamada de consulta dentro do corpo do método.

```
int  basePrice  =  quantidade  *  itemPrice ; 
double finalPrice = discountedPrice ( basePrice ) ;   
```


# Por que refatorar?

Uma longa lista de parâmetros é difícil de entender. Além disso, chamadas para esses métodos frequentemente se assemelham a uma série de cascatas, com cálculos de valores complexos que são difíceis de navegar, mas que precisam ser passados  ao métodos. portanto, se o valor de um parâmetro puder ser calculado com a ajuda de um método, faça isso dentro do próprio método e livra-se do parâmetro.


# Benefícios

Eliminamos parâmetros desnecessários e simplificamos chamadas de métodos. Esses parâmetros geralmente não são criados para o projeto atual, mas sim pensando em necessidades futuras que podem nunca chegar.


# Desvantagens

Você pode precisar do parâmetro amanhà para outras necessidades.. o que fará com que você reescreva o método



# Como refatorar

1. Certifique-se de que o código de obtenção de valor não use parâmetros do método atual, pois eles não estarão disponiveis dentro de outro método. Nesse caso, não será possivel mover o código.

2. Se o código relevante for mais complicado do que uma única chamada de método ou função, use Extrair Método para isolar esse código em um novo método e simplificar a chamada.

3. No código do método principal, substitua todas as referências ao parâmetro que está sendo substituído por chamadas ao método que obtém o valor.

4. Use Remover parâmetro para eliminar o parâmetro não utilizado.


