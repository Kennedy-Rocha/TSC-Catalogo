Eager Test
=====================

**Descrição**

Único teste cobre muitos comportamentos diferentes de uma só vez. Ele é “ansioso” porque tenta verificar várias funcionalidades ou cenários em um só teste, em vez de separá-los de forma clara.

**Contexto de ocorrência**

Ocorre quando há acoplamento excessivo entre diferentes verificações, geralmente com múltiplos comandos should() encadeados ou quando um teste é escrito para cobrir uma ampla gama de casos de uso em vez de focar em um único comportamento.

**Exemplo**

**Impacto na manutenibilidade e qualidade dos testes**

Viola o princípio da responsabilidade única, dificulta a detecção precisa de falhas e prejudica a rastreabilidade de problemas. Quando um teste falha, pode ser difícil identificar qual parte específica do comportamento esperado não foi atendida, levando a uma depuração mais complexa e demorada.

**Estratégias de refatoração**