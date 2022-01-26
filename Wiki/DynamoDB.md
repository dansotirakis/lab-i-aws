# Amazon DynamoDB

O Amazon DynamoDB é um serviço de banco de dados NoSQL de gestão completa que fornece um desempenho rápido e previsível com facilidade de escalabilidade. Um serviço de banco de dados NoSQL totalmente gerenciado que fornece uma performance rápida e previsível com escalabilidade integrada.

Permite excluir automaticamente os itens expirados das tabelas para ajudar você a reduzir o uso e o custo do armazenamento de dados que não são mais relevantes.

Oferece criptografia em repouso, o que elimina a carga e a complexidade operacionais envolvidas na proteção de dados confidenciais.

## Tabelas, itens e atributos

Estes são os componentes básicos do DynamoDB:

- **Tabelas**: semelhante a outros sistemas de banco de dados, o DynamoDB armazena dados em tabelas. Uma tabela é uma coleção de dados.
- **Items**: cada tabela contém zero ou mais itens. Um item é um grupo de atributos identificável exclusivamente entre todos os outros itens.
- **Atributos**: cada item é composto por um ou mais atributos. Um atributo é um elemento de dados fundamental, algo que não precisa ser dividido ainda mais.

## Aceleração na memória com o DynamoDB Accelerator (DAX)

Um serviço de armazenamento em cache compatível com o DynamoDB no qual você pode se beneficiar da rápida performance em memória para aplicações exigentes.

1. Como um cache na memória, o DAX reduz os tempos de resposta de workloads de leitura final consistente por uma ordem de magnitude que varia de milissegundos de um único dígito até microssegundos.

2. O DAX reduz a complexidade operacional e da aplicação fornecendo um serviço gerenciado que é compatível com a API do DynamoDB. Portanto, ele exige apenas alterações funcionais mínimas para uso com um aplicativo existente.

3. Para workloads de leitura intermitentes ou pesadas, o DAX fornece taxa de transferência mais alta e economia potencial de custos operacionais reduzindo a necessidade de provisionar unidades de capacidade de leitura em excesso. Isso é especialmente benéfico para aplicativos que exigem leituras repetidas para chaves individuais.

O DAX é compatível com a **criptografia do lado do servidor.**

O DAX também oferece suporte à **criptografia em trânsito**, garantindo que todas as solicitações e respostas entre a aplicação e o cluster sejam criptografadas por TLS (Transport Level Security) e que as conexões com o cluster possam ser autenticadas pela verificação de um certificado x509 de cluster.

### O DAX é ideal para os seguintes tipos de aplicações:

1. Aplicativos que exigem o melhor tempo de resposta possível para leituras.
2. Aplicativos que fazem a leitura de um pequeno número de itens com mais frequência do que outros.
3. Aplicativos que exigem leitura intensa, mas que também são sensíveis aos custos.
4. Aplicativos que exigem leituras repetidas em um grande conjunto de dados.

### O DAX não é ideal para os seguintes tipos de aplicação:

1. Aplicativos que exigem leituras fortemente consistentes
2. Aplicativos que não precisam de tempos de resposta em microssegundos
3. Aplicativos que exigem gravação intensa ou que não realizam muitas atividades de leitura.
4. Aplicações que já usam uma solução de armazenamento em cache

## DynamoDB Streams

- O DynamoDB Streams é um recurso opcional que captura eventos de modificação de dados em tabelas do DynamoDB. Os dados sobre esses eventos são exibidos no fluxo quase em tempo real e na ordem em que os eventos ocorreram. 
- Cada evento é representado por um registro de streaming. Se você habilitar um fluxo em uma tabela, o DynamoDB Streams gravará um registro de fluxo sempre que um dos seguintes eventos ocorrer.

O DynamoDB Streams é um recurso opcional que captura eventos de modificação de dados em tabelas do DynamoDB. Os dados sobre esses eventos são exibidos no fluxo quase em tempo real e na ordem em que os eventos ocorreram.

### Caso de uso:

Suponhamos que você queira enviar um e-mail de "boas-vindas" a cada novo cliente. Você pode habilitar um stream nessa tabela e depois associá-lo a uma função do Lambda. A função do Lambda seria executada sempre que um novo registro de streaming aparecesse, mas processaria apenas os novos itens adicionados à tabela *Customers*. Para qualquer item que tenha um atributo `EmailAddress`, a função do Lambda invocaria o Amazon Simple Email Service (Amazon SES) para enviar um e-mail a esse endereço.