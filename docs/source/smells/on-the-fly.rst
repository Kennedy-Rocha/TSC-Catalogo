On the Fly
=====================

**Descrição**

Dependência de dados ou funções externas, como scripts de geração de dados ou consultas diretas a banco de dados, que não são controlados pelo teste.

**Contexto de ocorrência**

Ocorre quando os testes são fortemente acoplados a dados gerados dinamicamente ou a componentes externos cuja alteração quebra os testes. 

**Exemplo**

**Impacto na manutenibilidade e qualidade dos testes**

Gera testes frágeis e suscetíveis a falhas não relacionadas diretamente à funcionalidade testada.

**Estratégias de refatoração**

* :ref:`Isole os Dados de Teste com Fixtures`