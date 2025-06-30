Nomeie Testes e Blocos com Clareza e Consistência
=====================

**Definição**

Evite usar nomes genéricos ou ambíguos como Test1, Verifica algo, ou CheckPage. Substitua por descrições específicas que reflitam o comportamento esperado, tanto em ``describe``, ``it``, quanto em funções auxiliares.

**Exemplo prático**

No exemplo a seguir, podemos aplicar a estratégia de refatoração para melhorar a clareza do teste.

.. code-block:: javascript

    describe('Click to change', () => {
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
    });
    // Teste em português
    describe('Clique para mudar', () => {
        it('permite mudar o slide quando clica no próximo slide', () => {
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
    });

Podemos substituir nomes vagos por nomes mais descritivos, que indiquem claramente o que está sendo testado:

.. code-block:: javascript

    describe('Image Carousel Navigation', () => {
        it('should advance to the next slide when the next slide is clicked', () => {
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
    });
    // Teste em português
    describe('Navegação do Carrossel de Imagens', () => {
        it('deve avançar para o próximo slide ao clicar nele', () => {
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
    });