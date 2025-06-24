On the Fly
=====================

**Descrição**

Dependência de dados ou funções externas, como scripts de geração de dados ou consultas diretas a banco de dados, que não são controlados pelo teste.

**Contexto de ocorrência**

Ocorre quando os testes são fortemente acoplados a dados gerados dinamicamente ou a componentes externos cuja alteração quebra os testes. 

**Exemplo**

No exemplo a seguir, temos um teste que depende de um usuário específico consultado diretamente do banco de dados durante a execução do teste.

.. code-block:: javascript

    it('deve permitir login e exibir o painel do usuário', () => {
        cy.task('buscarUsuarioNoBanco', { papel: 'admin' }).then((usuario) => {
            cy.login(usuario.username, 'admin123');
        });

        cy.contains('Bem-vindo de volta,').should('be.visible');
    });


**Impacto na manutenibilidade e qualidade dos testes**

Gera testes frágeis e suscetíveis a falhas não relacionadas diretamente à funcionalidade testada.

**Estratégias de refatoração**

* :doc:`Dados de teste em Fixtures </refatoracao/dados-em-fixtures>`