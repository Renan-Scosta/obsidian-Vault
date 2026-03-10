
**Data:** 2025-04-08
**keyboards:** 
**links internos:** 
___

### 🌳 **O que é um TreeMap?**

Um **TreeMap** é uma estrutura de dados que também armazena **pares chave-valor**, **ordenados automaticamente pela chave**.  
É baseado em uma **árvore binária de busca balanceada**, geralmente uma **Red-Black Tree**.


### 🔧 **Como funciona?**

- As chaves são armazenadas de forma **ordenada**.

- Cada inserção ou remoção **mantém a ordem** e o **balanceamento** da árvore.

- A ordenação pode ser **natural** (ex: ordem alfabética ou numérica) ou baseada em um **comparador customizado**.


### ✅ **Vantagens**

- Mantém os elementos **ordenados por chave**.

- Permite buscas por **intervalos** (ex: de X até Y).

- Ideal quando você precisa de **ordenação natural**.


## ⚠️ **Desvantagens**

- Mais **lento** que um HashMap para operações simples (por ser O(log n)).
    
- Não permite **chaves nulas** (em Java, por exemplo).


# Código exemplo:

![[Pasted image 20250424121438.png]]
