#  Crie e conecte-se ao Amazon FSx usando a instância do Windows

## Introdução

### Amazon FSx 

- Amazon FSx é um servidor de arquivos fornecido para Windows.
- É um sistema de armazenamento de arquivos totalmente gerenciado, altamente escalonável e excepcionalmente confiável que pode ser acessado através do bloco de mensagens do servidor padrão industrial que é o protocolo SMB.
- Ele é baseado no Windows Server, que oferece uma ampla gama de recursos de administração, como kotas do usuário, sistema de arquivos do usuário final e integração com o Microsoft Active Directory.
- Ele também oferece opções de implantação single-AZ e multi-AZ.
- Ele tem backups totalmente gerenciados e dados criptografados em repouso no trânsito.
- O custo pode ser otimizado e o desempenho de suas cargas de trabalho precisa com a opção de armazenamento SSD e HDD.
- Você também pode dimensionar o armazenamento e alterar o desempenho da taxa de transferência do seu sistema de arquivos a qualquer momento.
- O armazenamento de arquivos Amazon FSx pode ser acessado no Windows, mas também podemos acessá-lo em instâncias de computação do Linux e Mac OS e dispositivos em execução na AWS ou no local.
- Ele tem uma capacidade de armazenamento de 32 gb a 64 TB.

# Diagrama de Arquitetura

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/task_281_arch_diagram.png)

# Detalhes da Tarefa

1. Faça login no AWS Management Console.
2. Criação de uma função IAM.
3. Criando um serviço Active Directory para FSx.
4. Criando um grupo de segurança.
5. Criação de instância do Windows EC2 para acessar o sistema de arquivos
6. Criação de um sistema de arquivos Amazon FSx.
7. Criação de instâncias do Windows EC2 para acessar o sistema de arquivos.
8. Conectando-se à instância Whiz_FSx_Write e mapeando o compartilhamento de arquivo na instância.
9. Conectando-se à instância Whiz_FSx_Read e acessando os arquivos no sistema de arquivos.
10. Exclusão de recursos da AWS

## Pré-requisitos

Para prosseguir com o laboratório, você deve ter um aplicativo Remote Desktop em seu computador.

### Para usuários do Windows

1. Clique no botão **Iniciar** e pesquise **RDC** . Você encontrará o aplicativo Remote Desktop Connection.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image26.png)

### Para usuários de Mac

1. No Mac, temos que baixar o aplicativo Remote Desktop.
2. Vá para a App Store, pesquise por **Microsoft Remote Desktop** e baixe o seguinte aplicativo.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image31.png)

### Para usuários Linux

1. No Linux, o **Remmina** geralmente está incluído na distribuição.
2. Caso contrário, vá para https://remmina.org/how-to-install-remmina/ e siga as instruções de instalação para qualquer distribuição Linux.

## Etapas de laboratório

## **Observação: não há teste de validação para este laboratório.**

### Tarefa 2: Criação de uma função IAM

Vamos criar uma função IAM para EC2.

1. Navegue até **IAM** clicando no menu **Serviços** , na seção **Segurança, Identidade e Conformidade** .
2. No menu esquerdo, selecione **Funções** .
3. Clique em **Criar função** .
4. Para **Selecionar tipo de entidade confiável** , selecione **serviço AWS** e escolha **EC2** **.** Em seguida, clique em **Avançar: Permissão**

1. Em Anexar políticas de permissão **,** digite e selecione as seguintes políticas
   - **AmazonFSxFullAccess**
   - **AmazonSSMManagedInstanceCore**
   - **AmazonSSMDirectoryServiceAccess**

**Nota: Não adicione outras políticas além das mencionadas acima. Você obterá um erro ao criar a função.**

1. Em seguida, clique em **Avançar: Tags**
2. Adicionar Tags
   - **Chave** : Digite o *nome*
   - **Valor** : digite **FSx-role**
   - Clique em **Next: Review**
3. Análise
   - **Nome da função**  : insira **a função FSx**
   -  Para a **descrição da função** , digite uma descrição para a nova função.
   - Revise a função e clique em **Criar função** .

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image5.png)

### Tarefa 3: Criando um serviço Active Directory para FSx

Deixe-nos criar um Active Directory para autenticação do usuário e controle de acesso para o seu sistema de arquivos.

1. Certifique-se de que você está na região **us-east-1** do **US East (N.Virginia)** .
2. Navegue até **Serviço de diretório** clicando no menu **Serviços** , na seção **Segurança, Identidade e Conformidade** .
3. Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image14.png).
4. Em **Selecionar tipos de diretório** ,
   - **Tipos de diretório** : Escolha **AWS Managed Microsoft AD**
   - Clique em **Avançar** .
5. Em **Digite as informações do diretório** ,
   - **Edição** : Selecione a **Edição Standard**

- **Nome DNS do diretório** : digite ***WhizFSxAD.com\***
- **Nome do NetBIOS do diretório** : Digite ***WhizFSxAD\***
- **Descrição do diretório** : Insira ***o diretório ativo do Whizlabs FSx lab\***
- **Senha de administrador** : digite ***Whizlabs @ 123\***
- **Confirme a senha** : Digite ***Whizlabs @ 123\***
- Anote a senha em um bloco de notas para uso futuro.

1. Clique em **Avançar** .
2. Em **Escolher VPC e sub-redes** ,
   - Deixe VPC e sub-redes como padrão.
   - Clique em **Avançar** .
3. Em **Revisar e criar** ,
   - Reveja todas as configurações.
4. Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image2.png).
5. O Active Directory leva cerca de 15-20 minutos para ser criado. Espere até que o status do diretório seja **Ativo** .

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image9.png)

### Tarefa 4: Criando um Grupo de Segurança

Vamos criar um grupo de segurança para instância EC2 e sistema de arquivos FSx.

1. Certifique-se de que você está na região **us-east-1** do **US East (N.Virginia)** .

2. Navegue até **EC2** clicando no menu **Serviços** , na seção **Computação** .

3. Navegue até **Grupos de segurança** em **Rede e segurança** no painel esquerdo e clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image17.png).

4. Ao criar o sistema de arquivos FSx, o grupo de segurança deve ter as seguintes regras para permitir o tráfego de rede de saída na porta a seguir, conforme mostrado na captura de tela.

   No entanto, para fins de demonstração, estamos adicionando a regra Todo o tráfego.

1. Em **detalhes básicos** ,
   - **Nome do grupo de segurança** : Digite ***Whiz_SG\***
   - **Descrição** : Enter ***permite todo o tráfego para fins de demonstração\***
   - VPC: VPC padrão
2. Nas **regras de entrada** ,
   - Clique em **Adicionar regra** .
   - Para adicionar **RDP** ,
     - Tipo: Selecione **RDP**
     - Fonte: Selecione **Custom**
     - Na caixa de texto, adicione **0.0.0.0/0**
   - Para adicionar **todo o tráfego** ,
     - Tipo: Selecione **todo o tráfego**
     - Fonte: Selecione **Custom**
     - Na caixa de texto, adicione **0.0.0.0/0**
3. Deixe todas as outras configurações como padrão e clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image17_34_23.png).

### Tarefa 5: criando instâncias do Windows EC2 para acessar o sistema de arquivos

Vamos criar uma instância do Windows EC2.

1. Certifique-se de que você está na região **us-east-1** do **US East (N.Virginia)** .
2. Navegue até **EC2** clicando no menu **Serviços** , na seção **Computação** .
3. Navegue até **Instâncias** no painel esquerdo e clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image25.png)**.**
4. **Escolha uma Amazon Machine Image (AMI):** Procure **Microsoft Windows Server 2019 Base** na caixa de pesquisa e clique no botão de **seleção** .

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image8.png)

1. **Escolha um tipo de instância:** selecione ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image32.png) e clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image33.png)**.**
2. **Configure os detalhes da instância:**
   - **Número de instâncias** : digite o número **2**
   - **Auto-atribuir IP público**  : Escolha **Ativar**
   - **Diretório de associação de domínio** : Selecione **WhizFSxAD.com** que criamos anteriormente.
   - **Função IAM**  : Selecione **a função FSx** que criamos anteriormente.
3. Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image20.png).
4. **Adicionar armazenamento:** Não há necessidade de alterar nada nesta etapa, clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image15.png).
5. **Adicionar tags** : Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image27.png).
   - **Chave**   : Digite o ***nome\***
   - **Valor**   : Insira ***Whiz_FSx\***
   - Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image34.png)
6. Configure o Grupo de Segurança: 
   - Clique em **selecionar um grupo de segurança existente**
   - Selecione ***Whiz_SG*** , que criamos anteriormente.
7. Clique em **Review and Launch** .
8. Revise todas as configurações e clique em **Iniciar** .
9. **Par de chaves** : Clique em **Criar um novo par de chaves** . Deixe o tipo de par de chaves como **RSA** e insira ***whizkey\*** .
10. Clique no **par de chaves Download** e armazene-o em sua máquina local.
11. Clique em . **![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image4.png)**
12. **Status de inicialização:** sua instância está iniciando agora, clique no ID da instância e aguarde a inicialização completa da instância até que o status mude para **Executando** .
13. Agora nomeie as instâncias como **Whiz_FSx_Read** e **Whiz_FSx_Write** para evitar confusão, pois faremos tarefas diferentes em cada instância.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image13.png)

### Tarefa 6: Criando um sistema de arquivos Amazon FSx

Vamos criar um sistema de arquivos Amazon FSx.

1. Certifique-se de que você está na região **us-east-1** do **US East (N.Virginia)** .
2. Navegue até **FSx** clicando no menu **Serviços** , na seção **Armazenamento** .
3. Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image22.png).
4. Em **Selecionar tipo de sistema de arquivos** ,
   - **Opções do sistema de arquivos** : Selecione **Amazon FSx para Windows File Server**
   - Você obterá informações sobre a opção do sistema de arquivos pela qual pode passar.
   - Clique em **Avançar** .
5. Em **detalhes do sistema de arquivos** ,
   - **Nome do sistema de arquivos** : digite ***WhizFSx\***

- **Tipo de implantação** : Selecione **Single-AZ**
  - Deixe **Single-AZ 2** como padrão.
- **Tipo de armazenamento** : Escolha **SSD**
- **Capacidade de armazenamento** : insira **32 GB** (não insira mais do que 32 GB, pois você obterá um erro)
- **Capacidade de transferência** : deixe como padrão

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image1.png)

1. Em **Rede e segurança** ,
   - Nuvem privada virtual (VPC): padrão
   - Grupos de segurança VPC: Remova o grupo de segurança padrão e selecione ***Whiz_SG*** que foi criado anteriormente. ( **Importante** )
   - **Nota** : Seu FSx File System não será criado se você não escolher o grupo de segurança criado acima.
   - Deixe a sub-rede preferencial e a sub-rede em espera como padrão.
2. Na **autenticação do Windows** ,
   - Selecione **Microsoft Active Directory gerenciado pela AWS** .
   - No menu suspenso, selecione ***WhizFSxAD.com***

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image28.png)

1. Deixe todas as outras configurações como padrão.
2. Clique em **Tags** e adicione uma tag.

- **Chave** : Insira as ***informações\***
- **Valor** : Insira ***WhizFSx\***

1. Clique em **Avançar** .
2. Revise todas as configurações e clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image22.png).
3. O sistema de arquivos leva cerca de 15-20 minutos para ser criado. Espere até que o status do sistema de arquivos esteja **Disponível** .

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image12.png)

### Tarefa 7: conectando-se à instância Whiz_FSx_Write e mapeando o compartilhamento de arquivo na instância

Agora você pode montar seu sistema de arquivos Amazon FSx em sua instância do Amazon EC2 com base no Microsoft Windows unida ao diretório AWS Directory Service. Vamos nos conectar à instância primeiro.

#### Conectando-se a Whiz_FSx_Write

1. Certifique-se de que você está na região **us-east-1** do **US East (N.Virginia)** .
2. Navegue até **EC2** clicando no menu **Serviços** , na seção **Computação** .
3. No painel de navegação esquerdo, clique em **Instâncias** .
4. Selecione a instância de gateway de área de trabalho remota, ou seja, **whiz_FSx_Write** e clique em **Conectar** .

**Observação:** neste ponto, você deve ter o cliente RDP instalado em sua máquina local. Caso contrário, siga os pré-requisitos.

1. Navegue até a guia do **cliente RDP** .
2. Clique em **Obter senha** .
3. Clique em **Navegar** e escolha o arquivo **.pem** baixado .
4. Clique em **Descriptografar senha** . Copie a senha descriptografada e salve-a em um editor de texto para uso futuro.
5. Clique em **Baixar arquivo da área de trabalho remota** e salve o arquivo em sua máquina local.
6. Clique e abra o arquivo RDP baixado. Ele deve abrir no cliente RDP que você instalou com o nome de usuário de Administrador.
7. Em Senha, cole a senha descriptografada e clique em **Continuar** .
8. Quando for avisado de que o certificado não pôde ser verificado, clique em **Sim** ou **Continuar** .
9. Agora, você está conectado com êxito à instância de área de trabalho remota.

#### Mapeando o compartilhamento de arquivos na instância

1. Navegue até **FSx** clicando no menu **Serviços** , na seção **Armazenamento** .
2. Selecione o sistema de arquivos que criamos anteriormente. No meu caso, **WhizFSx** .
3. Clique em **Anexar** .
4. Para um sistema de arquivos Single-AZ associado a um Active Directory autogerenciado e qualquer sistema de arquivos Multi-AZ, o nome DNS é semelhante ao seguinte.
   - **amznfsx2i3ulbix.AD-DOMAIN.com**
5. Copie o comando começando em ” **\\** ” e cole em um bloco de notas. No meu caso
   - **\\ amznfsx2i3ulbix.WhizFSx.com \ share**
   - **\\ DNS-NAME \ share** (share é a pasta padrão para FSx)

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image11.png)

1. Navegue até a Área de Trabalho Remota.
2. Clique no **explorador de arquivos** .

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image24.png)

1. Clique em **Este PC** .
2. Na parte superior, clique em **Computador** e selecione **Mapear unidade de rede** na subseção.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image21.png)

1. Cole o comando que copiamos anteriormente no sistema de arquivos. No meu caso
   - **\\ amznfsx2i3ulbix.WhizFSxAD.com \ share**

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image29.png)

1. Depois de clicar em **Concluir** , serão solicitadas as **credenciais de rede** . Aqui você precisa fornecer os detalhes do Active Directory.
   - **Nome de usuário** : Digite ***Admin*** (padrão para todos os AD gerenciados pela Microsoft)
   - **Senha** : Digite ***Whizlabs @ 123*** (esta é a senha de administrador que usamos ao criar o AD). Certifique-se de fornecer a senha correta.
   - Clique **OK** .
2. Você pode ver a pasta criada.

  ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image23.png)

1. Navegue até **este PC** . Você pode ver a pasta nos **locais de rede** .

  ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image30.png)

1. Agora vamos criar algumas pastas e arquivos de amostra.
2. Clique duas vezes na pasta de compartilhamento para abri-la. Crie uma nova pasta **clicando com o botão direito** > **Novo** > **Pasta** . Dê um nome, **Whizlabs** e clique em **Enter** .
3. Da mesma forma, crie 2 ou 3 pastas.

  ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image18.png)

1. Abra qualquer pasta e crie um arquivo. Para fazer isso, **clique com o botão direito do mouse** > **Novo** > **Novo documento de texto** . Dê um nome, **teste** e clique em **Enter** .
2. Clique duas vezes no arquivo de texto, escreva algo e salve em **Arquivo** > **Salvar** .

  ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image7.png)

1. Feche todas as pastas.

### Tarefa 8: conectando-se à instância Whiz_FSx_Read e acessando os arquivos no sistema de arquivos

Vamos nos conectar à instância de leitura e montar o sistema de arquivos nela. Depois de montar o sistema de arquivos, devemos ser capazes de ver as pastas e arquivos que criamos na instância de gravação.

#### Conectando-se a Whiz_FSx_Read

1. Certifique-se de que você está na região **us-east-1** do **US East (N.Virginia)** .
2. Navegue até **EC2** clicando no menu **Serviços** , na seção **Computação** .
3. No painel de navegação esquerdo, clique em **Instâncias** .
4. Selecione a instância de gateway de área de trabalho remota, ou seja, **whiz_FSx_Read** e clique em **Conectar** .

**Observação:** neste ponto, você deve ter o cliente RDP instalado em sua máquina local. Caso contrário, siga os pré-requisitos.

1. Navegue até a guia do **cliente RDP** .
2. Clique em **Obter senha** .
3. Clique em **Navegar** e escolha o arquivo **.pem** baixado .
4. Clique em **Descriptografar senha** . Copie a senha descriptografada e salve-a em um editor de texto para uso futuro.
5. Clique em **Baixar arquivo da área de trabalho remota** e salve o arquivo em sua máquina local.
6. Clique e abra o arquivo RDP baixado. Ele deve abrir no cliente RDP que você instalou com o nome de usuário de Administrador.
7. Em Senha, cole a senha descriptografada e clique em **Continuar** .
8. Quando for avisado de que o certificado não pôde ser verificado, clique em **Sim** ou **Continuar** .
9. Agora, você está conectado com êxito à instância de área de trabalho remota.

#### Mapeando o compartilhamento de arquivos na instância

1. Navegue até **FSx** clicando no menu **Serviços** , na seção **Armazenamento** .
2. Selecione o sistema de arquivos que criamos anteriormente. No meu caso, **WhizFSx** .
3. Clique em **Anexar** .
4. Para um sistema de arquivos Single-AZ associado a um Active Directory autogerenciado e qualquer sistema de arquivos Multi-AZ, o nome DNS é semelhante ao seguinte.
   - **amznfsx2i3ulbix.AD-DOMAIN.com**
5. Copie o comando começando em ” **\\** ” e cole em um bloco de notas. No meu caso
   - **\\ amznfsx2i3ulbix.WhizFSx.com \ share**
   - **\\ DNS-NAME \ share** (share é a pasta padrão para FSx)

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image11.png)

1. Navegue até a Área de Trabalho Remota.
2. Clique no **explorador de arquivos** .

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image24.png)

1. Clique em **Este PC** .
2. Na parte superior, clique em **Computador** e selecione **Mapear unidade de rede** na subseção.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image21.png)

1. Cole o comando que copiamos anteriormente no sistema de arquivos. No meu caso
   - **\\ amznfsx2i3ulbix.WhizFSxAD.com \ share**

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image29.png)

1. Depois de clicar em **Concluir** , serão solicitadas as **credenciais de rede** . Aqui você precisa fornecer os detalhes do Active Directory.
   - **Nome de usuário** : Digite ***Admin*** (padrão para todos os AD gerenciados pela Microsoft)
   - **Senha** : Digite ***Whizlabs @ 123*** (esta é a senha de administrador que usamos ao criar o AD). Certifique-se de fornecer a senha correta.
   - Clique **OK** .
2. Você pode ver as pastas e arquivos que criamos na instância de gravação.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image18.png)

1. Você pode se desconectar da rede **clicando com o botão direito do mouse na pasta de compartilhamento** > **Desconectar** .

### Tarefa 9: Excluir recursos da AWS

### Encerrando instâncias EC2

1. Certifique-se de que você está na região **us-east-1** do **US East** ( **N.Virginia)** .
2. Navegue até o menu **Serviços** no canto superior esquerdo e clique em **EC2** presente na seção **Computação** .
3. Clique em **Instance** .
4. Selecione as instâncias criadas e clique em **Estado da instância** .
5. No menu suspenso, selecione **Terminar instância** .
6. Confirme a rescisão clicando em **Terminar** .

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image35.png)

### Excluindo sistema de arquivos FSx

1. Certifique-se de que você está na região **us-east-1** do **US East (N.Virginia)** .
2. Navegue até **FSx** clicando no menu **Serviços** , na seção **Armazenamento** .
3. Selecione o sistema de arquivos criado e clique em **Ações** .
4. No menu suspenso, selecione **Excluir sistema de arquivos** .
5. Marque **Não** para **Criar backup final** e confirme o mesmo.
6. Copie e cole o ID do sistema de arquivos mencionado na parte superior e clique em **Excluir sistema de arquivos** .

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image6.png)

1. Espere até que o sistema de arquivos seja completamente excluído antes de prosseguir com a exclusão do serviço de diretório ou você receberá uma mensagem de erro.

### Excluindo diretórios

1. Certifique-se de que você está na região **us-east-1** do **US East (N.Virginia)** .
2. Navegue até **Serviço de diretório** clicando no menu **Serviços** , na seção **Segurança, Identidade e Conformidade** .
3. Selecione o diretório criado e clique em **Ações** .
4. No menu suspenso, selecione **Excluir diretório** .
5. Confirme a exclusão digitando o nome do diretório e clique em **Excluir** .

![img](https://play.whizlabs.com/frontend/web/media/2021/09/27/image19.png)

### Conclusão e Conclusão

1. Você criou uma função IAM.
2. Você criou um serviço Active Directory para FSx.
3. Você criou um Grupo de Segurança.
4. Você criou uma instância do Windows EC2 para acessar o sistema de arquivos
5. Você criou um sistema de arquivos Amazon FSx.
6. Você criou instâncias do Windows EC2 para acessar o sistema de arquivos.
7. Você se conectou à instância Whiz_FSx_Write e mapeou o compartilhamento de arquivo na instância.
8. Você se conectou à instância Whiz_FSx_Read e acessou os arquivos no sistema de arquivos.