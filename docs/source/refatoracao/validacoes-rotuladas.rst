Utilize ``cy.log()`` para Explicitar Verificações
=====================

**Definição**

Evite realizar múltiplas asserções consecutivas utilizando apenas ``should()``, sem qualquer indicação do que está sendo verificado, especialmente porque o Cypress não permite a inclusão de mensagens explicativas diretamente nas asserções. Substitua por chamadas explícitas a ``cy.log()``, imediatamente antes de cada asserção, informando de forma clara qual comportamento está sendo validado.

**Exemplo prático**