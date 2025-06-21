Utilize ``cy.log()`` para Explicitar Verificações
=====================

**Definição**

Evite realizar múltiplas asserções consecutivas utilizando apenas ``should()``, sem qualquer indicação do que está sendo verificado, especialmente porque o Cypress não permite a inclusão de mensagens explicativas diretamente nas asserções. Substitua por chamadas explícitas a ``cy.log()``, imediatamente antes de cada asserção, informando de forma clara qual comportamento está sendo validado.

**Exemplo prático**

No exemplo a seguir, podemos aplicar a estratégia de refatoração para melhorar a clareza do teste.

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

Adicionando logs para explicitar as verificações, o código ficaria assim:

.. code-block:: javascript

  it('edits a comment successfully', () => {
    cy.log('Abre o modal de detalhes da issue');
    getIssueDetailsModal().within(() => {

      cy.log('Clica em "Edit" e verifica que o botão desaparece');
      cy.get(testid`issue-comment`)
        .contains('Edit')
        .click()
        .should('not.exist');

      cy.log('Verifica que o campo de texto contém o comentário original');
      cy.get('textarea[placeholder="Add a comment..."]')
        .should('have.value', 'Comment body');

      cy.log('Atualiza o conteúdo do comentário');
      cy.get('textarea[placeholder="Add a comment..."]')
        .clear()
        .type('TEST_COMMENT_EDITED');

      cy.log('Clica em "Save" e verifica que o botão desaparece');
      cy.contains('button', 'Save')
        .click()
        .should('not.exist');

      cy.log('Verifica que o comentário atualizado aparece com o botão "Edit"');
      cy.get(testid`issue-comment`)
        .should('contain', 'Edit')
        .and('contain', 'TEST_COMMENT_EDITED');

    });
  });

Importante: Comentários adicionados em português para facilitar o entendimento deste artigo, mas em caso real deve seguir o idioma que o projeto utiliza.