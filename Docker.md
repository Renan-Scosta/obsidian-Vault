
**Data:** 2026-01-07
**keyboards:** 
**links internos:** 
___
# Docker

O Docker é um software que serve pra criar, implantar e executar aplicações em ambientes isolados e seguros chamados **Contêineres**. Ele surgiu como uma evolução das Máquinas Virtuais (VMs) para resolver problemas de gerenciamento de recursos, permitindo que várias aplicações rodem no mesmo hardware de forma leve e escalável.

1. **Imagens**: São arquivos de metadados que funcionam como uma "receita de bolo" ou um executável da aplicação, contendo apenas as bibliotecas e dependências essenciais.

2. **Conteiners**: São as instâncias em execução da imagem, funcionando como "caixas" onde a aplicação roda de forma protegida.

3. **Docker Deamon**: É o ambiente controlado que gerencia e executa os contêineres no OS.

4. **Docker hub**: É uma biblioteca pública (repositório) onde mepresas e devs disponibilizam imagens pré-prontas para serem baixadas e usadas.

5. **Volumes**: Como os contêineres são efêmeros (os dados somem se fechar), os volumes servem para **persistir dados e informações** fora do contêiner.

Embora o Docker seja execelente para o desenvolvimento por usa praticidade e velocidade, as fontes indicam que é preciso cuidado ao usa-lo em **produção**, especialmente no que diz respeito à persistência de dados em volume, que podem não oferecer toda a estrutura de um banco de dados instalado nativamente.




# VMs  vs.  Docker (contêiners)

A evolução da infraestrutura de softaware passou de servidores físicos para máquinas virtuais e, finalmente, para a conteinerização, buscando resolver problemas de **gerenciamento de recursos e escalabilidade**. 


#### Máquinas Virtuais:

As máquinas virtuais surgiram para resolver a dificuldade de manter servidores físicos onde tudo era acoplado e o gerenciamento de recursos era inexistente.

A estrutura funciava assim:

- Uma VM roda sobre um hardware (bare metal) e um istema operacional raiz (host). Nela, utiliza-se um **KVM** (Kernal Virtual Machine), que subdivide o hardware em várias máquinas menores.

![[Pasted image 20260107133358.png]]


Cada VM era basicamente um "novo computador" vistualizaado que possui seu **próprio sistema operacional completo** (como windows ou linux) e *todas as bibliotecas necessárias para rodar uma aplicação*.

O principal problema é o **alto consumo de recurso**. como cada VM exige um sistema operacional inteiro e o download de muitas bibliotecas redundantes (que muitas vezes não usará), elas exigem hardwares extremamente potentes e caros para escalar.


#### Conteiners (Docker):

O Docker surge como um substituto ou evolução das VMs, focando em suprir as falhas de eficiência e execesso de peso das máquinas virtuais.

A estrutura funciona assim:

- Assim como a VM, existe o hardware para rodar o sistema operacional base. No entanto, em vez do KVM, utiliza-se o **Docker Daemon**.

![[Pasted image 20260107134357.png]]


O conteiner não virtualiza um hardware para rodar um OS completo; Ele cira um ambiente seguro que utiliza **o mínimo de recursos possíveis** do sistema anfitrião. Você baixa apenas a **imagem** exata (um executável) da aplicação com as estritamente necessárias para ela rodar.


