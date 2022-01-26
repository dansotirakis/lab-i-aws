# Lambda λ

Serviço computacional sem servidor que permite que você execute o código sem provisionar ou gerenciar servidores.

Você pode executar código para praticamente qualquer tipo de aplicação ou serviço de backend, tudo sem administração e pagar apenas pelo que usar.

O Lambda também oferece suporte ao processamento em ordem para filas FIFO (primeiro a entrar, primeiro a sair), aumentando a escala na vertical até o número de grupos de mensagens ativos.

É possível configurar a fila de origem para enviar itens para uma fila de mensagens mortas se eles não puderem ser processados.

O Lambda bloqueia conexões de rede de entrada. 

Embora você não possa invocar diretamente uma função do Lambda, outros serviços compatíveis podem invocar uma função.

## Funções

- Uma função do AWS Identity and Access Management (IAM) que concede à função permissão para acessar serviços e recursos da AWS.
- Você fornece essa função ao criar uma função, e o Lambda assume a função quando ela é invocada.
- As versões da função do Lambda são projetadas para gerenciar a implantação de funções,  podem ser usadas para alterações de código, sem afetar a versão de produção estável do código.

### Manipulador

- Toda função do Lambda precisa de um manipulador específico do Lambda. 
- As particularidades de criação variam entre os tempos de execução, mas todos eles compartilham um modelo de programação comum que define a interface entre o seu código e o código do tempo de execução. 
- Você informa ao tempo de execução qual método executar definindo um manipulador na configuração da função. 
- O *manipulador* da função do Lambda é o método no código da função que processa eventos. 
- Quando sua função é invocada, o Lambda executa o método do manipulador. 
- Quando o manipulador é encerrado ou retorna uma resposta, ele se torna disponível para tratar de outro evento.

## Balanceador de carga

Você pode usar uma função do Lambda para processar solicitações de um balanceador de carga da aplicação. O [Elastic Load Balancing](https://github.com/dansotirakis/lab-i-aws/Wiki/ElasticLoadBalancing) é compatível com funções do Lambda como destino para um balanceador de carga da aplicação.

Use regras de load balancer para rotear solicitações HTTP para uma função, com base no caminho ou em valores de cabeçalho. Processe a solicitação e retorne uma resposta HTTP de sua função do Lambda.

## Integrações

| [Amazon Alexa](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-alexa.html) | Conduzido por eventos; invocação síncrona   |
| ------------------------------------------------------------ | ------------------------------------------- |
| [Amazon Managed Streaming for Apache Kafka](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-msk.html) | Sondagem Lambda                             |
| [Apache Kafka autogerenciado](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-kafka.html) | Sondagem Lambda                             |
| [Amazon API Gateway](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-apigateway.html) | Conduzido por eventos; invocação síncrona   |
| [AWS CloudFormation](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-cloudformation.html) | Conduzido por eventos; invocação assíncrona |
| [Amazon CloudFront (Lambda@Edge)](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/lambda-edge.html) | Conduzido por eventos; invocação síncrona   |
| [Amazon EventBridge (CloudWatch Events)](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-cloudwatchevents.html) | Conduzido por eventos; invocação assíncrona |
| [Amazon CloudWatch Logs](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-cloudwatchlogs.html) | Conduzido por eventos; invocação assíncrona |
| [AWS CodeCommit](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-codecommit.html) | Conduzido por eventos; invocação assíncrona |
| [AWS CodePipeline](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-codepipeline.html) | Conduzido por eventos; invocação assíncrona |
| [Amazon Cognito](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-cognito.html) | Conduzido por eventos; invocação síncrona   |
| [AWS Config](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-config.html) | Conduzido por eventos; invocação assíncrona |
| [Amazon Connect](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-connect.html) | Conduzido por eventos; invocação síncrona   |
| [Amazon DynamoDB](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-ddb.html) | Sondagem Lambda                             |
| [Amazon Elastic File System](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-efs.html) | Integração especial                         |
| [Elastic Load Balancing Application Load Balancer)](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-alb.html) | Conduzido por eventos; invocação síncrona   |
| [AWS IoT](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-iot.html) | Conduzido por eventos; invocação assíncrona |
| [AWS IoT Eventos do](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-iotevents.html) | Conduzido por eventos; invocação assíncrona |
| [Amazon Kinesis](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-kinesis.html) | Sondagem Lambda                             |
| [Amazon Kinesis Data Firehose](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-kinesisfirehose.html) | Conduzido por eventos; invocação síncrona   |
| [Amazon Lex](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-lex.html) | Conduzido por eventos; invocação síncrona   |
| [Amazon MQ](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-mq.html) | Sondagem Lambda                             |
| [Amazon Simple Email Service](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-ses.html) | Conduzido por eventos; invocação assíncrona |
| [Amazon Simple Notification Service](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-sns.html) | Conduzido por eventos; invocação assíncrona |
| [Amazon Simple Queue Service](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-sqs.html) | Sondagem Lambda                             |
| [Amazon Simple Storage Service (Amazon S3)](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-s3.html) | Conduzido por eventos; invocação assíncrona |
| [Amazon Simple Storage Service Batch](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-s3-batch.html) | Conduzido por eventos; invocação síncrona   |
| [Secrets Manager](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-secrets-manager.html) | Conduzido por eventos; invocação síncrona   |
| [AWS X-Ray](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-xray.html) | Integração especial                         |

### Invocação conduzida por eventos

Alguns serviços geram eventos que podem invocar sua função do Lambda. Para obter mais informações sobre como projetar esses tipos de arquiteturas, consulte Arquiteturas orientadas por eventos no Guia do operador do Lambda.

### Sondagem Lambda

Para serviços que geram uma fila ou fluxo de dados, configure um mapeamento da fonte do evento no Lambda para fazer o Lambda sondar a fila ou um fluxo de dados.

#### Mapeamentos de fonte de eventos

Um mapeamento de fonte do evento é um recurso do Lambda que lê a partir de uma fonte de evento e invoca uma função do Lambda. Você pode usar os mapeamentos de origem do evento para processar itens de um stream ou fila em serviços que não invocam funções do Lambda diretamente.

Um mapeamento da origem do evento usa permissões na função de execução para ler e gerenciar itens na origem do evento.

##### Registro de invocação de uma transmissão do Kinesis

```shell
{
    "requestContext": {
        "requestId": "c9b8fa9f-5a7f-xmpl-af9c-0c604cde93a5",
        "functionArn": "arn:aws:lambda:us-east-2:123456789012:function:myfunction",
        "condition": "RetryAttemptsExhausted",
        "approximateInvokeCount": 1
    },
    "responseContext": {
        "statusCode": 200,
        "executedVersion": "$LATEST",
        "functionError": "Unhandled"
    },
    "version": "1.0",
    "timestamp": "2019-11-14T00:38:06.021Z",
    "KinesisBatchInfo": {
        "shardId": "shardId-000000000001",
        "startSequenceNumber": "49601189658422359378836298521827638475320189012309704722",
        "endSequenceNumber": "49601189658422359378836298522902373528957594348623495186",
        "approximateArrivalOfFirstRecord": "2019-11-14T00:38:04.835Z",
        "approximateArrivalOfLastRecord": "2019-11-14T00:38:05.580Z",
        "batchSize": 500,
        "streamArn": "arn:aws:kinesis:us-east-2:123456789012:stream/mystream"
    }
}
```

