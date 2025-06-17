Sleepy Test
=====================

**Descrição**

Uso excessivo de esperas fixas cy.wait() como solução para problemas de sincronização ou temporização.

**Contexto de ocorrência**

Ocorre quando os testes dependem de esperas fixas para garantir que a aplicação esteja pronta para interações, resultando em testes lentos e não determinísticos.

**Exemplo**

**Impacto na manutenibilidade e qualidade dos testes**

Testes lentos, não determinísticos e suscetíveis a erros de timing, dificultando a identificação de falhas reais e aumentando o tempo de execução dos testes.

**Estratégias de refatoração**

* :ref:`Adote Esperas Condicionais`