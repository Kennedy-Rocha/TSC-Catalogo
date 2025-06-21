Crie Comandos Reutilizáveis com ``Cypress.Commands.add()``
=====================

**Definição**

Evite repetir blocos de código semelhantes (ex.: login, preenchimento de formulários, navegações) em diversos testes. Substitua por comandos personalizados definidos em cypress/support/commands.js, encapsulando ações repetitivas.

**Exemplo prático**

No exemplo a seguir, podemos aplicar a estratégia de refatoração para melhorar a clareza do teste.

.. code-block:: javascript

    describe('Click to change', () => {
    beforeEach(() => {
        cy.visit('/docs/examples/clickToChange/');

        cy.get('.BrainhubCarouselItem--active')
        .children('img')
        .should('have.attr', 'src')
        .and('contain', 'mona');
    });

    it('allows to change slide when clicks on the next slide', () => {
        cy.get('.BrainhubCarouselItem')
        .eq(1)
        .trigger('mousedown')
        .wait(10)
        .trigger('mouseup', { force: true });

        cy.get('.BrainhubCarouselItem--active')
        .children('img')
        .should('have.attr', 'src')
        .and('contain', 'scream');
    });

    it('allows to change slide when clicks on the previous slide', () => {
        cy.get('.BrainhubCarouselItem')
        .eq(1)
        .trigger('mousedown')
        .wait(10)
        .trigger('mouseup', { force: true });

        cy.get('.BrainhubCarouselItem')
        .eq(0)
        .trigger('mousedown')
        .wait(10)
        .trigger('mouseup', { force: true });

        cy.get('.BrainhubCarouselItem--active')
        .children('img')
        .should('have.attr', 'src')
        .and('contain', 'mona');
    });
    });

No arquivo cypress/support/commands.js, adicione:

.. code-block:: javascript

    Cypress.Commands.add('clickCarouselSlide', (index) => {
    cy.get('.BrainhubCarouselItem')
        .eq(index)
        .trigger('mousedown')
        .wait(10)
        .trigger('mouseup', { force: true });
    });

    Cypress.Commands.add('assertActiveSlideImage', (expectedSubstring) => {
    cy.get('.BrainhubCarouselItem--active')
        .children('img')
        .should('have.attr', 'src')
        .and('contain', expectedSubstring);
    });

Agora, o teste pode ser simplificado para:

.. code-block:: javascript

    describe('Click to change', () => {
    beforeEach(() => {
        cy.visit('/docs/examples/clickToChange/');
        cy.assertActiveSlideImage('mona');
    });

    it('allows to change slide when clicks on the next slide', () => {
        cy.clickCarouselSlide(1);
        cy.assertActiveSlideImage('scream');
    });

    it('allows to change slide when clicks on the previous slide', () => {
        cy.clickCarouselSlide(1);
        cy.clickCarouselSlide(0);
        cy.assertActiveSlideImage('mona');
    });
    });

Dessa forma, o código fica mais limpo e fácil de entender, com ações repetitivas encapsuladas em comandos reutilizáveis. Isso melhora a legibilidade e a manutenção dos testes, além de reduzir a duplicação de código.