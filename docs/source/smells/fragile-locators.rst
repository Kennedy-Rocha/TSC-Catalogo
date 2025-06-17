Fragile Locators
=====================

**Descrição**

Uso de seletores frágeis e sensíveis a mudanças na estrutura do DOM ou nos estilos CSS.

**Contexto de ocorrência**

Ocorre quando são utilizados seletores baseados em classes dinâmicas, hierarquias profundas ou elementos pouco estáveis, tornando os testes suscetíveis a quebras frequentes devido a mínimas alterações na interface do usuário.

**Exemplo**

**Impacto na manutenibilidade e qualidade dos testes**

Aumenta significativamente o custo de manutenção, uma vez que alterações na interface frequentemente quebram os testes e exigem atualizações constantes dos seletores. Isso pode levar a uma falsa sensação de falhas nos testes, mesmo quando a funcionalidade não foi alterada.

**Estratégias de refatoração**

* :doc:`Seletores Exclusivos </refatoracao/seletores-exclusivos>`