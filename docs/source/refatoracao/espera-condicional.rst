Adote Esperas Condicionais
=====================

**Definição**

Evite o uso de comandos de espera fixa como ``cy.wait(5000)``, que introduzem dependência temporal artificial e fragilizam o teste. Substitua por comandos de espera automática ou condicional oferecidos pelo Cypress, como ``cy.get(selector).should(...)``, que aguardam o estado correto do elemento antes de prosseguir.

**Exemplo prático**