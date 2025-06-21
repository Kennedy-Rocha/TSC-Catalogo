Assertion Roulette
=====================

**Descrição**

Múltiplas asserções encadeadas sem mensagens descritivas, dificultando a compreensão do que falhou.

**Contexto de ocorrência**

O Cypress permite encadeamento de asserções via ``should()``, porém sem suporte a mensagens personalizadas, tornando os erros difíceis de rastrear quando ocorrem.

**Exemplo**

No exemplo a seguir, temos várias asserções e nenhuma indica, em tempo de execução, qual é o comportamento esperado ou o que está sendo validado. Se uma dessas falhar, o terminal do Cypress apenas exibirá que houve uma falha em algum ``should()``, mas não informará qual. 

.. code-block:: javascript

  it('edits a comment successfully', () => {
      getIssueDetailsModal().within(() => {
        cy.get(testid`issue-comment`)
          .contains('Edit')
          .click()
          .should('not.exist');

        cy.get('textarea[placeholder="Add a comment..."]')
          .should('have.value', 'Comment body')
          .clear()
          .type('TEST_COMMENT_EDITED');

        cy.contains('button', 'Save')
          .click()
          .should('not.exist');

        cy.get(testid`issue-comment`)
          .should('contain', 'Edit')
          .and('contain', 'TEST_COMMENT_EDITED');
      });
  });


**Impacto na manutenibilidade e qualidade dos testes**

Reduz a clareza dos testes e aumenta o tempo necessário para depuração de falhas, pois não é possível identificar facilmente qual asserção falhou ou por quê. Isso pode levar a frustrações e atrasos na resolução de problemas, especialmente em testes complexos com múltiplas condições.

**Estratégias de refatoração**

* :doc:`Validacões rotuladas </refatoracao/validacoes-rotuladas>`
* :doc:`Blocos it curtos </refatoracao/blocos-it-curtos>`