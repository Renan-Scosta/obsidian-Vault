
**Data:** 2025-08-23
**keyboards:** 
**links internos:** 
___

##### **O que é um Array?**

Um array é, no fundo, um pedaço contínuo de memória reservado para armazenar elementos do mesmo tipo

-> Exemplo: um arrya de int com 5 posiçoes.

- Cada int ocupa, digamos, 4 bits
- O compilador/Interpretador reserva 5 X 4 = 20 contínuos.

Na memoria ficaria algo assim (endereços hipoteticosem haxadecimal)

Endereço   Valor
0x1000     10   ← array[0]
0x1004     20   ← array[1]
0x1008     30   ← array[2]
0x100C     40   ← array[3]
0x1010     50   ← array[4]

Ou seja:

- O endereço base do array é 0x1000.
- para acessar array(i), a CPU calcula:
endereço = base + (i * tamanho_elemento)

- Assim, array[2] = 0x1000 + (2 * 4) = 1008

##### **Propiedades fundamentais**

1. **Contiguidade**
	- Os elementos ficam lado a lado, sem "buracos" 
	- Isso garante acesso aleatório ***O(1)*** (qualquer índice é acessado direto pelo cálculo de endereço).
2. **Homogeneidade**:
	- Todos os elementos tem o mesmo tamanho fixo, o que permite o cálculo de deslocamento.
3. **Tamanho fixo**:
	- Normalmente, ao declarar, você já precisa dizer quantos elementos o array terá (ou então ele precisa realocar um novo bloco quando crescer, como python faz por baixo dos panos)

##### **Acesso na memória**

O CPU nao entende "indice de array", Só entende endereços de memória
O indice é só uma forma do programador acessar, mas internamente vira "**Aritmética de ponteiros**"

Exemplo em C (baixo nivel):

int arr[5] = {10, 20, 30, 40, 50};
printf("%d\n", *(arr + 2)); // acessa arr[2]

##### **Em python**

A ==list== não é um array puro:

- Ela é um arrya de ponteiros -> Bloco contíguo de endereços de objetos.
- Os valores Reais (Inteiros, Strings, etc.) Ficam em outros lugares da memória

Exemplo: 

lista = [10, 20, 30]

**na memória**:

lista (array de ponteiros):
0x2000 → 0x5000 (objeto int 10)
0x2008 → 0x5010 (objeto int 20)
0x2010 → 0x5020 (objeto int 30)

objetos reais:
0x5000: int(10)
0x5010: int(20)
0x5020: int(30)

### Resumo : 

- Array = **Bloco contíguo na memória**.
- endereço de array[i] é calculado via **Aritmética de ponteiros**.
- todos os elementos tem o mesmo tamanho e ficam lado a lado.
- Em python, a ==list== é um array de endereços (ponteiros), nao de valores diretos.
