Adote Esperas Condicionais
=====================

**Definição**

Evite o uso de comandos de espera fixa como ``cy.wait(5000)``, que introduzem dependência temporal artificial e fragilizam o teste. Substitua por comandos de espera automática ou condicional oferecidos pelo Cypress, como ``cy.get(selector).should(...)``, que aguardam o estado correto do elemento antes de prosseguir.

**Exemplo prático**

No exemplo a seguir, podemos aplicar a estratégia de refatoração para melhorar a clareza do teste.

.. code-block:: javascript
    it('repeats slides when swipes right', () => {
        for (let i = 0; i < 17; i++) {
            cy.get('.BrainhubCarousel__arrowRight').trigger('click');

            cy.wait(5);
        }

        cy.wait(20);

        cy.get('.BrainhubCarouselItem--active')
            .children('img')

            .should('have.attr', 'src')
            .and('contain', 'starry-night');
    });

Podemos substituir as esperas fixas por esperas condicionais, em vez de esperar um tempo fixo, podemos aguardar que o elemento esteja ativo e visível antes de prosseguir.

.. code-block:: javascript
    it('repeats slides when swipes right', () => {
        for (let i = 0; i < 17; i++) {
            cy.get('.BrainhubCarousel__arrowRight')
            .click();

            cy.get('.BrainhubCarouselItem--active')
            .should('exist');
        }

        cy.get('.BrainhubCarouselItem--active')
            .children('img')
            .should('have.attr', 'src')
            .and('contain', 'starry-night');
    });
