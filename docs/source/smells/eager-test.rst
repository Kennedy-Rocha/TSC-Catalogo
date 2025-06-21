Eager Test
=====================

**Descrição**

Único teste cobre muitos comportamentos diferentes de uma só vez. Ele é “ansioso” porque tenta verificar várias funcionalidades ou cenários em um só teste, em vez de separá-los de forma clara.

**Contexto de ocorrência**

Ocorre quando há acoplamento excessivo entre diferentes verificações, geralmente com múltiplos comandos ``should()`` encadeados ou quando um teste é escrito para cobrir uma ampla gama de casos de uso em vez de focar em um único comportamento.

**Exemplo**

No seguinte teste, temos um exemplo claro de um teste "ansioso". Ele cobre a criação de uma issue, validações de formulário e a verificação de que a issue foi criada com sucesso.

.. code-block:: javascript

    it('validates form and creates issue successfully', () => {
        cy.get(testid`modal:issue-create`).within(() => {
        cy.get('button[type="submit"]').click();
        cy.get(testid`form-field:title`).should('contain', 'This field is required');

        cy.selectOption('type', 'Story');
        cy.get('input[name="title"]').type('TEST_TITLE');
        cy.get('.ql-editor').type('TEST_DESCRIPTION');
        cy.selectOption('reporterId', 'Yoda');
        cy.selectOption('userIds', 'Gaben', 'Yoda');
        cy.selectOption('priority', 'High');

        cy.get('button[type="submit"]').click();
        });

        cy.get(testid`modal:issue-create`).should('not.exist');
        cy.contains('Issue has been successfully created.').should('exist');
        cy.location('pathname').should('equal', '/project/board');
        cy.location('search').should('be.empty');

        cy.contains(testid`list-issue`, 'TEST_TITLE')
        .should('have.descendants', testid`avatar:Gaben`)
        .and('have.descendants', testid`avatar:Yoda`)
        .and('have.descendants', testid`icon:story`);
    });


**Impacto na manutenibilidade e qualidade dos testes**

Viola o princípio da responsabilidade única, dificulta a detecção precisa de falhas e prejudica a rastreabilidade de problemas. Quando um teste falha, pode ser difícil identificar qual parte específica do comportamento esperado não foi atendida, levando a uma depuração mais complexa e demorada.

**Estratégias de refatoração**

* :doc:`Blocos it curtos </refatoracao/blocos-it-curtos>`