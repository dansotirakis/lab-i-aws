# Introdução ao Amazon Simple Email Service SES

## Diagrama de Arquitetura

![img](https://play.whizlabs.com/frontend/web/media/2020/07/01/task_id_134_introduction_to_amazon_simple_email_service_ses_(1).png)

## Detalhes da Tarefa

1. Crie uma identidade de e-mail usando SES.
2. Verifique o endereço de e-mail.
3. Envie um e-mail de teste.

### Tarefa 1: Iniciando o ambiente de laboratório

1. Inicie o ambiente de laboratório clicando em ![img](https://play.whizlabs.com/frontend/web/media/2021/05/31/start_lab.png). Aguarde até que o ambiente de laboratório seja provisionado. O provisionamento do ambiente de laboratório levará menos de 2 minutos.
2. Uma vez que o laboratório é iniciado, você será fornecido com ***nome IAM usuário\*** , ***senha\*** , **AccessKey,** e ***acesso chave secreta\*** . 
3. Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/05/31/open_console.png), AWS Management Console abrirá em uma nova guia.
4. Na página de login da AWS, a ID da conta estará presente por padrão.
   - Deixe a ID da conta como padrão. Não remova ou altere a ID da conta, caso contrário, você não poderá prosseguir com o laboratório.
5. Copie e cole o ***nome de usuário*** e a ***senha\*** do ***IAM*** no console da AWS. Clique em **Sign in** para fazer o login no AWS Console. 

**Observação:** se você enfrentar qualquer problema, consulte as [**perguntas frequentes e a solução de problemas para laboratórios**](https://play.whizlabs.com/site/task_support/faqs-and-troubleshooting) .

### Tarefa 2: crie uma identidade de e-mail usando SES

1. Certifique-se de que você está na região **us-east-1 do leste** dos **EUA (Virgínia do** Norte).
2. Navegue até o ![img](https://play.whizlabs.com/frontend/web/media/2020/02/10/image7_45_32.png) menu na parte superior. Clique em **Amazon Simple Email Service** na ![img](https://play.whizlabs.com/frontend/web/media/2021/04/16/business_application.png)seção.
3. No menu do lado esquerdo, **selecione** ![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/1.png)
4. Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/2.png)
5. Insira os seguintes detalhes:
   - Tipo de identidade: Selecione o **endereço de e-mail**
   - Endereço de e-mail: **digite seu ID de e-mail válido** .
   - **Deixe as outras opções como padrão.**
   - Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/2_19_27.png)

![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/3_20_47.png)

1. Você obterá o **erro IAM** abaixo , apenas ignore-o. Você não precisará dessa permissão para concluir o laboratório.?

![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/4.png)

1. Agora você poderá ver que o **status de identidade** no e-mail será Não **verificado.**

![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/5.png)

### Tarefa 3: verifique o endereço de e-mail

1. A AWS enviará um email de confirmação para o email que você forneceu na etapa acima.
2. Faça login em sua caixa de correio e você poderá ver um e-mail da Amazon Web Services.

![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/6_26_12.png)

1. Depois de clicar no **link** , você será direcionado para a página de sucesso.

![img](https://play.whizlabs.com/frontend/web/media/2020/02/10/image3_50_44.png)

1. Agora vá para a **página Endereço de** e- **mail SES** e **atualize a página** . Você poderá ver o status de verificação como **Ativo** .

![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/7.png)

### Tarefa 4: envie um e-mail de teste 

1. Deixe-nos enviar um e-mail de teste para o mesmo endereço de e-mail.
2. Clique em **Enviar e-mail de teste** .

![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/8.png)

1. Faça as seguintes alterações:
   - Formato de e-mail: selecione **Formatado** (mantenha-o como padrão)
   - De: Seu endereço de e-mail estará presente por **padrão**
   - Cenário: Selecione **Personalizado** no menu suspenso
   - Destinatário personalizado: **forneça o mesmo endereço de e-mail** (para fins de teste)
   - Assunto: Digite **Enviando um Email de Teste**
   - Corpo: **Digite qualquer texto que desejar**
   - **Deixe as outras opções como padrão.**
   - Clique em **Enviar e-mail de teste** .

![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/9.png)

1. Verifique o e-mail recebido em sua caixa de entrada. Se não estiver na sua caixa de entrada, verifique o **spam** .

![img](https://play.whizlabs.com/frontend/web/media/2021/12/20/11.png)