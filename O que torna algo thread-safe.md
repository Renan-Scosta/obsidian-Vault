
**Data:** 2026-03-05
**keyboards:** 
**links internos:** 
___

Ser **thread-safe** (seguro para threads) significa que um trecho de código, objeto ou estrutura de dados garante que as informações permanecerão consistentes e o comportamento será correto, mesmo se **várias threads tentarem acessá-lo e modificá-lo exatamente ao mesmo tempo**.

Para entender de forma prática, é mais fácil olhar para o que acontece quando algo **não** é thread-safe.

### O Problema: Condição de Corrida (Race Condition)

Imagine uma variável `contador = 0` e duas threads tentando adicionar 1 a esse contador no mesmo milissegundo. O fluxo desprotegido ocorre assim:

1. A Thread A lê o valor atual: `0`.

2. A Thread B lê o valor atual: `0`.

3. A Thread A soma 1 e salva o novo valor: `1`.

4. A Thread B soma 1 e salva o novo valor: `1`.


O resultado final salvo na memória foi `1`, mas o correto deveria ser `2`. Houve corrupção de estado porque as operações se sobrepuseram.

### Como um código se torna Thread-Safe?

Para evitar o problema acima e garantir a segurança, a linguagem ou a estrutura de dados precisa implementar mecanismos de controle. Em Java, isso geralmente é feito de três maneiras:

- **Bloqueios de Exclusão Mútua (Locks/Sincronização):** Estabelece um bloqueio exclusivo. Quando uma thread entra em um método ou bloco de código, as outras threads que tentam acessar o mesmo recurso são colocadas em espera até que a primeira termine e libere o acesso. (Exemplo: palavra-chave `synchronized`).

- **Operações Atômicas:** A operação de ler, modificar e gravar acontece como um passo único e indivisível, geralmente com suporte direto do hardware do processador. É impossível que uma thread seja interrompida no meio dessa operação específica. (Exemplo: classes como `AtomicInteger`).

- **Imutabilidade:** Se um objeto é criado e seu estado interno nunca mais pode ser alterado, ele é naturalmente thread-safe. Se os dados são apenas para leitura, milhares de threads podem acessá-los ao mesmo tempo sem risco de corrupção. (Exemplo: a classe `String`).


Resumindo: quando você usa uma coleção que é thread-safe (como o `ConcurrentHashMap`), a própria classe já possui esses controles embutidos no seu código interno. Ela garante que, se duas threads tentarem inserir dados ao mesmo tempo, nenhuma informação será perdida ou corrompida.