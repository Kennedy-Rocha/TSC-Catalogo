Unsuitable Naming
=====================

**Descrição**

Uso de nomes pouco descritivos ou vagos nos testes, como ``Test1`` ou ``CheckSomething``.

**Contexto de ocorrência**

Aparece quando os nomes dos testes não refletem claramente o comportamento testado, estão vagos demais ou imprecisos, o que dificulta o entendimento e manutenção.

**Exemplo**

No exemplo abaixo, as nomeclaturas mesmo que não sendo genericas, não são claras o suficiente para entender o que está sendo testado:

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

**Impacto na manutenibilidade e qualidade dos testes**

Reduz a clareza, dificulta o entendimento do que está sendo validado e aumenta o tempo para manutenção e depuração dos testes.

**Estratégias de refatoração**

* :doc:`Nomeação consistente</refatoracao/nomes-claros>`
* :doc:`Blocos it curtos </refatoracao/blocos-it-curtos>`