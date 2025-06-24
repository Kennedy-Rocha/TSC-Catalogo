Utilize Atributos de Teste para Seletores Estáveis
=====================

**Definição**

Evite utilizar seletores frágeis baseados em classes CSS, posições no DOM ou estruturas hierárquicas sensíveis a mudanças. Substitua por atributos como ``data-cy``, ``data-testid`` ou IDs exclusivos para cada elemento.

**Exemplo prático**

No exemplo a seguir, podemos aplicar a estratégia de refatoração para melhorar a clareza do teste.

.. code-block:: javascript
    it('should display current values in form', () => {
        cy.get('input[name="name"]').should('have.value', 'Project name');
        cy.get('input[name="url"]').should('have.value', 'https://www.testurl.com');
        cy.get('.ql-editor').should('contain', 'Project description');
        cy.selectShouldContain('category', 'Software');
    });

Podemos substituir os seletores frágeis por atributos de teste, tornando-os mais estáveis e menos suscetíveis a quebras:

.. code-block:: javascript
    it('should display current values in form', () => {
        cy.get('[data-cy="project-name"]').should('have.value', 'Project name');
        cy.get('[data-cy="project-url"]').should('have.value', 'https://www.testurl.com');
        cy.get('[data-cy="project-description"]').should('contain', 'Project description');
        cy.selectShouldContain('category', 'Software');
    });

Se ainda não existirem esses atributos, a recomendação é adicioná-los no código da aplicação, especificamente para fins de automação de testes.