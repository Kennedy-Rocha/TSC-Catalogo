Assertion Roulette
=====================

**Descrição**

Múltiplas asserções encadeadas sem mensagens descritivas, dificultando a compreensão do que falhou.

**Contexto de ocorrência**

O Cypress permite encadeamento de asserções via should(), porém sem suporte a mensagens personalizadas, tornando os erros difíceis de rastrear quando ocorrem.

**Exemplo**

**Impacto na manutenibilidade e qualidade dos testes**

Reduz a clareza dos testes e aumenta o tempo necessário para depuração de falhas, pois não é possível identificar facilmente qual asserção falhou ou por quê. Isso pode levar a frustrações e atrasos na resolução de problemas, especialmente em testes complexos com múltiplas condições.

**Estratégias de refatoração**

* :ref:`Utilize cy.log() para Explicitar Verificações`
* :ref:`Divida Testes Longos em Blocos it Focados`