
**Data:** 2025-05-06
**keyboards:** 
**links internos:** 
___

# Descrição:

Em uma arquitetura monolítica, todos os componentes do gateway de pagamentos (processamentos de transações, gestão de usuários, comunicação com adquirentes, etc.) são construídos com uma única unidade.

# Vantagens:

- Simplicidade de desenvolvimento inicial e deploy.
- Gerenciamento centralizado.
- Ideal para MVPs (Produtos mínimos Viáveis) ou sistema de menor complexidade.


# Desvantagens: 

- Dificuldade de escalar componentes individualmente.
- Maior risco de um erro em um módulo afetar todo o sistema.
- Acoplamento forte entre os componentes, dificultando a manutenção e a evolução.
- Escalabilidade pode se tornar um gargalo com o aumento do volume de transações.