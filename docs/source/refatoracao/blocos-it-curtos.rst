Divida Testes Longos em Blocos ``it`` Focados
=====================

**Definição**

Evite agrupar múltiplas verificações e fluxos em um único bloco ``it``, o que gera acoplamento excessivo e testes difíceis de depurar. Substitua por múltiplos blocos ``it``, cada um responsável por testar um único comportamento ou cenário.

**Exemplo prático**

No exemplo a seguir, podemos aplicar a estratégia de refatoração para melhorar a clareza do teste.

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

Podemos dividir o teste em blocos ``it`` menores, cada um focado em uma parte específica do fluxo de criação de issue:

.. code-block:: javascript

    it('shows validation messages when submitting empty form', () => {
        cy.get(testid`modal:issue-create`).within(() => {
            cy.get('button[type="submit"]').click();
            cy.get(testid`form-field:title`).should('contain', 'This field is required');
        });
    });

    it('creates issue successfully with valid data', () => {
        cy.get(testid`modal:issue-create`).within(() => {
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
