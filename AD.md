# AWS Directory Service - Trabalhando com Simple AD

## Detalhes do laboratório

1. Este laboratório orienta você nas etapas de como criar um diretório Simple AD, adicionar grupos, usuários e computador.
2. Como parte deste laboratório, os principais AWS Services usados são - IAM, EC2, VPC, Directory Services.
3. Duração: **1 hora 30 minutos**
4. Região AWS: **Leste dos EUA (N Virginia)**

## Introdução

### O que é o AWS Directory Service?

- O AWS Directory Service oferece várias maneiras de usar o Microsoft Active Directory (AD) com outros serviços da AWS.
- Esses diretórios armazenam informações sobre usuários, grupos e dispositivos, e os administradores os usam para gerenciar o acesso a informações e recursos.
- O Directory Service oferece várias opções para clientes que desejam usar aplicativos existentes do Microsoft AD ou Lightweight Directory Access Protocol (LDAP) na nuvem.
- O serviço é baseado no Microsoft Active Directory real e baseado no Windows Server 2012 R2.
- O AWS Directory Service inclui vários tipos de diretório para escolher. Eles são:

- AWS Directory Service para Microsoft Active Directory
- Conector AD
- AD simples
- Amazon Cognito

**AWS Directory Service para Microsoft Active Directory**

- É alimentado por um Microsoft Windows Server Active Directory (AD) real, gerenciado pela AWS na nuvem AWS.
- Funciona com - Microsoft SharePoint, grupos de disponibilidade Always On do Microsoft SQL Server e muitos aplicativos .NET.
- Oferece suporte a aplicativos e serviços gerenciados pela AWS, incluindo - Amazon WorkSpaces, Amazon WorkDocs, Amazon QuickSight, Amazon Chime, Amazon Connect e Amazon Relational Database Service para Microsoft SQL Server / Oracle / PostgreSQL.

**Conector AD**

- É um serviço de proxy que fornece uma maneira fácil de conectar aplicativos AWS compatíveis, como Amazon WorkSpaces, Amazon QuickSight e Amazon EC2 para instâncias do Windows Server, ao seu Microsoft Active Directory local existente.
- É a melhor escolha quando você deseja usar seu Active Directory local existente com serviços AWS compatíveis.

**Amazon Cognito**

- É um diretório de usuário que adiciona inscrição e inscrição em seu aplicativo móvel ou aplicativo da web usando o Amazon Cognito User Pools.
- É usado quando você precisa criar campos de registro personalizados e armazenar esses metadados em seu diretório de usuário.
- Este serviço pode ser escalado para dar suporte a centenas de milhões de usuários.

**AD simples**

- Um diretório autônomo compatível com o Microsoft AD do AWS Directory Service que é desenvolvido com Samba 4.
- Ele é usado como um diretório independente na nuvem para suportar cargas de trabalho do Windows que precisam de recursos AD básicos, aplicativos AWS compatíveis ou para suportar cargas de trabalho do Linux que precisam de serviço LDAP.
- Oferece suporte a recursos AD básicos, como contas de usuário, associações de grupo, ingressar em um domínio Linux ou instâncias EC2 baseadas em Windows, SSO baseado em Kerberos e políticas de grupo.
- A AWS fornece monitoramento, instantâneos diários e recuperação como parte do serviço.
- Compatível com Amazon WorkSpaces, Amazon WorkDocs, Amazon Quicksight e Amazon WorkMail.
- Não suporta MFA, relações de confiança, atualização dinâmica de DNS, extensões de esquema, comunicação por LDAPS, etc.
- Não compatível com RDS SQL Server.
- Disponível em 2 tamanhos.

- Pequeno - Suporta até 500 usuários
- Grande - Suporta até 5.000 usuários

- Pré-requisitos

- Seu VPC deve ter pelo menos 2 sub-redes. Para que o Simple AD seja instalado corretamente, você deve instalar seus dois controladores de domínio em sub-redes separadas que devem estar em uma zona de disponibilidade diferente. Além disso, as sub-redes devem estar no mesmo intervalo CIDR.
- As portas necessárias para os controladores de domínio que o AWS Directory Service cria para você devem ser abertas para permitir que eles se comuniquem entre si.
- O VPC deve ter locação de hardware padrão.

- Quando o diretório é criado com o Simple AD, o AWS Directory Service executa as seguintes tarefas em seu nome:

- Configura um diretório baseado em Samba no VPC.
- Cria uma conta de administrador de diretório com o nome de usuário "Administrador" e a senha especificada. Esta conta é usada para gerenciar seu diretório.
- Cria um grupo de segurança para os controladores de diretório.
- Cria uma conta com privilégios de administrador de domínio.

- O Simple AD encaminha as solicitações de DNS para o endereço IP dos servidores DNS fornecidos pela Amazon para o seu VPC. Esses servidores DNS resolverão os nomes configurados nas zonas privadas do Route 53 hospedadas.

## Diagrama de Arquitetura

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image87.png)

## Detalhes da Tarefa

1. Iniciando ambiente de laboratório.
2. Criação de uma função IAM para trabalhar com o Active Directory.
3. Criação de um VPC
4. Criando um diretório simples de AD
5. Crie um conjunto de opções de DHCP
6. Criação e configuração do servidor Active Directory
7. Iniciando o servidor Active Directory
8. Registro com credenciais de usuário.
9. Adicionando um computador ao servidor Active Directory.
10. Exclusão de recursos da AWS

## Pré-requisitos

Para prosseguir com o laboratório, você deve ter um aplicativo Remote Desktop em seu computador.

### Para usuários do Windows

1. Clique no botão **Iniciar** e pesquise **RDC** . Você encontrará o aplicativo Remote Desktop Connection.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image3.png)

### Para usuários de Mac

1. No Mac, temos que baixar o aplicativo Remote Desktop.
2. Vá para a App Store, pesquise por **Microsoft Remote Desktop** e baixe o seguinte aplicativo.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image181.png)

### Para usuários Linux

1. No Linux, o **Remmina** geralmente está incluído na distribuição.
2. Caso contrário, vá para https://remmina.org/how-to-install-remmina/ e siga as instruções de instalação para qualquer distribuição Linux.

## Estudo de caso

- Somos obrigados a criar um anúncio simples.
- Adicionando grupos / usuários / computadores ao AD criado.
- Login no AD com as novas credenciais do usuário.

## Etapas de laboratório

## Tarefa 1: Iniciando o ambiente de laboratório

1. Inicie o ambiente de laboratório clicando em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/16/image76.png). Aguarde até que o ambiente de laboratório seja provisionado. O provisionamento do ambiente de laboratório levará menos de 2 minutos.
2. Uma vez que o laboratório é iniciado, você será fornecido com ***nome IAM usuário\*** , ***senha\*** , **AccessKey** e ***acesso chave secreta\*** . 
3. Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/16/image63.png), AWS Management Console abrirá em uma nova guia.
4. Na página de login da AWS, a ID da conta estará presente por padrão.
   - Deixe a ID da conta como padrão. Não remova ou altere a ID da conta, caso contrário você não poderá prosseguir com o laboratório.
5. Copie e cole o ***nome de usuário*** e a ***senha\*** do ***IAM*** no console da AWS. Clique em **Sign in** para fazer o login no AWS Console. 

**Observação:** se você enfrentar qualquer problema, consulte as [**perguntas frequentes e a solução de problemas para laboratórios**](https://play.whizlabs.com/site/task_support/faqs-and-troubleshooting) .

**Observação: não há teste de validação para este laboratório**

### Tarefa 2: criando uma função IAM para trabalhar com o Active Directory

1. Clique em **Services** e clique em **IAM** na seção **Security, Identity & Compliance** .
2. Selecione **Funções** no painel esquerdo e clique em **Criar função** para criar uma nova **função IAM** .
3. Na seção **Selecionar tipo de entidade confiável** , clique em **serviço AWS** .
4. Em **Escolha um caso de uso,** clique em **EC2** e clique no botão **Avançar: Permissões** para atribuir políticas.
5. Na página exibida, pesquise **AmazonSSMManagedInstanceCore** e **AmazonSSMDirectoryServiceAccess** e selecione-os um por vez.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image123_59_53.png)

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image110_00_28.png)

1. Clique no botão **Avançar: Tags** e forneça os detalhes.

- **Chave** : Digite o ***nome\***
- **Valor** : Insira ***AWS_SAD_Role\***

1. Clique no botão **Avançar: Revisar** e, na página exibida, forneça o nome da função que está sendo criada.

- **Nome da função** : digite ***AWS_SAD_Role\***
- **Descrição da função** : insira a ***função atribuída para trabalhar com Simple AD** .*

1. Ao dar o nome, clique no botão **Criar função** e a função é criada exibindo a mensagem.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image27_05_15.png)

### Tarefa 3: Criando um VPC

1. Navegue até o  menu **Serviços** na parte superior e clique em **VPC** presente na  seção **Rede e entrega de conteúdo** .
2. No **painel VPC,** você encontra os detalhes de todos os recursos disponíveis.
3. No lado esquerdo, clique em **Your VPC's** present no  menu **VIRTUAL PRIVATE CLOUD** .
4. Na página exibida, clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image40_13_30.png)botão e na página exibida, forneça os seguintes detalhes.

- **Nome** : Digite ***AWS_SAD_VPC\***
- **Bloco CIDR IPv4** : digite ***10.0.0.0/16\***
- Deixe todas as opções como estão e clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image40_14_03.png)botão e o VPC é criado com as configurações.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image28_14_49.png)

- A mensagem abaixo é exibida assim que o VPC é criado.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image95_16_38.png)

1. Agora vamos habilitar os nomes de host DNS neste VPC que usaremos para RDP para a instância onde o AD será configurado.
2. Selecione o VPC criado, clique no menu **A** **cções** e selecione **Editar nomes de host DNS** .
3. Na página exibida, marque **Habilitar** e clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image7_25_17.png)botão.
4. Você é exibido com a mensagem abaixo sobre a atualização da opção.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image59_26_07.png)

1. Clique no menu **Sub** - **redes** presente no lado esquerdo da página. Estaremos criando 2 sub-redes em diferentes zonas de disponibilidade para este laboratório.
2. Na página exibida, clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image47_27_25.png)botão e forneça os seguintes valores para criar.

- **ID de VPC** : selecione **AWS_SAD_VPC** no menu suspenso.
- **Nome da sub-rede** : digite ***AWS_SAD_Subnet1\***
- **Zona de disponibilidade** : Selecione **us-east-1a**
- **Bloco CIDR IPv4** : digite ***10.0.1.0/24\***

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image140.png)

- Deixe os demais campos como estão e clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image47_29_45.png)botão. 
- A sub-rede é criada e uma mensagem é exibida.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image132_46_16.png)

1. Selecione a sub-rede criada e clique no  menu **Ações** e selecione **Modificar configurações de IP de atribuição automática** .
2. Marque a caixa de seleção **Ativar atribuição automática de endereço IPv4 público** e clique no  botão **Salvar** .

1. Na página exibida, clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image47_35_35.png)botão e forneça os seguintes valores para criar.

- **ID de VPC** : selecione **AWS_SAD_VPC** no menu suspenso.
- **Nome da sub-rede** : digite ***AWS_SAD_Subnet2\***
- **Zona de disponibilidade** : Selecione **us-east-1b**
- **Bloco CIDR IPv4** : digite ***10.0.2.0/24\***

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image18_41_59.png)

- Deixe os demais campos como estão e clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image47_35_35.png)botão. 
- A sub-rede é criada e uma mensagem é exibida.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image157_47_04.png)

1. Selecione as sub-redes criadas uma por uma e clique no  menu **Ações** e selecione **Editar configurações de sub-rede** .
2. Marque a caixa de seleção **Ativar atribuição automática de endereço IPv4 público** e clique no  botão **Salvar** .
3. Clique no menu **Rotear Tabelas** presente no lado esquerdo da página. Estaremos criando uma única tabela de rota.
4. Na página exibida, clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image78_51_48.png)e forneça os seguintes valores na página exibida.

- **Nome** : Digite ***AWS_SAD_RT\***
- **VPC** : **selecione AWS_SAD_VPC** no controle suspenso.
- Clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image78_51_48.png)botão para criar a tabela de rotas.
- Abaixo está a mensagem exibida quando o serviço é criado.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image25_53_46.png)

1. Clique no menu **Gateways** da **Internet** presente no lado esquerdo da página.
2. Na página exibida, clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image151_55_25.png)botão e forneça os seguintes valores.

- **Tag de nome** : Insira ***AWS_SAD_IGW\***
- Clique no  botão **Criar gateway de internet** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image15_58_09.png)

1. No canto superior direito da página, clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image120_59_41.png)botão e forneça os seguintes valores.

- **VPCs disponíveis** : Selecione **AWS_SAD_VPC**
- Clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image104_00_57.png)botão e o Gateway de Internet é anexado ao VPC.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image44_01_49.png)

1. Como precisamos que nossas sub-redes se comuniquem pela Internet, atribuiremos o gateway da Internet e as sub-redes à tabela de rotas criada na **Etapa 9** .
2. Clique no menu **Rotear Tabelas** presente no lado esquerdo da página.
3. Selecione a tabela de rota criada anteriormente. Você é exibido com as guias abaixo.
4. Clique na  guia **Rotas** e, na grade exibida, clique no botão **Editar rotas,** botão presente no canto direito.
5. Na tela exibida, clique no botão **Adicionar rota** e forneça os seguintes valores para adicionar o Gateway de Internet.

- Em **Destino** : digite ***0.0.0.0/0\***
- Em **Destino** : selecione **Gateway de Internet** e escolha o gateway de Internet que criamos anteriormente.
- Clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image7_06_42.png)botão para salvar as configurações acima.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image96_07_50.png)

1. Na tela exibida, clique na guia **Associações de sub** - **rede** e, na grade exibida, clique no botão **Editar associações de sub-rede** presente no canto direito.

**Nota:** Por padrão, as sub-redes criadas são anexadas à tabela de rota padrão que foi criada quando o VPC foi criado.

1. Na página exibida, selecione as sub-redes criadas e clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image85_11_06.png)botão.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image139_12_39.png)

1. As sub-redes são anexadas à tabela de rotas criada e a mensagem abaixo é exibida como confirmação. ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image105_14_16.png)

**Nota** - Ao executar a etapa acima, as sub-redes são desassociadas da tabela de rota padrão.

### Tarefa 4: Criando um diretório simples do AD

1. Navegue até o  menu **Serviços** na parte superior e clique em **Serviço de diretório** presente no  menu **Segurança, Identidade e Conformidade** .
2. Na página exibida, clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image167_17_40.png)botão para criar um diretório.
3. Este trabalho é um processo de 3 etapas.

- **Passo 1 - Selecione o tipo de diretório**

   .

  - Estaremos selecionando ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image54.png)na lista exibida e clicar no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image92.png)botão.

- **Etapa 2 - Forneceremos as informações do diretório aqui** .

- **Tipo de diretório** : **Simple AD**
- **Tamanho do diretório** : selecione **pequeno**
- **Nome DNS do diretório** : digite ***whizlabs.com*** , que deve ser um nome de domínio totalmente qualificado.
- **Nome do NETBIOS do diretório ( \*opcional\* )** : digite ***WHIZLABS*** . Estaremos atribuindo nossas instâncias EC2 a este nome de domínio.
- Usuário administrativo padrão: **Administrador** , fornecido pelo sistema. Isso é usado para fazermos login assim que a instância for adicionada ao domínio criado acima.
- Senha do administrador: digite ***Whizlabs123*** . Este valor é usado para fazer login na instância como administrador com o nome de domínio acima.
- Confirme a senha: digite ***Whizlabs123\*** fornecido acima.
- Descrição do diretório ( *opcional* ): deixe em branco.
- Clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image92_26_58.png)botão.
- **Etapa 3 - Escolha o VPC e as sub-redes nas quais o AD está presente** .

- **VPC** : selecione o VPC que criamos na **Tarefa 3** .
- **Sub** - **redes** : selecione as 2 sub-redes que foram criadas como parte da **Tarefa 3** .
- Clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image92_28_07.png)botão.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image14.png)

- **Etapa 4 - Revisar e criar**

- Todos os detalhes configurados são exibidos para uma revisão e, uma vez feito isso, clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image39.png)botão.
- Demora cerca de 5 a 10 minutos para esta tarefa ser concluída. Você pode clicar no  ícone **Recarregar** para verificar e, uma vez concluído, o Status mostra **Ativo** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image150.png)

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image61.png)

- Depois que o diretório for criado, clique em **Directory ID** e você será direcionado aos detalhes. Nesta página, clique no  ícone **Recarregar** para encontrar os detalhes.
- A partir dos detalhes exibidos, copie o **endereço DNS** que solicitamos ao trabalhar com o **conjunto de opções DHCP** na próxima tarefa.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image89.png)

**Na criação do Simple AD, o seguinte é criado dentro do ambiente:**

1. Um diretório baseado em Samba é configurado no VPC.
2. Uma conta de administrador do Directory com o nome de usuário **Administrator** é criada. Esta conta é usada para gerenciar o diretório.
3. O grupo de segurança é criado para os controladores de diretório.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image129.png)

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image73.png)

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image6_41_32.png)

1. É criada uma conta com o nome **AWSAdminD-xxxxxxxx** que tem privilégios de administrador de domínio. Essa conta é usada pelo AWS Directory Service para realizar operações automatizadas para operações de manutenção de diretório, como tirar instantâneos de diretório e transferências de função FSMO. As credenciais para esta conta são armazenadas pelo AWS Directory Service.
2. Cria e associa automaticamente uma interface de rede elástica (ENI) a cada um de seus controladores de domínio.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image21.png)

1. Os ENIs criados são necessários para conectividade entre controladores de domínio (DC) VPC e AWS Directory Service e não devem ser excluídos.
2. **Controlador de domínio (DC)** - é um servidor que responde às solicitações de autenticação de segurança em um domínio do Windows Server. É um servidor em uma rede Microsoft Windows ou Windows NT responsável por permitir o acesso do host aos recursos de domínio do Windows.
3. Os DCs são implantados em dois AZs em uma região por padrão e conectados ao VPC. Os backups são feitos automaticamente uma vez por dia e os volumes do EBS são criptografados para garantir que os dados fiquem protegidos em repouso.
4. Quando o DC falha, eles são substituídos automaticamente na mesma Zona de disponibilidade usando o mesmo endereço IP e um DR completo pode ser executado usando o backup mais recente.

**Diferença entre AD e DC** .

- AD é um serviço de diretório que armazena objetos como usuários e computadores. É um banco de dados que armazena a configuração de usuários e computadores no domínio AD.
- DC é o servidor que executa o AD.

### Tarefa 5: Criação de um conjunto de opções DHCP

**Notas :**

- **O protocolo de configuração dinâmica de hosts** (DHCP) fornece um padrão para passar informações de configuração para hosts em uma rede TCP / IP.
- O campo de opções de uma mensagem DHCP contém parâmetros de configuração, incluindo o nome de domínio, servidor de nome de domínio e o tipo de nó netbios.
- A AWS recomenda criar um para seu diretório AWS Directory Service e atribuí-lo ao VPC em que o diretório está. Isso permite que qualquer instância nesse VPC aponte para o domínio especificado e os servidores DNS resolvam seus nomes de domínio.

1. Navegue até o  menu **Serviços** na parte superior e clique em **VPC** presente na  seção **Rede e entrega de conteúdo** .
2. No **painel VPC** exibido, você encontra os detalhes de todos os recursos disponíveis.
3. No lado esquerdo, clique em **Conjuntos de opções DHCP** presentes no menu **NUVEM PRIVADA VIRTUAL** .
4. Na página exibida, haverá poucos DHCP presentes
5. Ignore isso e clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image90.png)botão para criar um para nosso laboratório. Forneça as seguintes informações para criar um e anexar ao nosso VPC.

- **Nome do conjunto de opções DHCP** : digite ***AWS_DHCP\***
- **Nome de domínio** : digite ***whizlabs.com\***
- **Servidores de nome de domínio** : digite os servidores de nome, no meu caso ***10.0.1.108, 10.0.2.140\*** . Estes são os valores gerados quando criamos o diretório na **Tarefa 4** . (Esses valores variam sempre que criamos o diretório.)

![img](https://play.whizlabs.com/frontend/web/media/2021/12/03/screenshot_2021-12-03_125056.png)

- Deixe todas as outras opções e clique no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image90_52_53.png)botão para criar uma.

- Agora precisamos atribuir isso ao VPC.

1. À esquerda, clique em **Seus VPCs** presentes no menu **NUVEM PRIVADA VIRTUAL** . A página exibida à direita exibe a lista de VPCs presentes e selecione aquele que criamos e clique no  menu **Ações** e selecione **Editar conjunto de opções de DHCP** .
2. Na página exibida, selecione o conjunto de opções de DHCP criado acima no menu suspenso e clique no botão **Salvar alterações** .

![img](https://play.whizlabs.com/frontend/web/media/2021/12/03/screenshot_2021-12-03_125523.png)

1. Assim que a alteração for salva, recebemos a mensagem de sucesso abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image102.png)

### Tarefa 6: Criação e configuração do servidor Active Directory

1. Na janela VPC atual, clique em **Painel VPC** e na página exibida. Clique em **Launch EC2 Instances** . 
2. Uma nova guia é aberta, onde podemos começar a configurar a instância para este laboratório, ou seja, **Launch instance wizard | Console de gerenciamento EC2** .
3. **Passo 1: Escolha uma Amazon Machine Image (AMI)** , na barra de pesquisa digite **Windows** e pressione Enter.
4. Somos exibidos com todas as imagens relacionadas ao Windows. À esquerda, marque a caixa **de** seleção **Apenas nível gratuito** .
5. Na lista exibida de AMIs, selecione **Microsoft Windows Server 2012 R2 Base** para nosso laboratório.

![img](https://play.whizlabs.com/frontend/web/media/2021/12/03/screenshot_2021-12-03_125834.png)

1. **Etapa 2: Escolha um tipo de instância** , selecione **t2.micro** o padrão e clique no botão **Configurar detalhes da instância** .
2. **Etapa 3: configurar os detalhes da instância** , forneça os seguintes detalhes.

- Rede: Selecione o VPC criado - **AWS_SAD_VPC**
- Sub-rede: Selecione um da lista - **AWS_SAD_Subnet1 | us-east-1a**
- Auto-atribuir IP público: Selecione **Habilitar**
- Diretório de associação de domínio: Selecione o nome do diretório - **whizlabs.com**
- **Função** IAM: Selecione **AWS_SAD_Role**

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image68.png)

- Deixe o resto das opções como estão e clique no botão **Adicionar armazenamento** .

1. **Etapa 4: Adicionar armazenamento** , sem alterações aqui e clique no botão **Adicionar tags** .
2. **Etapa 5: Adicionar Tags** , clique no botão **Adicionar tag** , Insira o ***Nome\*** como chave e tag como ***SADServer\*** e clique no botão **Configurar Grupo de Segurança** .
3. **Etapa 6: Configure o grupo de segurança** , crie um novo grupo de segurança.

- Atribuir um grupo de segurança: Selecione Criar um **novo** grupo de segurança.
- Nome do grupo de segurança: Digite ***SAD_SG1\***
- Descrição: Digite o ***grupo de segurança para o servidor SAD\* .**
- A AWS nos fornece a porta RDP padrão aberta para esta instância.
- Clique no botão **Revisar e iniciar** .

1. **Etapa 7: Revise o lançamento da instância** , revise os detalhes fornecidos e clique no botão **Iniciar** .
2. Visto que usaremos credenciais de “ **Administrador** ” para fazer o login no servidor Simple AD, não precisamos ter um “ **Par de Chaves** ” criado. Portanto, prosseguiremos sem criar um.

- Selecione **Continuar sem um par de chaves** .
- Marque a caixa de seleção - **eu reconheço** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image176.png)

- Clique em **Launch Instances** para iniciar a instância EC2.

1. Depois que o status de inicialização for apagado, clique no botão **Exibir instâncias** para ver a instância criada.
2. Aguarde alguns minutos para que o estado da Instância esteja no estado “ **Executando** ”.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image175.png)

1. Selecione o servidor acima e, na seção de detalhes, encontraremos os detalhes de - Endereço IP público / DNS IPv4 público / ID de VPC / ID de sub-rede.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image11.png)

### Tarefa 7: Iniciando o servidor Active Directory

1. Aguarde 5 minutos para que a instância se estabilize.
2. Como unimos a instância a um domínio, usaremos as credenciais definidas durante a criação do serviço de diretório.
3. Assim que a instância EC2 for iniciada e o status mudar para “Em **execução** ”, clique na caixa de seleção ao lado do nome do servidor e copie o **DNS IPv4 público** exibido nos detalhes.
4. Certifique-se de ter o aplicativo Remote Desktop em seu computador. Abra o aplicativo Remote Desktop.
5. Na janela exibida, forneça o valor **DNS IPv4 público** copiado e clique no botão Conectar.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image138.png)

1. Na tela exibida, forneceremos um nome de usuário totalmente qualificado para o administrador ( ***whizlabs.com \ Administrador*** ) e a senha ( ***Whizlabs123*** ) e clique no botão OK.

![img](https://play.whizlabs.com/frontend/web/media/2021/12/03/screenshot_2021-12-03_130816.png)

1. Se as credenciais inseridas estiverem corretas, a tela abaixo será exibida e clique no botão Sim para fazer o login na máquina (Servidor AD Simples).

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image57.png)

1. Uma vez conectado à instância EC2, aguarde **5 minutos** para que o servidor fique pronto.
2. Abra **Painel de controle** → **Sistema e segurança** → **Sistema** . Em Nome do computador, domínio e configurações de grupo de trabalho, encontramos o domínio como **whizlabs.com** . Isso ocorre porque lançamos nossa instância EC2 no diretório do domínio.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image169.png)

1. Assim que o sistema estiver pronto, precisamos instalar as **Ferramentas Administrativas do Active Directory** . Para fazer isso, siga estas etapas:

- Abra o Server Manager na tela inicial ou você terá um ícone na bandeja de tarefas ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image12.png).
- Aguarde 2 minutos para que o Gerenciador do Servidor se estabilize e clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image35.png)presente no painel.
- A tela do assistente é exibida e clique aqui no botão **Avançar** , pois precisamos instalar as ferramentas necessárias para trabalhar.
- No tipo de instalação, selecione ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image64.png). Esta opção é selecionada por padrão e clique no botão **Avançar** .
- Na seleção do servidor, você encontrará um nome de computador com o endereço IP privado atribuído pela AWS. Clique no botão **Avançar** .
- Nas Funções do Servidor, não estaremos trabalhando nada e clique no botão **Avançar** .
- Em Recursos, instalaremos as ferramentas necessárias abaixo para nosso laboratório.

- Role para baixo até a caixa de listagem presente e abra **Ferramentas de Administração de Servidor Remoto, Ferramentas de Administração de Função** , selecione **AD DS e Ferramentas AD LDS** , role para baixo e selecione **Ferramentas de Servidor DNS** e clique no botão **Avançar** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image141.png)

- Revise as informações e selecione **Instalar** para instalar as ferramentas.
- A instalação é concluída em alguns minutos e clique no botão **Fechar** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image106.png)

- Assim que a instalação for concluída, você verá que os Serviços de Domínio Active Directory e as Ferramentas dos Serviços Active Directory Lightweight Directory estão disponíveis na tela Iniciar da pasta **Ferramentas Administrativas** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image117.png)

1. Antes de adicionar Usuários / Grupos, desconecte-se do servidor Active Directory, selecione o servidor ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image75.png), clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image43.png)e selecione ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image33_55_53.png). Aguarde alguns minutos e faça login no servidor AD usando **<< nome de domínio \ Administrador >> e senha** .
2. Siga as **etapas 2 a 6** trabalhadas acima para fazer o login no servidor.

**Observação** : se não fizermos login com credenciais de administrador e tentarmos abrir Usuários e computadores do Active Directory, será exibida uma mensagem de erro. Por esse motivo, nos desconectamos do servidor, reinicializamos o sistema e fazemos o login com as credenciais acima.

1. Clique em **Iniciar** → **Ferramentas** Administrativas → A janela Ferramentas Administrativas é exibida.
2. Dê um clique duplo em **Usuários e Computadores** do **Active Directory** , e uma nova janela será exibida onde podemos adicionar Usuários / Grupos.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image108.png)

1. Na captura de tela acima, você pode ver o domínio que adicionamos ao criar o diretório na **Tarefa 4** .
2. Para adicionar usuários, expanda o nome do domínio ou clique com o botão direito no nome do domínio e siga a tela abaixo ou clique com o botão direito em “ **Usuários** ” presente ao lado direito e clique em **Novo** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image164.png)

1. Na tela exibida, forneça as seguintes informações e clique no botão **Avançar** . Aqui estaremos fornecendo as informações básicas.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image142.png)

1. Na próxima tela, forneça a senha ( ***Whizlabs123\*** ) para o usuário e marque A **senha nunca expira** . Simplesmente ignore a mensagem de erro e clique no botão **OK** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image19.png)

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image97.png)

1. C lique no  botão **Avançar** e, em seguida, clique no  botão **Concluir** para criar o usuário.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image22.png)

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image124.png)

### Tarefa 8: registrando com credenciais de usuário

1. Depois de criar um usuário, não podemos usar as credenciais diretamente para fazer o login. Ao fazer isso, obtemos a mensagem de erro abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image155.png)

1. Para resolver o problema acima, precisamos adicionar o usuário para **Gerenciar contas de usuário** com acesso remoto à área de trabalho.
2. Navegue até **Painel de controle → Contas de usuário → Contas de usuário** . Na página exibida, clique em **Gerenciar contas de usuário** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image143.png)

1. Ao clicar no link, uma nova janela pop-up permite ao usuário fornecer detalhes.

- Clique no botão **Adicionar** para adicionar um usuário ao domínio.
- Na tela clique exibido em **B** r **OWSE** botão e na janela exibida inserir o nome de usuário ***james\*** e clique em **Verificar nomes** . Se os detalhes do usuário inseridos estiverem disponíveis, eles serão exibidos e clique no botão **OK** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image4.png)

- O usuário é adicionado na página Adicionar um usuário e agora clique no botão N **ext** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image98.png)

- Na tela exibida, deixe as configurações como estão e clique no botão **Avançar** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image126.png)

- Na próxima tela, clique no botão **Concluir** para que o usuário seja adicionado.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image45.png)

- O usuário é adicionado ao domínio.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image137.png)

- Agora precisamos fornecer ao usuário acesso remoto à área de trabalho e, para isso, clique na guia Avançado.
- Na guia exibida, em Gerenciamento avançado de usuários, clique no botão **Avançar** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image112.png)

- É exibida uma nova janela chamada **Usuários e Grupos Locais e** nesta janela clique no ícone **Grupos** e todos os serviços disponíveis são exibidos.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image114.png)

- Clique duas vezes em Usuários da área de trabalho remota e, na janela pop-up, clique no botão **Adicionar** . Na janela pop-up digite o nome de usuário ***james\*** e clique em **Verificar nomes** para confirmar e, por último, clique no botão OK.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image116.png)

- Assim que o nome for adicionado, clique no botão **Aplicar** para aceitar as alterações.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image147.png)

- Clique no botão **OK** e feche a janela.
- Feche a janela **Usuários e grupos locais** e também a janela Usuários gerenciados.
- Para ver as atualizações da conta do usuário, clique em Gerenciar contas do usuário e, na janela exibida, você encontrará o usuário obtendo permissão para RDP para o sistema.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image127.png)

1. Agora, feche a janela RDP e faça login novamente no RDP com as credenciais abaixo.
2. Use o login como ***whizlabs \ jamesb*** e passe a senha como ***Whizlabs123*** definida no momento da criação.
3. Se o nome de usuário ainda for **whizlabs / administrador** , clique em **Mais opções** e escolha **Usar uma conta diferente** .

![img](https://play.whizlabs.com/frontend/web/media/2021/12/03/screenshot_2021-12-03_145923.png)

1. Pressione o botão **OK** e, na janela exibida, clique no botão Sim para fazer login na máquina virtual.
2. Para confirmar seu login, abra **Painel de controle → Contas de usuário → Contas de usuário** e você encontrará os detalhes do usuário.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image103.png)

### Tarefa 9: Adicionando um computador ao servidor Active Directory

1. Navegue até o  menu **Serviços** na parte superior e clique em **EC2** presente na seção **Computação** .
2. No painel do EC2, clique em **Instâncias** presentes em Instâncias.
3. Na página exibida, clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image158.png). Siga as etapas abaixo para criar uma instância EC2.

- **Passo 1: Escolha uma Amazon Machine Image (AMI)** , na barra de pesquisa digite **Windows** e pressione Enter.
  - Somos exibidos com todas as imagens relacionadas ao Windows. À esquerda, marque a caixa **de** seleção **Apenas nível gratuito** .
  - Na lista exibida de AMIs, selecione **Microsoft Windows Server 2012 R2 Base** para nosso laboratório.

![img](https://play.whizlabs.com/frontend/web/media/2021/12/03/screenshot_2021-12-03_125834_08_20.png)

- **Etapa 2: Escolha um tipo de instância** , selecione **t2.micro** o padrão e clique no botão **Configurar detalhes da instância** .
- **Etapa 3: configurar os detalhes da instância** , forneça os seguintes detalhes.

- **Rede** : Selecione o VPC criado - **AWS_SAD_VPC**
- **Sub** - **rede** : Selecione um da lista - **AWS_SAD_Subnet2 | us-east-1b**
- **Auto-atribuir IP público** : Selecione **Habilitar**
- **Diretório de associação de domínio** : Selecione o nome do diretório - **whizlabs.com**
- **Função** **IAM** : Selecione **AWS_SAD_Role**

- Deixe o resto das opções como estão e clique no botão **Adicionar armazenamento** .

- **Etapa 4: Adicionar armazenamento** , sem alterações aqui e clique no botão **Adicionar tags** .
- **Etapa 5: Adicionar tags** , clique no link - **clique para adicionar uma tag de nome** e fornecer ***SADClient\*** e clique no botão **Configurar grupo de segurança** .
- **Etapa 6: Configurar Grupo de Segurança** , marque Selecionar um grupo de segurança **existente** e selecione **SAD_SG1** que criamos ao criar o Servidor Active Directory.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image119.png)

- Clique no botão **Revisar e iniciar** .
- **Etapa 7: Revise o lançamento da instância** , revise os detalhes fornecidos e clique no  botão **Iniciar** .
  - Visto que usaremos credenciais de “ **Administrador** ” para fazer o login no servidor Simple AD, não precisamos ter um “ **Par de Chaves** ” criado. Portanto, prosseguiremos sem criar um.
- Selecione **Continuar sem um par de chaves** .
- Marque a caixa de seleção - **eu reconheço** .
- Clique em **Launch Instances** para iniciar a instância EC2.
- Aguarde alguns minutos para que o estado da Instância esteja no estado “ **Executando** ”.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image177.png)

1. Faça login na instância acima e abra **Painel de Controle** → **Sistema e Segurança** → **Sistema** → Aqui você encontrará o Nome do Computador. Copie o nome e volte para o servidor do Active Directory.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image8.png)

1. No servidor Active Directory, é exibida a janela **Iniciar** → **Ferramentas** Administrativas → Ferramentas Administrativas.
2. Clique duas vezes em **Usuários e Computadores** do **Active Directory** , e uma nova janela será exibida onde podemos ver o computador adicionado ao Active Directory.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image168.png)

1. O nome é o mesmo que adicionamos recentemente ao diretório.

### Tarefa 10: Excluir recursos da AWS

Excluindo Active Directory Simples

1. Navegue até o  menu **Serviços** na parte superior e clique em **Serviço de diretório** presente no  menu **Segurança, Identidade e Conformidade** .
2. Selecione o ID do diretório criado, clique em **Ações** e selecione **Excluir diretório**
3. Na tela pop-up exibida, forneça o nome do diretório e clique no botão **Excluir** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image99.png)

1. O diretório é excluído em uma duração de 5 a 10 minutos.

### Excluindo Servidor AD Simples

1. Navegue até o  menu **Serviços** na parte superior e clique em **EC2** presente no  menu **Computar** .
2. No painel exibido, clique na **Instância** criada .
3. Clique no **estado da instância** e selecione **Terminate instance** . Confirme a exclusão do servidor clicando no ![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image134_26_05.png)botão.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/15/image149_29_04.png)

### Conclusão e Conclusão

1. Você criou com êxito uma função IAM para trabalhar com os serviços de diretório.
2. Você criou com êxito um VPC e associou um conjunto de opções de DHCP.
3. Você criou e iniciou o Simple Active Directory com sucesso.
4. Você criou grupos, usuários e adicionou computadores com sucesso.
5. Você se logou com sucesso com os usuários criados.