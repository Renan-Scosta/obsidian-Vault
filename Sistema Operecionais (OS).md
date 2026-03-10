
**Data:** 2025-08-27
**keyboards:** 
**links internos:** 
___

### Definição de sistema operacional:

- Software de sistema essencial do computador
- faz a interface entre hardware e usuário
- controla recursos fisico e lógicos
- controla


### Papel central do S.O

- coordena o uso do processador e memoria
- controla dispositivos de entrada/saida
- Oferece ambiente seguro para aplicativos
- Exemplo: sme SO, usuário precisaria enviar instruções diretas em liguangem de máquina.

### Arquitetura Geral em um SO

- Camadas principais:
	- Hardware
	- Núcleo (kernel)
	- Chamadas de sistema
	- Aplicações de usuário


### Funções de Sistema Operacional

- Gerenciamento de processos 
- Gerenciamento de memória
- Gerenciamento de Arquivos 
- Gerenciamento de Dispositivos
- Interface com Usuário.


### Gerenciamento de Hardware

- Controle de CPU, RAM, HD, GPU
- Drivers como intermediários
- alocação eficiente de recursos

![[Pasted image 20250827192012.png]]



### Interface com Usuário:

- CLI (Command Line interface) -> ex: MS-DOS, Bash
- GUI (Graphival User Interface) -> ex : Windows, macOS
- Tendência: Interfaces hibridas (toques + gestos + graficos)

### Controles de programas

- Execução de múltiplas applicações
- prevenção de conflitos
- Isolamento de processos
- Comunicação entre processos.


### Segurança e proteção:

- Controle de acesso por usuário
- Criptografia de dados
- Auditoria e monitoramento
- Firewall integrado em alguns OS


### Rede e comunicação:

- Gerenciamento de conexões TCP/IP
- Compartilhamento de arquivos/impressoras
- Comunicação cliente-servidor


### Virtualização e Multiplataforma:

- OS hospedeiro e convidado (VMware, VirtualBox)
- Contêineres(Docker, Kubernetes)
- Suporte multiplataforma (Windoes subsystem for Linux).


### Resumos das funções:

- Coordenação de Hardware
- Ambiente de execução
- Proteção e segurança
- Suporte à conectividade e virtualização


### Tipos de Sistemas Operacionais 

#### Classificação geral:

- Quanto às tarefas
- quanto aos usuários
- Quanto a arquitetura
- Quanto à aplicação (desktop, servidor, móvel, embarcado)


### OS Monotarefa

- Executa apenas uma aplicação por vez
- Exemplo: MS-DOS
- Simples, mas limitado


### OS Multitarefa:

- Executa várias aplicações simultaneamente
- Controle de tempo de CPU
- Exemplo: Windows, Linux


### OS monousuário:

- Suporta apenas um usuário ativo por vez
- Exemplo: versões antigas do windows.

### OS Multiusuário:

- Permite vários usuários ao mesmo tempo
- Compartilhamento de recursos
- Exemplo: Unix, servidores linux


### OS de tempo real:

- Respostas imediata e prvisível
- Usado em controle industrial, aviação, saúde
- Exemplo: VxWorks, QNX
- Comum em sistemas embarcados.

### OS de servidor:

- Foco em estabilidade, escalabilidade e segurança
- Exemplo: Windows Server, Red hat Enterprises Linux
- Usados em data centes e nuvem

### OS Embarcados e Móveis:

- Em dispositivos específicos: smartphones, TVs, eletrodométicos
- Exemplo: Android, IOS, HarmonyOS
- Exemplo de embarcados: RTOS em carros e eletrodomésticos inteligentes.


### Gerenciamento de Processos:

#### O que é um processo?

- Programa em execução
- Unidade fundamental de trabalho do OS
- Pode conter Múltiplas threads


### Estado de um processo

- Novo
- Pronto
- Em execução
- Em espera
- Finalizado


### Escalanomento de Processos:

- FIFO (First In, First Out)
- Round Robin (tempo de fatia)
- Prioridades
- Objetivo: equilibrio entre desempenho e Justiça


### Comunicções entre Processos (IPC)

- Pipes
- Sinais
- Memória compartilhada
- Mensagens


### Threads:

- Unidade menor que o processo
- Compartilham espaço de memoria
- Benefícios: desempenho e paralelismo

### Deadlock:

- Situação em que processos ficam bloqueados mutualmente
- Condições para ocorrer: Exclusão mútua, espera circular
- Estratégias de prevenção

### Conceito de memória no OS:

- Recurso limitado e crítico
- Impact diretamente o desempenho
- Tipos: RAM, cache, memória virtual

![[Pasted image 20250827200924.png]]


### Alocação de memória:

- Contígua vs não Contígua
- Partisionamento fixo e dinâmico


### Paginação:

- Divide memória em blocos (págians)
- Mapeamento lógico -> Físico
- Vantagem: reduz fragmentação


### Segmentação:

- Divisão lógica em segmentos (Códigos, dados, pilha)
- Maior flexibilidade que paginação


### Memória virtual:

- Uso de Hd como entensão da RAM
- Arquivo de paginação (**swap**)
- Permite executar programas maiores que a memória física


### Conceito de arquivo

- Conjunto organizado de dados
- Identificação por nome + extensão
- Manipulando via sistemas de arquivos


### Estrutura de diretórios

- Hierarquia em árvore
- Raiz -> subpastas -> arquivos
- Exemplos: c:\ (Windows),/home(Linux)


### Sistemas de arquivos:

- FAT32: Simples, compatível, mas limitado
- NTFS: Moderno, Seguro, usado no Windows
- EXT4: Padrão em linux
- APFS: Usado em sistemas Apple


### Permissões de arquivos:

- Leitura(R), Escrita (W), Execução (X)
- Conmtrole por usuário e grupo
- Exemplo: chmod no linux


### Tendências em OS:

- Computadores em nuvem
- OS minimalistas (contêiners)
- Integrações com IA e assistentes Virtuais


### Exemplos de Uso Atual:

- Desktop (Windows, MacOS, Linux)
- Servidores (Linux, Windows server)
- SmartPhones (Android, IOS)
- IoT(OS embarcados)


### Recapitulando:

- OS = software base do computador
- Funções: processos, memória, arquivos, dispositivos
- Classificações: Mono/Multitarefa, mono.
