
**Data:** 2025-10-10
**keyboards:** 
**links internos:** 
___

**A DDL é o conjunto de comandos responsável por criar, alterar e excluir a estrutura dos objetos do banco de dados. É com a DDL que se define o "esqueleto" onde os dados serão armazenados.**


- ==CREATE==: Utilizado para criar novos objetos, como banco de dados, tabelas, índices e views.
	- Exemplo (Criar tabela):

![[Pasted image 20251010150343.png]]


- ==ALTER==: MOdifica a estrutura de um objeto existente. Pode ser usado para adicionar, remover ou alterar colunas em uma tabela.

	- Exemplo (Adicionar coluna):

![[Pasted image 20251010150512.png]]

- ==DROP==: Remove permanentemente um objeto do banco de dados.
	- Exemplo (excluir tabela):

![[Pasted image 20251010150619.png]]

- ==TRUNCATE==: Remove todos os registros de uma tabela rapidamente, mas mantém a estrutura da tabela intacta. Diferente do ==DELETE==, geralmente não pode ser revertido.