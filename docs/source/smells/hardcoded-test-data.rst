Hardcoded Test Data
=====================

**Descrição**

Dados utilizados nos testes estão codificados diretamente no corpo do teste, como usuários, senhas, urls e identificadores.

**Contexto de ocorrência**

Surge quando não são utilizados mecanismos como fixtures ou geração dinâmica de dados, e os valores são inseridos diretamente no código do teste. 

**Exemplo**

**Impacto na manutenibilidade e qualidade dos testes**

Torna os testes pouco reutilizáveis, difíceis de manter e frágeis a mudanças no ambiente.

**Estratégias de refatoração**

* :ref:`Isole os Dados de Teste com Fixtures`