Hardcoded Test Data
=====================

**Descrição**

Dados utilizados nos testes estão codificados diretamente no corpo do teste, como usuários, senhas, urls e identificadores.

**Contexto de ocorrência**

Surge quando não são utilizados mecanismos como fixtures ou geração dinâmica de dados, e os valores são inseridos diretamente no código do teste. 

**Exemplo**

No seguinte exemplo, os dados do usuário estão codificados diretamente no teste, o que torna difícil a reutilização e manutenção do código:

.. code-block:: javascript

    it("should allow a visitor to sign-up, login, and logout", function () {
        const userInfo = {
            firstName: "Bob",
            lastName: "Ross",
            username: "PainterJoy90",
            password: "s3cret",
        };

        cy.getBySel("signup-first-name").type(userInfo.firstName);
        cy.getBySel("signup-last-name").type(userInfo.lastName);
        cy.getBySel("signup-username").type(userInfo.username);
        cy.getBySel("signup-password").type(userInfo.password);
        cy.getBySel("signup-confirmPassword").type(userInfo.password);

        cy.getBySelLike("bankName-input").type("The Best Bank");
        cy.getBySelLike("accountNumber-input").type("123456789");
        cy.getBySelLike("routingNumber-input").type("987654321");
    });


**Impacto na manutenibilidade e qualidade dos testes**

Torna os testes pouco reutilizáveis, difíceis de manter e frágeis a mudanças no ambiente.

**Estratégias de refatoração**

* :doc:`Dados de teste em Fixtures </refatoracao/dados-em-fixtures>`