Stinky Synchronization
=====================

**Descrição**

Sincronização inadequada entre teste e aplicação, levando a testes instáveis.

**Contexto de ocorrência**

Ocorre quando comandos de espera são utilizados de forma incorreta, sem considerar o estado real dos elementos na interface. Realiza interações com a UI antes que o DOM esteja pronto ou que os elementos estejam visíveis.

**Exemplo**

**Impacto na manutenibilidade e qualidade dos testes**

Gera testes flaky, difíceis de reproduzir e de manter.

**Estratégias de refatoração**