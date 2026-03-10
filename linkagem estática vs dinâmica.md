 
**Data:** 2025-11-21
**keyboards:** 
**links internos:** 
___
# contexto: processo de compilaçao

Antes de falar dos tipos de linkagem, precisamos lembrar onde o "Linker" entra na história. Quando você compila um código em C (gcc main.c), o processo tem etapas: 

1. Pré-processamento: Resolve ===#include=== e macros.
2. Compilação: Transforma C em Assembly.
3. Montagem (Assembler): Transforma Assembly em código objeto (.o ou .obj).
4. Linking: Junta o seu código objeto com as bibliotecas que você usou (como a biblioteca que contém ===printf===) para criar o Executável final.

A grande questão é: Como o linker junta essas bibliotecas ao seu código? É aqui que a estrada se divide


## 1. Linkagem estática (static linking)

Na linkagem estática, o linker faz uma cópia física de todo o código das bibliotecas que você usou e o insere diretamente dentro do seu arquivo executável final.


**Como funciona (a metáfora do livro)**
 
imagine que você está escrevendo um trabalho escolar (seu programa) e quer citar um poema famoso (uma função da biblioteca)
 - na linkagem estática, você copia o poema inteiro e o escreve nas páginas do seu trabalho.
 - agora, o poema faz parte inseparável do seu caderno.

**Detalhes técnico**:

- *No momento da compilação*: O linker busca o arquivo da biblioteca estática (geralmente .a no linux ou .lib no windows). ele extrai o código de máquina das funções necessárias (ex: o código binário printf) e o anexa ao seu binário.
- *resultado*: O arquivo executável final é um "pacote completo". ele não precisas de nenhum outro arquivo externo pra rodar.


**Desvantagens**:

1. *Tamanho do arquivo*: O executável fica gigante. Se você fizer 10 programas simples que usam a mesma biblioteca, você terá 10 cópias desse código ocupando espaço em disco.
2. *dificuldade de atualização*: Se for descoberto um bug de segurança na biblioteca que você usou, você precisa recompilar e redistribuir seu programa inteiro para incluir a correção


## 2. Linkagem dinâmica (Dynamic Linking) 

Na linkagem dinâmica, o linker não copia o código da biblioteca para o seu executável. Em vez disso, ele coloca apenas uma referência (um apontamento ou endereço) dizendo: "quando precisar dessa função, procure no arquivo X do sistema operacional".


**Como funciona (A metáfora do Hyperlink)**

Voltando ao trabalho escolar: 
-  Na linkagem dinâmica, em vez de copiar o poema, você escreve apenas: "vide página 40 do livro de antologia poética da biblioteca".
- Quando alguém for ler seu trabalho (executar o programa), essa pessoa precisará ter o livro "antologia poética" na estante.

**Detalhes técnicos**

- *Arquivos envolvidos*: As bibliotecas vivem em arquivos separados, chamados de shared libraries.
	- Window: .d11 (dynamic link library)
	- Linux: .so (shared object)
- *tempo de execução*: Quando você clica em abrir o programa, o sistema operacional (o "loader") vê que seu programa precisa de uma DLL específica. Ele carrega essa DLL na memória RAM e conecta os pontos.


**Vantagens**: 

1. *Economia de memória e disco*: Se 50 programas (chrome, word, spotify, etc) usam a mesma biblioteca do sistema para desenhar janelas na tela, o sistema operacional carrega essa biblioteca na memória RAM **uma única vez** e todos os programas **compartilham** essa mesma cópia.
2. *Facilidade de atualizaação*: Se a biblioteca tem um bug, basta atualizar o arquivo .d11 ou .so, todos os programas que usam essa biblioteca passam a usar a versão corrigida automaticamente na próxima vez que forem abertos, sem precisar recompilar nada.

**Desvantagens**: 

1. *Dependência (DLL Hell)*: Se você tentar rodar um programa em um computador que não tem aquela biblioteca específica instalada (ou tem uma versão diferente/incompativel), o programa **Não abre**. É o clássico erro "falta msvcr100.dll"


## 2.1 o cenário em Java

Java funciona de maneira peculiar que se assemelha quase inteiramente com à **linkagem dinâmica (dynamic linking)**.


Em Java, você não gera um .exe (nativo) com tudo incluido normalmente.

1. Você compila seu código ==.java== para ==.class== (bytecode).
2. Quando você roda o programa (java MeuPrograma), a JVM (java virtual machine) atua como um grande carregador dinâmico.
3. Se seu código usa uma classe externa (ex: ==ArrayList==), a JVM vai procurar essa classe nas bibliotecas do Java (o JDK/JRE) ou no seu classpath **apenas no momento em que ela for necessária**.


**Em resumo**: Java é dinâmico por natureza. Se você alterar um arquivo .class de uma biblioteca e reiniciar a aplicação Java, ela pegará a mundaça imediatamente.

- Em versões moderníssimas do Java (GraalVM Native Image), é possivel fazer uma compilação "AOT" (Ahead of Time) que cria um executável nativo. nesse caso específico, o Java se comporta como linkagem estática, empacotando tudo num binário só.



