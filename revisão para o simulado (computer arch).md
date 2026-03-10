
# Tópicos:

- Evolução dos computadores (linha do tempo)
- Modelos arquiteturais (von neumann x Havard)
- CPU: ULA/UC, registradores e pipeline;
- Memória e hierarquia: cache, RAM e memória virtual.
- Representação da informação: decimal, binários e hexadecimal;
- Codificação de caracteres (ASCII);
- Sistemas operacionais: processos, memória e arquivos.
- Redes: Elementos, topologia e TCP/IP.


# Evolução dos computadores

- **Ábaco** - > calculadoras mecânicas - > cartões perfurados - > computadores eletrônicos
- **Gerações**: válvulas - > transitores - > circuitos integrados - > microprocessadores.
- **Pioneiros**: babbage, ada Lovalace, turing, von neumann.
- Do mainframe ao PC e aos dispositivos móveis; foco atual em nuvem e IA.


# Modelos Arquiteturais e Componentes

- Von Neumann: programa e dados na mesma memória (gargalo do barramento).
- Havard: memórias separadas (instruções vs dados) - Comum em microcontroladores.
- Componentes: CPU, memória. E/S, Barramentos (dados, endereços, controle)
- Controladores, drivers e DMA para E/S eficiente.

# CPU em datalhe

- UC (controle), ULA (cálculos), registradores (ultrarapidos), clock e pipeline.
- Ciclo de instrução: buscar -> decodificar -> executar -> escrever resultado
- ISA e arquiteturas: CISC (x86), RISC (ARM), RISC-V
- Multicores e paralelismo; hazerds em pipeline (estruturais, dados, controle).

# Memória e Hierarquia

- Hierarquia: registradores -> cache (L1/L2/L3) -> RAM -> SSd/HDD -> Nuvem.
- memorias principal (RAM) é volatil; ROM/Flash armazena firmware.
- Memoria virtual: paginação e swap.
- DDR1 -> DDR5: ganho de largura de banda e eficiência energética; SSD vs. HDD.

# Redes de computadores 

- Elementos: hosts, meios (cabos/fibra/rádio), dispositivos (switch/roteador), protocolos     (TCP/IP).
- Classificações: Lan, MAN, WAN; cabeada vs sem fio; domestica, academica, corporativa.
- Topologias:barreamento, anel, estrela, malha e hibrida.
- Integração com arquiteturas: cliente-servidor, P2P, cloud e computação distribuida.

# Sistemas operacionais - Funções e Tipos

- Funções: processos, memorias, arquivos, dispositivos, segurança e rede.
- Tipos: mono/multitarefa; mono/multiusuário; tempo real; servidor; móvel; embarcado.
- Conceitos: threads, IPC, escalonamento (FIFO, Round-robin, prioridades).
- Memória: paginação, segmentação, espaço de endereçamento e proteção.

# Codifição de caracteres (ASCII)

- ASCII: padrão histórico (0-255) para letras, dígitos e símbolos.
- Mapeamento binários <-> caractere usando pesos (128, 64, 32, 16, 8, 4, 2, 1).
- Ex.: 0100001 -> 'A' ; 01010010 01010101... -> Palavras inteiras.
- Ideia geral: dados textuais também são números binários.

# Representação da informação

- Bit e Byte; múltiplos (KB,MB,B,TB)
- Sistemas de numeração: decimal, binário hexadecimal.
- Conversões manuais: divisões sucessicas (->bin/hex) e pesos posicionais (-> dec).
- Aplicações: enderaçamento de memória, códigos de cores, compressão/ amarzenamento.

