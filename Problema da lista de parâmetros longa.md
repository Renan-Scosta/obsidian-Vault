
**Data:** 2025-10-22
**keyboards:** 
**links internos:** 
___

# Sinais e sintomas

Mais de três ou quatro parâmetros para um método


![[Pasted image 20251022091006.png]]



# Razões para o problema

Uma longa lista de parâmetros pode surgir após um fusão de vários tipos de algoritmos em um único método. Uma longa lista pode ter sido criada para controlar qual algoritmo será executado e como.

Listas de parâmetros longas também podem ser o subproduto de esforços para tornar as classes mais independentes umas das outras. Por exemplo, o código para criar objetos epecíficos necessários em um método foi movido do método para o código para chamar o método, mas os objetos criados são passados para o método como parâmetros,. Assim, a classe original não sabe mais sobre os relacionamentos entre os objetos, e a dependência diminuiu. Mas se vários desses objetos forem criados, cada um deles exigirá seu próprio parâmetro, o que significa uma lista de parâmetros mais longa.

É difícil entender essas listas, que se tornam contraditórias e difíceis de usar à medida que aumentam. Em vez de uma longa lista de parâmetros, um método pode usar os dados do seu próprio objeto. Se o objeto atual não contiver todos os dados necessários, outro objeto (que obterá os dados necessários) pode ser passado como parâmetro do método.


# Tratamento

- Verifique quais valores são passados ​​aos parâmetros. Se alguns dos argumentos forem apenas resultados de chamadas de método de outro objeto, use [[Substituir Parâmetro por Chamada de Método]] . Este objeto pode ser colocado no campo de sua própria classe ou passado como um parâmetro de método.

- Em vez de passar um grupo de dados recebidos de outro objeto como parâmetros, passe o próprio objeto para o método, usando [[Preserve Whole Object]]

- Mas se esses parâmetros vierem de fontes diferentes, você pode passa-los como um único objeto de parâmetros por meio de [[introduzir Objeto de Parâmetro]]



# Payoff

- Código mais legível e mais curto.

- A refatoração pode revelar código duplicado que não havia sido notado anteriormente.


# Quando ignorar

- Não se livre de parâmetros se isso causar dependência indesejada entre classes.
