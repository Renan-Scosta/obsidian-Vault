
**Data:** 2026-03-11
**keyboards:** 
**links internos:** 
___

# PROCESSOS

Um conceito fundamental em todo os SIstemas operacionais é o **Processo.** Um processo é basicamente um programa em execução. Associado a cada processo está o **Espeço de endereçamento**, uma lista de posições de memória que vai de o a algum máximo, onde o processo pode ler e escrever. O espaço de endereçamento contém o programa executável, os dados do programa e sua pilha. Também associado com cada processo há um conjunto de recursos, em geral abrangendo registradores (incluindo o contador do programaa e o ponteiro de pilha), listas de processos relacionados e todas as demais informações necessárias para executar um programa.
Um processo é na essência um contêiner que armazena todas as informações necessárias para executar um programa.

Em qualquer Sistema de multiprogramação, a CPU muda de um processo para o outro toda rapidamente, executando cada um por dezenas ou centenas de milissegundos. Enqunato, estritamente falando, em qualquer dado instante a CPU está executando apenas um processo, no curso de 1 segundo ela pode trabalahr em vários deles, dando a ilusão de paralelismo.

Ter controle sobre múltiplas atividades em paralelo é algo difícil para as pessoas realizarem, portanto, projetistas de sistemas operacionais através dos anos desenvolveram um modelo conceitual (**processos sequenciais**) que torna o paralelismo algo mais fácil de lidar. Esse modelo, seus usos e algumas das suas consequências compõem o assunto deste Artigo.


---
## O modelo de processo

Nesse modelo, todos os softwares executáveis no computador, ás vezes incluindo o sistema operacional, são organizados em uma série de **processos sequenciais**, ou simplesmente, **processos**.
Um Processo é apenas uma instância de um programa em execução, incluindo o contador do programa, registradores e variáveis.

Conceitualmente, cada processo tem sua própria **CPU virtual**. Na verdade, a CPU real troca a todo momento de processo em processo, mas para compreender o sistema, é muito mais fácil pensar a respeito de uma coleção de processos sendo executados em (pseudo) paralelo do que tentar acompanhar como a CPU troca de programa para outro. Esse mecanismo de trocas rápidas e chamado de **multiprogramação**.

![[image-38.png]]

Na Figura 2.1(a) vemos um computador multiprogramando quatro programas na memória.

Na Figura 2.1(b) vemos quatro processos, cada um com seu próprio fluxo de controle (isto é, seu próprio contador de programa lógico) e sendo executado independente dos outros. É claro que há apenas **um contador de programa físico**, de maneira que, quando cada processo é executado, o seu contador de programa lógico é carregado para o contador de programa real. No momento em que ele é concluído, o contador de programa físico é salvo no contador de programa lógico do processo na memória.

Na figura 2.1(c) vemos que analisados durante um intervalo longo o suficiente, todos os processos tiveram progresso, mas a qualquer dado instante apenas um está sendo de fato executado. 
Claro que aqui, estamos presumindo que há apenas uma CPU (um núcleo).

Com o chaveamento rápido da CPU entre os processos, a taxa pela qual um processo realiza a sua computação não será uniforme e provavelmente nem reproduzível se os mesmos processos forem executados outra vez. Desse modo, processos não devem ser programados com suposições predefinidas sobre a temporização.

A ideia fundamental é que um processo é uma atividade de algum tipo. Ela tem uum programa, uma entrada, uma saída e um estado. Um único processador pode ser compartilhado por vários processos, com algum algoritmo de escalonamento sendo usado para determinar quando parar o trabalho em um processo e servir outro. Em comparação, um programa é algo que pode ser armazenado em disco sem fazer nada.

>Vale a pena observar que se um programa está sendo executado duas vezes, é contado como dois processos.

O fato de que dois processos em execução estão operando o mesmo programa não importa, eles são processo distintos. O sistema operacional pode ser capaz de compartilhar o código entre eles de maneira que apenas um cópia esteja na memória, mas isso é um detalhe técnico que não muda a situação conceitual de dois processos sendo executados.

---
## Criação de Processos

Sistemas operacionais precisam de alguma maneira para criar processos. Em sistemas para fins gerais, alguma maneira é necessária para criar e terminar processos, na medida do necessário, durante a operação.

Quatro eventos principais fazem com que os processos sejam cirados:

1. Inicialização do sistema.
2. Execução de uma chamada de sistema (syscalls) de criação de processo por um processo em execução.
3. Solicitação de um usuário para criar um novo processo.
4. Início de uma tarefa em lote.

Quando um sistema operacional é inicializado, uma série de processos é criada. Alguns desses processos são de primeiro plano, isto é, processos que interagem com usuários (humanos) e realizam trabalho para eles. Outros operam em segundo plano (**Background**) e não estão associados com usuários em particular, mas em vez disso têm alguma função específica.

Por exemplo, um processo de segundo plano pode ser projetado para aceitar e-mails, ficando inativo a maior parte do dia, mas subitamente entrando em ação quando chega um e-mail. Processos que ficam em segundo plano para lidar com algumas atividades, como e-mail, páginas da web, notícias, impressão e assim por diante, são chamados de **daemons**.

Além dos processos criados durante a inicialização do sistema, novos processos podem ser criados depois também. Muitas vezes, um processo em execução emitirá chamadas de sistema para criar um ou mais processos novos para ajudá-lo em seu trabalho. 

Criar processo novos é particularmente útil quando o trabalho a ser feito pode ser facilmente formulado em termos de vários processos relacionados, mas de outras forma interagindo de maneira independente. 

Por exemplo, se uma grande quantidade de dados está sendo buscada através de uma rede para processamento subsequente, pode ser conveniente criar um processo para buscar os dados e colocá-los em um local compartilhado de memória enquanto um segundo processo remove os itens de dados e os processa.

Em um multiprocessador, permitir que cada processo execute em um CPU diferente também pode fazer com que a tarefa seja realizada mais rápido.

Em sistemas interativos, os usuários podem começar um programa digitando um comando ou clicando duas vezes sobre um ícone. Cada uma dessas ações inicia um novo processo e executa nele o programa selecionado. Em sistemas UNIX baseados em comandos que executam X, o novo processo ocupa a janela na qual ele foi iniciado. No Windows, quando um processo é iniciado, ele não tem uma janela, mas ele pode criar uma (ou mais), e a maioria o faz. Em ambos os sistemas, os usuários têm múltiplas janelas abertas de uma vez, cada uma executando algum processo. Utilizando o mouse, o usuário pode selecionar uma janela e interagir com o processo, por exemplo, fornecendo a entrada quando necessário.

---

No UNIX, há apenas uma chamada de sistema para criar um novo processo: **fork**. Essa chamada cria um clone exato do processo que a chamou. Após o fork, os dois processos, o pai e o filho, tem a mesma imagem de memória, as mesmas variáveis de ambiente e os mesmos arquivos abertos. E isso é tudo. 

Normalmente, o processo filho então executa **execve** ou uma chamada de sistema similar para mudar sua imagem de memória e executar um novo programa. Por exemplo, quando um usuário digita um comando, por exemplo, *sort*, para o shell, este se bifurca gerando um processo filho, e o processo filho executa *sort*. O objetivo desse processo em dois passos é permitir que o processo filho manipule seus descritores de arquivos depois da fork, mas antes da execve, a fim de conseguir o redirecionamento de entrada padrão, saida padrão e erro padrão.

Tanto no sistema UNIX quanto no windows, após um processo ser criado, pai e filho tem os seus próprios espaços de endereços distintos. Se um dos dois processos muda uma palavra no seu espaço de endereço, a mudança não é visível para o outro processo. No UNIX, o espaço de endereço inicial do filho é uma cópia do espaço de endereço do pai, mas há definitivamente dois espaços de endereços distintos envolvidos; nenhuma memória para escrita é compartilhada.

Algumas implementações UNIX compartilham o programa de texto entre as duas, tende em vista que isso não pode ser modificado. Alternativamente, o filho pode compartlhar toda a memória do pai, mas nesse caso, a memória é compartilhada no sistema [[copy-on-wirte]], o que significa que sempre que qualquer uma das duas quiser modificar parte da memória, aquele pedaço de memória é explicitamente copiado primeiro para certificar-se de que a modificação ocorra em uma área de memória privada.

Novamente, nenhuma memória que pode ser escrita é compartilhada. É possível no entanto, que um processo recentemente criado compartilhe alguns de alguns dos outros recursos do seu criador, como **arquvoss abertos**. No windows, os espaços de endereçcos do pai e do filho são diferentes desde o início.

---

## Termino de Processos

Após um processo ter sido criado, ele começa a ser executado e realiza qualquer que seja seu trabalho. No entanto, nada dura pra sempre, nem mesmo os processos. Cedo ou tarde, o novo processo terminará, normalmente devido a uma das condições a seguir

**1. Saída normal** (volubtária).
**2. Erro fatal** (Involuntário).
**3. Saída por erro** (Voluntária).
**4. Morto por outro processo** (Involuntário).

A maioria dos processos terminam por terem realizado seus trabalhos. Quando um compilador termina de traduzir o programa dado a ele, o compilador executa uma chamada para dizer ao sistema operacional que ele terminou. Essa chamada é **exit()** em UNIX e **Exit-Process** no windows. Programas baseados em tela também dão suporte ao término voluntário. Processadores de texto, visualizadores da internet e programas similares sempre têm um ícone ou item no menu em que o usuário pode clicar para dizer ao processo para remover quaisquer arquivos temporários que ele tenha aberto e então concluí-lo.

A segunda razão pelo término é a que o processo descobre um erro fatal. Por exemplo, se um usuário digita o comando `cc foo.c`.

para compilar o programa foo.c e não existe esse arquivo, o compilador simplesmente anuncia esse fato e termina a execução. Processos interativos com base em tela geralmente não fecham quando parâmetros ruins são dados. Em vez disso, eles abrem uma caixa de diálogo e pedem ao usuário para tentar de novo.

