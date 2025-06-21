Isole os Dados de Teste com Fixtures
=====================

**Definição**

Evite codificar diretamente dados como usuários, senhas ou identificadores dentro do código do teste. Substitua por arquivos fixtures (.json, .js ou .ts) armazenados em cypress/fixtures, acessados via ``cy.fixture()``.

**Exemplo prático**

No exemplo a seguir, podemos aplicar a estratégia de refatoração para melhorar a clareza do teste.

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

Crie um arquivo fixture chamado `user.json` em `cypress/fixtures` com o seguinte conteúdo:

.. code-block:: json

    {
        "firstName": "Bob",
        "lastName": "Ross",
        "username": "PainterJoy90",
        "password": "s3cret",
        "bankName": "The Best Bank",
        "accountNumber": "123456789",
        "routingNumber": "987654321"
    }

Agora, modifique o teste para utilizar os dados do fixture:

.. code-block:: javascript

    it("should allow a visitor to sign-up, login, and logout", function () {
        cy.fixture("user").then((userInfo) => {
            cy.getBySel("signup-first-name").type(userInfo.firstName);
            cy.getBySel("signup-last-name").type(userInfo.lastName);
            cy.getBySel("signup-username").type(userInfo.username);
            cy.getBySel("signup-password").type(userInfo.password);
            cy.getBySel("signup-confirmPassword").type(userInfo.password);

            cy.getBySelLike("bankName-input").type(userInfo.bankName);
            cy.getBySelLike("accountNumber-input").type(userInfo.accountNumber);
            cy.getBySelLike("routingNumber-input").type(userInfo.routingNumber);
        });
    });