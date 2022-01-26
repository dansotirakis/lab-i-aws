# AWS Step Functions

Step Functions é um serviço de orquestração sem servidor que permite combinarAWS LambdaFunções e outrosAWSpara criar aplicativos essenciais para os negócios. Através do console gráfico do Step Functions, você vê o fluxo de trabalho do aplicativo como uma série de etapas orientadas por eventos.

Gerencia os componentes e a lógica do seu aplicativo, para que você possa escrever menos código e se concentrar em criar e atualizar seu aplicativo rapidamente.

Permite adicionar automação de fluxo de trabalho resiliente aos seus aplicativos em minutos, sem escrever código.

## Integações

- [AWS Lambda](https://github.com/dansotirakis/lab-i-aws/Wiki/Lambda/)
- [AWS Glue](https://github.com/dansotirakis/lab-i-aws/Wiki/Glue)

- [AWS SDK Integrações](https://github.com/dansotirakis/lab-i-aws/Wiki/Itegrations)
- [Integrações otimizadas](https://docs.aws.amazon.com/pt_br/step-functions/latest/dg/connect-supported-services.html)

## Fluxos de trabalho

Os fluxos de trabalho expressos têm uma execução de fluxo de trabalho de pelo menos uma vez e podem ser executados por até cinco minutos. Execuções são instâncias em que você executa seu fluxo de trabalho para executar tarefas.

### Standart

- Taxa de execução de 2.000 por segundo
- Taxa de transição de estado de 4.000 por segundo
- Cobrado por transição de estado
- Mostra o histórico de execução e a depuração visual
- Compatível com todas as integrações e padrões

### Express

- Taxa de execução de 100.000 por segundo
- Taxa de transição de estado quase ilimitada
- Preço por número e duração das execuções
- Envia o histórico de execução para o [CloudWatch](https://github.com/dansotirakis/lab-i-aws/Wiki/CloudWatch)
- Oferece suporte a todas as integrações de serviço e a maioria

## Resursos

### Fluxo de trabalho visual

O AWS Step Functions permite coordenar tarefas individuais em um fluxo de trabalho visual, para que você possa criar e atualizar aplicativos rapidamente.

### Maquina de estado

Os fluxos de trabalho criados com o Step Functions são chamados de **máquinas de estado** e cada etapa do fluxo de trabalho é chamada de **estado**.

### Tarefas

**As tarefas** executam o trabalho coordenando outro serviço da AWS ou um aplicativo que você pode hospedar basicamente em qualquer lugar.

Um estado `Task` (`"Type": "Task"`) representa uma unidade de trabalho específica executada por uma máquina de estado.

Em sua máquina de estado, todo trabalho é realizado por *tarefas*. Uma tarefa executa o trabalho usando uma atividade ou uma função AWS Lambda ou passando parâmetros para as ações de API de outros serviços.

### States

Os estados individuais podem tomar decisões com base em seus dados de entrada, executar ações e transmitir os dados de saída para outros estados. 

Um estado é chamado por seu nome, que, embora possa ser qualquer string, deve ser exclusivo no escopo da máquina de estado como um todo.

Os estados podem realizar uma variedade de funções na máquina de estado:

- Realizar alguns trabalhos na máquina de estado (um estado [Task](https://docs.aws.amazon.com/pt_br/step-functions/latest/dg/amazon-states-language-task-state.html))
- Escolher entre ramificações da execução (um estado [Choice](https://docs.aws.amazon.com/pt_br/step-functions/latest/dg/amazon-states-language-choice-state.html)).
- Interromper uma execução com falha ou que tenha tido êxito (um estado [Fail](https://docs.aws.amazon.com/pt_br/step-functions/latest/dg/amazon-states-language-fail-state.html) ou [Succeed](https://docs.aws.amazon.com/pt_br/step-functions/latest/dg/amazon-states-language-succeed-state.html)).
- Simplesmente passar a entrada para a saída ou injetar alguns dados fixos (um estado [Pass](https://docs.aws.amazon.com/pt_br/step-functions/latest/dg/amazon-states-language-pass-state.html)).
- Introduzir um atraso de determinada duração ou até uma data/hora especificada (um estado [Wait](https://docs.aws.amazon.com/pt_br/step-functions/latest/dg/amazon-states-language-wait-state.html)).
- Iniciar ramificações paralelas da execução (um estado [Parallel](https://docs.aws.amazon.com/pt_br/step-functions/latest/dg/amazon-states-language-parallel-state.html)).
- Iterar dinamicamente as etapas (estado de [mapa](https://docs.aws.amazon.com/pt_br/step-functions/latest/dg/amazon-states-language-map-state.html))

#### Os estados compartilham muitos recursos comuns (campos obrigatórios)

##### Campo `Type` para indicar que tipo de estado ele é.

##### Todo estado **pode ter** um campo `Comment` opcional para armazenar um comentário ou uma descrição humanamente legível do estado.

##### Todo estado (exceto um estado `Succeed` ou `Fail`) exige um campo `Next` ou, de outro modo, pode se tornar um estado final por meio da especificação de um campo `End`.

> Um estado `Choice` pode ter mais de um `Next`, mas apenas um em cada Choice Rule. Um estado `Choice` não pode usar `End`.

#### Exemplo de estado que executa uma função Lambda.

```
"HelloWorld": {
  "Type": "Task",
  "Resource": "arn:aws:lambda:us-east-1:123456789012:function:HelloFunction",
  "Next": "AfterHelloWorldState",
  "Comment": "Run the HelloWorld Lambda function"
}
```