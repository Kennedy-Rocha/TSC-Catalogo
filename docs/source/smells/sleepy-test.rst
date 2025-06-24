Sleepy Test
=====================

**Descrição**

Uso excessivo de esperas fixas ``cy.wait()`` como solução para problemas de sincronização ou temporização.

**Contexto de ocorrência**

Ocorre quando os testes dependem de esperas fixas para garantir que a aplicação esteja pronta para interações, resultando em testes lentos e não determinísticos.

**Exemplo**

No exemplo a seguir, o teste utiliza `cy.wait(ms)` para aguardar as mudanças na aplicação.

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


**Impacto na manutenibilidade e qualidade dos testes**

Testes lentos, não determinísticos e suscetíveis a erros de timing, dificultando a identificação de falhas reais e aumentando o tempo de execução dos testes.

**Estratégias de refatoração**

* :doc:`Espera condicional </refatoracao/espera-condicional>`