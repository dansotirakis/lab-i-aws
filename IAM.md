# IAM

## Papéis

Criação de papéis IAM

### Detalhes do laboratório:

1. Este laboratório orienta você nas etapas para criar funções de IAM.
2. Duração: **30 minutos**
3. Região AWS: **US East (N. Virginia) us-east-1**

### Diagrama de arquitetura:

![img](https://play.whizlabs.com/frontend/web/media/2020/06/04/task_id_81_creating_iam_roles.png)

#### Detalhes da tarefa:

1. Faça login no AWS Management Console.
2. Criar função IAM para serviço EC2
3. Crie uma função IAM para o serviço DynamoDB.
4. Validação do laboratório

### Etapas de laboratório

#### Tarefa 1: Iniciando o ambiente de laboratório

1. Inicie o ambiente de laboratório clicando em ![img](https://play.whizlabs.com/frontend/web/media/2021/05/31/start_lab.png). Aguarde até que o ambiente de laboratório seja provisionado. O provisionamento do ambiente de laboratório levará menos de 2 minutos.
2. Uma vez que o laboratório é iniciado, você será fornecido com ***nome IAM usuário\*** , ***senha\*** , **AccessKey** e ***acesso chave secreta\*** . 
3. Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/05/31/open_console.png), AWS Management Console abrirá em uma nova guia.
4. Na página de login da AWS, a ID da conta estará presente por padrão.
   - Deixe a ID da conta como padrão. Não remova ou altere a ID da conta, caso contrário você não poderá prosseguir com o laboratório.
5. Copie e cole o ***nome de usuário*** e a ***senha\*** do ***IAM*** no console da AWS. Clique em **Sign in** para fazer o login no AWS Console. 

**Observação:** se você enfrentar qualquer problema, consulte as [**perguntas frequentes e a solução de problemas para laboratórios**](https://play.whizlabs.com/site/task_support/faqs-and-troubleshooting) .

#### Tarefa 2: Criação de função para um serviço EC2

1. Navegue até **IAM** clicando no ![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image13.png) menu na parte superior e, a seguir, clique em **IAM** na ![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image2.png) seção.
2. No menu esquerdo, selecione **Funções** .
3.  Clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image4.png).
4. Para **Selecionar tipo de entidade confiável** , escolha **EC2.** Então clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/09/image21.png)

![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image11.png)

1. Em Anexar políticas de permissão **,** digite **EC2** nas Políticas de filtro e selecione **AmazonEC2FullAccess**

**Nota: Não adicione outras políticas além das mencionadas acima. Você obterá um erro ao criar a função.**

![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image3.png)

1. Então clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/09/image19.png)
2. Adicionar Tags
   - Chave: Digite o ***nome\***
   - Valor: Insira ***MyEC2role\***  
   - Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/09/image22.png)
3. Análise:
   - Nome da função: digite ***EC2Role\***
   -  Para a **descrição da função** , digite uma descrição para a nova função.
   - Revise a função e escolha **Criar função** .
4. Após a criação, você obterá uma verificação para a função criada.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image10.png)

1. Ao pesquisar por nosso nome de função, você verá a função criada ser preenchida.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image14.png)

**Nota** :

- Ao configurar um ambiente de serviço AWS, você deve definir uma função para o serviço assumir. Você pode anexar esta função aos serviços da AWS. Esta função de serviço deve incluir todas as permissões necessárias para que o serviço acesse os recursos da AWS de que precisa.
- Isso permite que o EC2 execute ações em nosso nome.

#### Tarefa 3: Criação de função para um serviço AWS - DynamoDB

1. No menu esquerdo, selecione **Funções** .
2.  Clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image4_51_37.png)
3. Para **Selecionar tipo de entidade confiável** , escolha **DynamoDB.**
4. Selecione o caso de uso como **Amazon DynamoDB Accelerator (DAX) - acesso DynamoDB.**

![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image7_52_31.png)

1. Então clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/09/image21_54_41.png)
2. Em Anexar políticas de permissão **,** você pode ver **AmazonDynamoDBFullAccess.**

##### **Nota: Não adicione outras políticas além das mencionadas acima. Você obterá um erro ao criar a função.**

![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image6.png)

1. Então clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/09/image19_55_01.png)
2. Adicionar Tags
   - Chave: Digite o ***nome\***
   - Valor: Insira ***MyDynamoDBrole\***  
   - Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/09/image22.png)
3. Análise:
   - Nome da Função: Digite ***DynamoDBRole\***
   -  Para a **descrição da função** , digite uma descrição para a nova função.
   - Revise a função e escolha **Criar função** .
4. Após a criação, você obterá uma verificação para a função criada.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image9_53_50.png)

1. Ao pesquisar por nosso nome de função, você verá a função criada ser preenchida.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/image8.png)

1. Ao configurar um ambiente de serviço da AWS, você deve definir uma função para o serviço assumir. Você pode anexar essa função aos serviços da AWS. Esta função de serviço deve incluir todas as permissões necessárias para que o serviço acesse os recursos da AWS de que precisa.
2. Isso permite que o DynamoDB execute ações em nosso nome. 

## Politicas

Criação de políticas IAM



### Detalhes do laboratório:

1. Este laboratório orienta você nas etapas para criar políticas de IAM
2. Duração: **30 minutos**
3. Região AWS: **US East (N. Virginia) us-east-1**

### Diagrama de arquitetura:

![img](https://play.whizlabs.com/frontend/web/media/2020/06/04/task_id_82_creating_iam_policies.png)

#### Detalhes da tarefa:

1. Faça login no AWS Management Console.
2. Crie a política IAM para EC2.
3. Crie a política IAM para S3.
4. Crie uma política IAM para o DynamoDB.
5. Validação do laboratório

### Etapas de laboratório

#### Tarefa 1: Iniciando o ambiente de laboratório

1. Inicie o ambiente de laboratório clicando em ![img](https://play.whizlabs.com/frontend/web/media/2021/05/31/start_lab.png). Aguarde até que o ambiente de laboratório seja provisionado. O provisionamento do ambiente de laboratório levará menos de 2 minutos.
2. Uma vez que o laboratório é iniciado, você será fornecido com ***nome IAM usuário\*** , ***senha\*** , **AccessKey** e ***acesso chave secreta\*** . 
3. Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/05/31/open_console.png), AWS Management Console abrirá em uma nova guia.
4. Na página de login da AWS, a ID da conta estará presente por padrão.
   - Deixe a ID da conta como padrão. Não remova ou altere a ID da conta, caso contrário você não poderá prosseguir com o laboratório.
5. Copie e cole o ***nome de usuário*** e a ***senha\*** do ***IAM*** no console da AWS. Clique em **Sign in** para fazer o login no AWS Console. 

**Observação:** se você enfrentar qualquer problema, consulte as [**perguntas frequentes e a solução de problemas para laboratórios**](https://play.whizlabs.com/site/task_support/faqs-and-troubleshooting) .

#### Tarefa 2: Criando Política para EC2

1. Navegue até o ![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image10.png) menu na parte superior e clique em **IAM** na ![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image15.png) seção.
2. No menu esquerdo, selecione **Políticas** .
3. Clique em **Criar política** .
4. No **Editor Visual** , selecione **escolher um serviço** . 
5. Digite **EC2** na caixa de pesquisa e selecione **EC2** .

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image6.png)

1. Em **Ações** , especifique as ações permitidas em EC2. Para este serviço, escolheremos **Listar** e **Ler** .

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image18.png)

1. Clique em **Recursos,** role para baixo e escolha **Todos os recursos** para que não haja necessidade de especificar o ARN do recurso.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image11.png)

1. Agora role para cima e se você clicar no JSON, você pode ver a política que criamos.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image16.png)

1. Clique em **Avançar: Tags** . Nenhuma mudança necessária.
2. Clique em **Next: Review** .
3. Análise:
   - Nome: Digite ***EC2Policy***
   - Descrição: Digite ***EC2 Full Read and List access***
   - No Resumo, você pode ver o nível de acesso.
   - Revise a política e clique em **Criar política** .

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image2.png)

1. Após a criação, você obterá uma verificação para a Política criada.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image14.png)

1. Nas políticas de filtro, digite o nome da sua política e clique nele.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image20.png)

1. No Resumo, (sob o JSON) você pode ver a política que você criou. 

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image19.png)

 

#### Tarefa 3: Criando Política para S3

1. No menu esquerdo, selecione **Políticas** .
2. Clique em **Criar política** .
3. No **Editor Visual** , selecione **escolher um serviço** . 
4. Digite S3 na caixa de pesquisa e selecione **S3** .
5. Em **Ações** , especifique as ações permitidas no S3. Para este serviço, escolheremos **List, Tagging** e **Write** .

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image4.png)

1. Clique em **Recursos** e escolha **Todos os recursos** para que não haja necessidade de especificar o ARN do recurso.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image11.png)

1. Se você clicar no JSON, poderá ver a política que criamos.
2. Clique em **Avançar: Tags** . Nenhuma mudança necessária.
3. Clique em **Next: Review** .
4. Análise:
   - Nome: Digite ***S3Policy***
   - Para a **descrição da política** , digite uma descrição para a nova política.
   - No Resumo, você pode ver o nível de acesso.
   - Revise a política e clique em **Criar política** .
5. Depois de criar, você obterá uma verificação para a política criada

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image8.png)

1. Nas políticas de filtro, digite o nome da sua política e clique nele.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image9.png)

1. No Resumo, (sob o JSON) você pode ver a política que você criou. 

#### Tarefa 4: Criando Política para DynamoDB

1. No menu esquerdo, selecione **Políticas** .
2. Clique em **Criar política** .
3. No **Editor Visual** , selecione **escolher um serviço** . 
4. Digite DynamoDB na caixa de pesquisa e selecione **DynamoDB** .
5. Em **Ações** , especifique as ações permitidas no DynamoDB. Para este serviço, vamos escolher **List, Read, Tagging** e **Write.**

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image7.png)

1. Clique em **Recursos** e escolha **Todos os recursos** para que não haja necessidade de especificar o ARN do recurso.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image11.png)

1. Se você clicar no JSON, poderá ver a política que criamos.
2. Clique em **Avançar: Tags** . Nenhuma mudança necessária.
3. Clique em **Next: Review** .
4. Análise:
   - Nome: Digite ***DynamoDBPolicy***
   -  Para a **descrição da política** , digite uma descrição para a nova política.
   - No Resumo, você pode ver o nível de acesso.
   - Revise a política e clique em **Criar política** .
5. Depois de criar, você obterá uma verificação para a política criada

![img](https://play.whizlabs.com/frontend/web/media/2020/01/23/image3.png)

1. Nas políticas de filtro, digite o nome da sua política e clique nele.
2. No Resumo, (sob o JSON) você pode ver a política que você criou. 