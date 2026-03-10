
**Data:** 2025-11-05
**keyboards:** 
**links internos:** 
___

O Single Responsibility Principle (SRP), ou Princípio da Responsabilidade Única, é basicamente o "S" do acrônimo SOLID.

A definição chique é: "Uma classe deve ter apenas um, e somente um, motivo para mudar."

Em bom português: cada classe deve fazer UMA coisa e fazer BEM.

Pense em um canivete suíço. Ele faz 10 coisas, mas não faz nenhuma delas perfeitamente. O SRP diz para você parar de criar "classes canivete suíço" no seu código.

Por que isso é importante?
Se sua classe Funcionario faz tudo—calcula o salário, salva no banco de dados E gera um relatório em PDF—você tem um problema.

Se o contador pedir uma mudança no cálculo do salário, você vai mexer na classe.

Se o DBA pedir uma mudança no banco de dados, você vai mexer na mesma classe.

Se o gerente pedir uma mudança no layout do PDF, adivinha? Você vai mexer na mesma classe de novo.

Isso é ruim porque:

É frágil: Ao mudar o PDF, você pode quebrar o cálculo do salário sem querer.

É difícil de testar: Testar uma classe que faz 10 coisas é um pesadelo.

É difícil de reutilizar: Você só queria usar o cálculo de salário em outro lugar, mas agora é obrigado a levar junto a lógica do PDF e do banco de dados.