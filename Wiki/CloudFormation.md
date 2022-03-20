# CloudFormation

​	Um serviço que ajuda você a modelar e configurar seus recursos da AWS, para que você gaste menos tempo gerenciando esses recursos e mais tempo se concentrando nas aplicações executadas na AWS.

​	Você cria um modelo que descreve todos os recursos da AWS que você deseja (como funções do Amazon EC2 e tabelas do Amazon RDS) e o CloudFormation cuida do provisionamento e da configuração desses recursos para você.

​	Não é necessário criar e configurar individualmente os recursos da AWS e descobrir o que depende do que; o CloudFormation lida com isso.

## Utilidade

### Simplificar o gerenciamento de infraestrutura

Para uma aplicação Web escalável que também inclui um banco de dados de backend, é possível usar um grupo do Auto Scaling, um balanceador de carga do Elastic Load Balancing e uma instância de banco de dados do Amazon Relational Database Service.

### Replicar sua infraestrutura com rapidez

Se o seu aplicativo requer mais disponibilidade, é possível replicá-lo em várias regiões, de forma que se uma região se tornar indisponível, os usuários ainda podem usar o aplicativo em outras regiões.

### Controlar e rastrear alterações em sua infraestrutura com facilidade

Em alguns casos, você pode ter recursos subjacentes que deseja atualizar de forma incremental.

## Como o AWS CloudFormation funciona?

![img](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/images/create-stack-diagram.png)

As **chamadas que o CloudFormation faz são todas declaradas por seu modelo**. Por exemplo, suponha que você tem um modelo que descreve uma instância EC2 com um tipo de instância `t2.micro`. Quando você usa esse modelo para criar uma pilha,CloudFormation chama a API de criação de instância Amazon EC2 e especifica o tipo de instância como`t2.micro`.

### Atualizar uma pilha com conjuntos de alterações

## ![img](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/images/update-stack-diagram.png)Resiliencia

Se houver falha na criação da pilha, o CloudFormation reverterá as alterações excluindo os recursos que ele criou.

## O Modelo

```
{
  "AWSTemplateFormatVersion" : "version date",

  "Description" : "JSON string",

  "Metadata" : {
    template metadata
  },

  "Parameters" : {
    set of parameters
  },
  
  "Rules" : {
    set of rules
  },

  "Mappings" : {
    set of mappings
  },

  "Conditions" : {
    set of conditions
  },

  "Transform" : {
    set of transforms
  },

  "Resources" : {
    set of resources
  },
  
  "Outputs" : {
    set of outputs
  }
}
```

## Seções do modelo

Os modelos incluem várias seções principais. A seção `Resources` é a única seção necessária. Algumas seções em um modelo podem ser em qualquer ordem. No entanto, à medida que você cria o modelo, pode ser útil usar a ordem lógica da lista a seguir, porque valores em uma seção podem fazer referência a valores de uma seção anterior.

- **[Format Version (opcional)](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/format-version-structure.html)**

  A versão do modelo do AWS CloudFormation com a qual o modelo está em conformidade. A versão do formato do modelo não é a mesma que a versão da API ou da WSDL. A template format version pode ser alterada independentemente das versões da API e da WSDL.

- **[Description (opcional)](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/template-description-structure.html)**

  Uma sequência de texto que descreve o modelo. Esta seção deve sempre seguir a seção template format version.

- **[Metadata (opcional)](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/metadata-section-structure.html)**

  Os objetos que fornecem informações adicionais sobre o modelo.

- **[Parameters (opcional)](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html)**

  Os valores a serem passados para seu modelo em tempo de execução (ao criar ou atualizar uma pilha). Você pode fazer referência a parâmetros nas seções `Resources` e `Outputs` do modelo.

- **[Rules (opcional)](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/rules-section-structure.html)**

  Valida um parâmetro ou uma combinação de parâmetros repassados para um modelo durante uma criação de pilha ou atualização de pilha.

- **[Mappings (opcional)](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/mappings-section-structure.html)**

  Um mapeamento de chaves e valores associados que você pode usar para especificar valores de parâmetros condicionais, semelhante a uma tabela de pesquisa. Você pode vincular uma chave a um valor correspondente usando a função intrínseca [Fn::FindInMap](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-findinmap.html) nas seções `Resources` e `Outputs`.

- **[Conditions (opcional)](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/conditions-section-structure.html)**

  As condições que controlam se determinados recursos são criados ou se determinadas propriedades de recursos são atribuídas a um valor durante a criação ou a atualização da pilha. Por exemplo, condicionalmente, você pode criar um recurso que depende de se a pilha é de um ambiente de teste ou de produção.

- **[Transform (opcional)](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/transform-section-structure.html)**

  Em [aplicativos sem servidor](https://docs.aws.amazon.com/lambda/latest/dg/deploying-lambda-apps.html) (também chamados de aplicativos baseados no Lambda), especifique a versão do [AWS Serverless Application Model (AWS SAM)](https://github.com/awslabs/serverless-application-specification) a ser usada. Quando você especifica uma transformação, você pode usar a sintaxe AWS SAM para declarar recursos em seu modelo. O modelo define a sintaxe que você pode usar e como ela é processada.Você também pode usar transformações `AWS::Include` para trabalhar com trechos de modelos que são armazenados separadamente do modelo principal do AWS CloudFormation. Você pode armazenar seus arquivos de trechos em um bucket do Amazon S3 e, em seguida, reutilizar as funções em vários modelos.

- **[Resources (obrigatório)](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/resources-section-structure.html)**

  Especifica os recursos da pilha e suas propriedades, como uma instância do Amazon Elastic Compute Cloud ou um bucket do Amazon Simple Storage Service. Você pode fazer referência a recursos nas seções `Resources` e `Outputs` do modelo.

- **[Outputs (opcional)](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/outputs-section-structure.html)**

  Descreve os valores que são retornados sempre que você visualiza as propriedades da pilha. Por exemplo, você pode declarar uma saída para o nome de um bucket do S3 e, em seguida, chamar o comando da `aws cloudformation describe-stacks`AWS CLI para visualizar o nome.