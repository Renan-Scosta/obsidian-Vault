
**Data:** 2025-10-10
**keyboards:** 
**links internos:** 
___

**A TCL gerencia as transações no banco de dados, garantindo a integridade dos dados ao agrupar uma sequência de operações em uma única lógica de trabalho**. 

- ==COMMIT==: Salva permanentemente todas as alterações realizadas durante a transação atual.
- ==ROLLBACK==: Desfaz todas as alterações realizadas na transação atual, revertendoo banco de dados para o estado em que se encontrava antes do inicio da transação.
- ==SAVEPOINT==: Cria um ponto de salvamento dentro de uma transação, para o qual é possivel reverter posteriormente sem desfazer a transação inteira.
