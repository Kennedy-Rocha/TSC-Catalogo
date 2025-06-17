Duplicated Actions
=====================

**Descrição**

Sequências de comandos são repetidas em múltiplos testes, sem abstração adequada ou reutilização de código, levando a redundância e aumento do custo de manutenção.

**Contexto de ocorrência**

O modelo declarativo do Cypress, que concentra comandos dentro dos blocos it, favorece a repetição de ações comuns como login, navegação ou preenchimento de formulários em vários cenários de teste. Isso leva a uma duplicação desnecessária de código.

**Exemplo**

**Impacto na manutenibilidade e qualidade dos testes**

Aumenta o custo de manutenção e gera inconsistências quando uma alteração precisa ser aplicada em vários testes ao invés de um único local. Isso pode levar a falhas não detectadas se uma ação for alterada em um teste, mas não em outro, resultando em testes que passam incorretamente ou falham sem motivo aparente.

**Estratégias de refatoração**

* :ref:`Crie Comandos Reutilizáveis com Cypress.Commands.add()`