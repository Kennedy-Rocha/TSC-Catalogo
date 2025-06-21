Duplicated Actions
=====================

**Descrição**

Sequências de comandos são repetidas em múltiplos testes, sem abstração adequada ou reutilização de código, levando a redundância e aumento do custo de manutenção.

**Contexto de ocorrência**

O modelo declarativo do Cypress, que concentra comandos dentro dos blocos ``it``, favorece a repetição de ações comuns como login, navegação ou preenchimento de formulários em vários cenários de teste. Isso leva a uma duplicação desnecessária de código.

**Exemplo**

No seguinte trecho de código, observamos que a ação de clicar em um slide para alterá-lo, e a validação da imagem, são repetidos em ambos os testes. Mudando apenas os valores utilizados em cada um. Caracterizando o smell descrito.

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

**Impacto na manutenibilidade e qualidade dos testes**

Aumenta o custo de manutenção e gera inconsistências quando uma alteração precisa ser aplicada em vários testes ao invés de um único local. Isso pode levar a falhas não detectadas se uma ação for alterada em um teste, mas não em outro, resultando em testes que passam incorretamente ou falham sem motivo aparente.

**Estratégias de refatoração**

* :doc:`Comandos reutilizáveis </refatoracao/comandos-reutilizaveis>`