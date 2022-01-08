# Criando uma função Lambda e testando-a

## Diagrama de Arquitetura

![img](https://play.whizlabs.com/frontend/web/media/2020/07/14/task_id_148_creating_a_lambda_function_and_testing_it.png)

## Detalhes da Tarefa

1. Faça login no AWS Management Console.
2. Crie uma função Lambda.
3. Teste a função imprimindo "Hello World" no console.
4. Validação do laboratório

## Etapas de laboratório

### Tarefa 1: Criando uma função Lambda

1. Certifique-se de estar na região da **Virgínia** .
2. Navegue até o  ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image12_14_44.png) menu e clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image11_14_59.png)
3. Clique no botão **Criar uma função** .
   - Escolha o **autor do zero** .
   - Nome da função: Digite ***myfirstlambda\***
   - Tempo de execução: selecione **Python 3.8**
   - Não precisamos de nenhuma permissão para este laboratório.
   - Clique na **função Criar**
4. Sua função Lambda será criada.

![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image9_16_25.png)

### Tarefa 2: invocando a função com o evento de teste

1. Role para baixo até ver o editor de texto integrado.
2. Clique duas vezes em **lambda_function.py** à sua esquerda para ver o editor de texto.
3. Vamos mudar o corpo para **Hello Lambda!** em vez de **Hello from Lambda!** Em seguida, clique no botão **Implementar** . 

![img](https://play.whizlabs.com/frontend/web/media/2021/04/28/lambda_ss_3.png)

1. Para testar nosso código, clique em **Testar** . Precisamos configurar um evento de teste primeiro.
2. Insira o nome do evento como ***myfirstevent*** . Role para baixo e clique em **Criar** .
3. Clique em **Testar** para testar o código.
4. Você obterá um Resultado de Execução como bem-sucedido se tudo funcionar corretamente.

![img](https://play.whizlabs.com/frontend/web/media/2021/04/28/lambda_lab_screenshot_12_06.png)

1. Aqui, o **código de status - 200** , significa que a solicitação foi recebida e está sendo processada.