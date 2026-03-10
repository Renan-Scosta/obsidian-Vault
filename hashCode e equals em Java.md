
**Data:** 2025-10-01
**keyboards:** 
**links internos:** 
___

# hashCode e equals

 São operações da Classe Object uitlizadas para comparar se um objeto é igual a outro

- **equals**: lento, resposta 100% precisa.
- **hashCode**: rápido, porém resposta positiva não é 100%

tipos comuns (String, Date, Integer, Double, etc.) já possuem implementação para essas operações. classes personalizadas precisam sobrepô-las.


## Equals: 

Método que compara se o objeto é igual a outro, retornando true ou false.

``` 
String a = "Marias";
String b = "Alex";

IO.println(a.equals(b));
```

## HashCode:

Método que retorna um número inteiro representando um código gerado a partir das informações do objeto

```
String a = "Maria";
String b = "Alex";

IO.println(a.hashCode());
IO.println(b.hashCode());
```

### regra de ouro do HashCode

- Se o hashCode de dois objetos for diferente, então os dois objetos são diferentes

![[Pasted image 20251001110145.png]]

- Se o código de dois objetos for igual, muito provavelmente os objetos são iguals (pode haver colisão)


## HashCode e Equals personalizados

```
public class Client {

	private String name;
	private String email;

}	
```

