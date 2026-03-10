
**Data:** 2025-04-08
**keyboards:** 
**links internos:** 
___

### 🔑 **O que é um HashMap?**

Um **HashMap** é uma estrutura de dados que armazena **pares chave-valor**. Ele permite acessar rapidamente um valor a partir de sua chave.


### 🧠 **Como funciona?**

- Usa uma **função hash** para transformar a chave em um **índice**.
    
- Esse índice determina onde o valor será armazenado em uma **tabela interna (array)**.
    
- Se duas chaves diferentes geram o mesmo índice (colisão), elas são tratadas com técnicas como **encadeamento** ou **endereçamento aberto**.


### ✅ **Vantagens**

- Acesso rápido a dados.
    
- Fácil de usar.
    
- Evita duplicação de chaves (substitui valor se mesma chave for usada).


## ⚠️ **Desvantagens**

- Ordem dos elementos **não é garantida**.
    
- Desempenho pode cair com muitas colisões.
    
- Precisa de uma boa função hash.



# Código exemplo:

![[Pasted image 20250424121132.png]]

![[Pasted image 20250424121210.png]]

![[Pasted image 20250424121238.png]]

![[Pasted image 20250424121303.png]]
