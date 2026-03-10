
**Data:** 2026-03-04
**keyboards:** 
**links internos:** 
___


# 1. A Interface ==Runnable== 

Pense no **Runnable** como um contrato. Ele não é o executor, é apenas a definição do que deve ser feito.

- **O que ele faz**: Ele possui apenas um método, o `public void run()`. Tudo o que você escrever dentro desse método será o trabalho que a thread vai realizar

- **Vantagem**: Como é uma interface, sua classe pode implementar ==Runnable== e ainda estender qualquer outra classe (lembre-se: Java não permite herança múltipla de classes, mas permite múltiplas interfaces).

![[image-16.png]]


# 2. A Classe ==Thread==

Se o Runnable é o manual de intruções, a Thread é o operário. Ela é quem realmente ganha vida dentro do sistema operacional e executa as instruções.


- **O que ela faz**: Ela gerencia todo o ciclo de vida da execução (iniciar, pausar, prioridade, etc.)

- **Como funciona**: Você cria uma thread Passando um Runnable para ela (o jeito mais comum e recomendado).

---


> **Cuidado com a pegadinha:** Nunca chame o método `run()` diretamente se quiser paralelismo. Se você fizer `thread.run()`, ele executa como um método comum na mesma linha (na thread principal). Para criar uma nova linha de execução, você **sempre** deve chamar o método `start()`.