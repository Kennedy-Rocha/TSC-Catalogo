Bem vindo ao Catálogo - TSC: Catálogo de Test Smells em Cypress
===================================

Catálogo-TSC é um catálogo de Test Smells para Cypress, que são más práticas de teste que podem levar a testes frágeis e difíceis de manter. Além disso, o projeto oferece métodos de refatoração para evitar esses problemas.

Inicialmente, o catálogo conta com 10 Test Smells, que podem ser consultados juntamente com suas respectivas descrições e métodos de refatoração. O objetivo é ajudar desenvolvedores e equipes a identificar e corrigir problemas comuns em testes automatizados, melhorando a qualidade e a manutenibilidade dos testes.

Test Smells 
------------------------------


* :doc:`Assertion Roulette </smells/assertion-roulette>`
* :doc:`Duplicated Actions </smells/duplicated-actions>`
* :doc:`Eager Test </smells/eager-test>`
* :doc:`Fragile Locators </smells/fragile-locators>`
* :doc:`Hardcoded Test Data </smells/hardcoded-test-data>`
* :doc:`On the Fly </smells/on-the-fly>`
* :doc:`Sleepy Test </smells/sleepy-test>`
* :doc:`Unsuitable Naming </smells/unsuitable-naming>`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Test Smells

   /smells/assertion-roulette
   /smells/duplicated-actions
   /smells/eager-test
   /smells/fragile-locators
   /smells/hardcoded-test-data
   /smells/on-the-fly
   /smells/sleepy-test
   /smells/unsuitable-naming
   

Estratégias de refatoração
------------------------------

* :doc:`Espera condicional </refatoracao/espera-condicional>`
* :doc:`Dados de teste em Fixtures </refatoracao/dados-em-fixtures>`
* :doc:`Blocos it curtos </refatoracao/blocos-it-curtos>`
* :doc:`Seletores Exclusivos </refatoracao/seletores-exclusivos>`
* :doc:`Nomeação consistente</refatoracao/nomes-claros>`
* :doc:`Comandos reutilizáveis </refatoracao/comandos-reutilizaveis>`
* :doc:`Validacões rotuladas </refatoracao/validacoes-rotuladas>`


.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Estratégias de refatoração

   /refatoracao/espera-condicional
   /refatoracao/dados-em-fixtures
   /refatoracao/blocos-it-curtos
   /refatoracao/seletores-exclusivos
   /refatoracao/nomes-claros
   /refatoracao/comandos-reutilizaveis
   /refatoracao/validacoes-rotuladas
   