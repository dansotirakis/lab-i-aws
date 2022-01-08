## Criação de um pool de usuários no AWS Cognito

![img](https://play.whizlabs.com/frontend/web/media/2020/06/04/task_id_74_creating_a_user_pool_in_aws_cognito.png)

1. Criar um pool de usuários
2. Nomes e Atributos
3. Políticas
4. MFA e verificações
5. Personalizações de mensagens
6. Tag
7. Dispositivos
8. Cliente de aplicativo
9. Personalize Fluxos de Trabalho
10. Análise

### Tarefa 1: Criando um pool de usuários

1. Navegue até o Cognito clicando no ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image16.png) menu na parte superior, clique em Cognito na ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image20.png)seção.
2. Certifique-se de que você está na região **us-east-1 do leste** dos **EUA (Virgínia do** Norte). Clique em **Gerenciar pools de usuários** **.**

**![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image8.png)**

1. Clique em **Create a User Pool** .

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image23.png)

### Tarefa 2: Nome e atributos

1. Dê ao seu Pool de usuários um nome descritivo (que é necessário para a identidade). Usaremos **whizlabs** . .
2. Escolhemos as **configurações de Passo a passo** para fazer cada configuração nossa própria escolha, conforme mostrado abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image17.png)

1. Na página Atributos, podemos mencionar como um usuário pode realizar um login.
2. Você pode escolher que os usuários façam login com um endereço de e-mail, número de telefone, nome de usuário ou nome de usuário preferencial mais sua senha.
3. Aqui, escolhemos o **endereço de e-mail ou número de telefone** , onde os usuários podem usar um endereço de e-mail ou número de telefone como **nome** de **usuário** para se inscrever e entrar. Aqui, escolha **Permitir endereços de e-mail** .

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image1.png)

1. Podemos escolher os **atributos padrão** , que serão necessários ao realizar uma inscrição. Aqui, escolhemos e-mail, nome, nome de usuário preferido, número de telefone, que são necessários para realizar uma inscrição.
2. Também podemos personalizar nossos atributos que são necessários durante a inscrição, clicando em **Adicionar outro atributo** . 
3. Clique no **próximo passo**

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image21.png)

### Tarefa 3: Políticas

1. Fornecemos a **Força Mínima da Senha** e podemos adicionar os parâmetros necessários, como números, letras minúsculas, maiúsculas e caracteres especiais. Aqui, selecionamos todos os parâmetros.
2. Você pode optar por **permitir que apenas administradores criem usuários ou permitir que os próprios usuários se inscrevam** .
3. Nós escolhemos **permitir que os usuários se inscrevam,** onde os **próprios** usuários podem se inscrever sem a interferência do administrador.
4. Como administrador, você pode configurar quando as senhas temporárias devem expirar . Isso inclui contas criadas por administradores, ou seja, se você escolher **permitir que apenas administradores criem usuários** . Aqui, podemos deixar a opção porque não a selecionamos.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image14.png)

1. Clique no **próximo passo**

### Tarefa 4: MFA e verificações

1. **A autenticação multifator (MFA)** aumenta a segurança para seus usuários finais. Os números de telefone devem ser verificados se o MFA está habilitado. Escolhemos **O** **ff** para este laboratório.
2. **Recuperação de conta :** quando um usuário esquece sua senha, um código pode ser enviado para seu e-mail verificado ou telefone verificado para recuperar sua conta. Você pode escolher a forma preferida de enviar os códigos abaixo. Aqui, escolhemos **apenas e-** **mail** .

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image12.png)

1. **A verificação** exige que os usuários recuperem um código de seu e-mail ou telefone para confirmar a propriedade. A verificação de um telefone ou e-mail é necessária para confirmar automaticamente os usuários e permitir a recuperação de senhas esquecidas. Neste caso, escolhemos **Email** .

![img](https://play.whizlabs.com/frontend/web/media/2021/07/15/task_5_step_4.jpg)

1. Ignorar o aviso acima e **desmarque** a **Reconhecer proceder** . Clique no **próximo passo**

### Tarefa 6: personalizações de mensagens

1. Você pode enviar e-mails de uma identidade verificada pelo SES. Antes de enviar um e-mail usando o Amazon SES, você deve verificar cada identidade que usará como endereço De, Origem, Remetente ou Caminho de retorno para provar que você é o proprietário. Por enquanto, deixamos em branco.
2. **Configuração do Amazon SES : O** Cognito enviará e-mails por meio da configuração do Amazon SES. Selecione Sim se você precisar de limites de e-mail diários mais altos, caso contrário, selecione Não. Aqui, selecionamos **Não - Usar Cognito (Padrão)** .

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image13.png)

1. Tipo de verificação: você pode optar por enviar um código ou um link clicável e personalizar a mensagem para verificar os endereços de e-mail. Nós o mantemos como código padrão .

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image15.png)

1. Mensagens de convite do usuário: Podemos personalizar a mensagem SMS, o assunto do e-mail e a mensagem do e-mail de acordo com a forma como você deseja que o texto seja entregue ao usuário.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image3.png)

1. Clique no **próximo passo**

### Tarefa 6: Tags

1. Você pode criar novas tags inserindo chaves de tag e valores de tag.

- Chave de tag: Digite o ***nome***
- Valor da tag: Insira ***MyUserPool\*** 

1. Clique no **próximo passo**

### ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image5.png)Tarefa 7: Dispositivos

- Podemos escolher lembrar os dispositivos de nossos usuários. Aqui, escolhemos **Não** e clicamos em **Próxima etapa**

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image10.png)

### Tarefa 8: App Client

1. Os clientes de aplicativos que adicionarmos receberão um ID exclusivo e uma chave secreta opcional para acessar esse pool de usuários. Não estamos usando nenhum App Client aqui, então passamos para a **próxima etapa**

### Tarefa 9: personalizar fluxos de trabalho

1. Você pode fazer personalizações avançadas com funções do AWS Lambda. Escolha as funções do AWS Lambda para disparar com eventos diferentes se desejar personalizar fluxos de trabalho e experiência do usuário. 
2. Você pode passar por todos os eventos. Vamos pular isso e prosseguir para a **próxima etapa**

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image9.png)

### Tarefa 10: Revisão

- Revise todas as configurações e clique em Criar Pool conforme mostrado abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image6.png)

- Você receberá uma mensagem informando que **Seu pool de usuários foi criado com êxito** .

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image19.png)

- No canto superior esquerdo, clique em Pools de usuários para ver **seus pools de usuários.**

**![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/created_user_pool.png)**

- Navegue até o Cognito, clique em **Usuários** **e grupos** para navegar até a página Usuários conforme mostrado abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image4.png)

- Aqui, podemos começar a criar usuários e grupos.
- De uma perspectiva administrativa, se tivermos um aplicativo, o aplicativo invocará o Amazon Cognito para criar o próprio usuário.