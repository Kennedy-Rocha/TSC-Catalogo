Isole os Dados de Teste com Fixtures
=====================

**Definição**

Evite codificar diretamente dados como usuários, senhas ou identificadores dentro do código do teste. Substitua por arquivos fixtures (.json, .js ou .ts) armazenados em cypress/fixtures, acessados via ``cy.fixture()``.

**Exemplo prático**