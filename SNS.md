# Criação de um tópico SNS e inscrição por e-mail

## Diagrama de Arquitetura

![img](https://play.whizlabs.com/frontend/web/media/2020/07/14/task_id_150_creating_a_sns_topic_and_subscribing_to_email_notifications.png) Detalhes da Tarefa

1. Faça login no AWS Management Console.
2. Crie um Tópico SNS.
3. Inscreva-se para receber notificações por e-mail ao criar o Tópico SNS.
4. Validação do laboratório

# Etapas de laboratório

## Tarefa 1: Criando Tópico SNS

1. Navegue até o ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image11_10_56.png) menu e clique em **Simple Notification Service (SNS)** na ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image8_11_17.png) seção.
2. Selecione Tópicos no painel esquerdo e clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image1_11_36.png).
3. Em **Detalhes**
   - Tipo: Selecione o **padrão**
   - Nome: digite ***mysnstopic\***
   - Nome de exibição: ***mysnsnotification\***
     ![img](https://play.whizlabs.com/frontend/web/media/2020/12/28/abc.png)
4. Deixe as outras opções como padrão e clique em **Criar tópico** .
5. Um tópico SNS será criado.

![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image6_12_49.png)

## Tarefa 2: inscrevendo-se no tópico

1. Assim que o Tópico SNS for criado, clique em seu tópico.
2. Clique em **Criar assinatura**
3. Em Detalhes
   - Protocolo: Selecione **E-mail**
   - Endpoint: Digite o ***seu <Mail Id>***
   - **Nota:** Certifique-se de fornecer um endereço de e-mail válido, pois você receberá uma notificação SNS neste endereço.
4. Clique em **Criar assinatura** .

![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image3_13_46.png)

1.  Você receberá um e-mail em sua caixa de correio do SNS.

![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image2_14_11.png)

1. Clique em **Confirmar assinatura** .
2. Seu endereço de e-mail agora está inscrito no tópico SNS ***mysnstopic** .*

![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image10_14_47.png)

1. Você pode cancelar a assinatura do Tópico SNS a qualquer momento.
2. Podemos usar isso para se inscrever em eventos S3, eventos CloudWatch e muito mais.

