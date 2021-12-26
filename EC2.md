# O que é EC2?

- A AWS o define como Elastic Compute Cloud.
- É um ambiente virtual onde “você aluga” para ter seu ambiente criado, sem comprar.
- A Amazon se refere a essas máquinas virtuais como instâncias.
- Os modelos pré-configurados podem ser usados para iniciar instâncias. Esses modelos são chamados de imagens. A Amazon fornece essas imagens na forma de AMIs (Amazon Machine Images).
- Permite que você instale aplicativos e serviços personalizados.
- O dimensionamento da infraestrutura, ou seja, para cima ou para baixo, é fácil com base na demanda que você enfrenta.
- A AWS oferece várias configurações de CPU, memória, armazenamento, etc., por meio das quais você pode escolher o tipo que é necessário para o seu ambiente.
- Sem limitação de armazenamento. Você pode escolher o armazenamento com base no tipo de instância na qual está trabalhando.
- Volumes de armazenamento temporário são fornecidos, chamados de Volumes de armazenamento de instância. Os dados armazenados são excluídos assim que a instância é encerrada.
- Volumes de armazenamento persistente estão disponíveis e são chamados de volumes EBS (Elastic Block Store).
- Essas instâncias podem ser colocadas em vários locais, chamados de regiões e zonas de disponibilidade (AZ).
- Você pode ter suas instâncias distribuídas em vários AZs, ou seja, dentro de uma única região, de modo que, se uma instância falhar, o AWS remapeie automaticamente o endereço para outro AZ.
- As instâncias implantadas em um AZ podem ser migradas para outro AZ.
- Para gerenciar instâncias, imagens e outros recursos EC2, você pode opcionalmente atribuir seus próprios metadados a cada recurso na forma de tags.
- Um Tag é um rótulo que você atribui a um recurso da AWS. Ele contém uma chave e um valor opcional, ambos definidos por você.
- Cada conta da AWS vem com um conjunto de limites padrão sobre os recursos por região.
- Para qualquer aumento no limite, você precisa entrar em contato com a AWS.
- Para trabalhar com as instâncias criadas, usamos pares de chaves.

## Lançando máquina EC2 e SSH usando Putty

![img](https://play.whizlabs.com/frontend/web/media/2020/06/04/task_id_144__launching_ec2_machine_and_ssh_using_putty_(1).png)

Detalhes da Tarefa

1. Inicie uma instância do Amazon Linux a partir de um Amazon Linux AMI 2
2. Encontre sua instância no AWS Management Console.
3. SSH em sua instância para usuários Mac.
4. SSH em sua instância para usuários do Windows.
5. Execute alguns outros comandos úteis.

### Etapas de laboratório

#### Tarefa 1: iniciando uma instância EC2

1. Certifique-se de que você está na região **us-east-1 do leste** dos **EUA (Virgínia do Norte)** .
2. Navegue até **EC2** clicando no ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image20.png)menu na parte superior e, a seguir, clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image19.png)na ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image21.png)seção.
3. Navegue até **Instâncias** no painel esquerdo e clique em **Iniciar Instância.**

1. **Pesquise e escolha Amazon Linux 2 AMI:**

   **![img](https://play.whizlabs.com/frontend/web/media/2020/07/30/linux_2_ami_09_09.png)**

2. **Escolha um tipo de instância:** selecione ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image31.png)e clique em Próximo: Configurar detalhes da instância

    

3. **Configurar detalhes da instância: não** há necessidade de alterar nada nesta etapa, clique em **Próximo: Adicionar armazenamento**

4. **Adicionar armazenamento: não** há necessidade de alterar nada nesta etapa, clique em **Próximo: Adicionar tags**

5. **Adicionar Tags:** Clique em **Adicionar Tags**

   - Chave: Digite o ***nome\***
   - Valor: Insira ***MyEC2Server\***
   - Clique em **Configurar Grupo de Segurança**

6. Configure o Grupo de Segurança:

   - Atribua um grupo de segurança: Verifique (Criar um novo grupo de segurança)
   - Nome do grupo de segurança: Digite ***whizlabs_SG\***
   - Descrição: Insira uma descrição do grupo de segurança para o ***whizlabs_SG\***
   - Para adicionar **SSH:**
     - Escolha o tipo: ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image17.png)
     - Fonte: Anywhere (de TODOS os endereços IP acessíveis).
   - Depois disso, clique em **Review and Launch**

7. **Revisar e iniciar:** Revise todas as configurações e clique em Iniciar.

8. **Par de chaves:** Selecione “Criar um novo par de chaves”, nomeie o par de chaves e clique em **Baixar par de chaves** . Depois disso, clique em **Launch Instances** .

9. **Status de inicialização:** sua instância agora está sendo iniciada. Clique em **Exibir instâncias** . No painel, encontre sua instância e aguarde a inicialização completa da instância até que o estado da instância mude para execução.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/01/task_2_step_14.jpg)

1. Observe o endereço IP público IPv4 da instância EC2. Um exemplo é mostrado na imagem abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/01/task_2_step_15.jpg)

#### Tarefa 2: SSH na instância EC2

##### Linux

1. Abra o terminal.
2. Navegue até o local onde seu **par de chaves** foi baixado e armazenado em sua máquina local.
3. Para atualizar as **permissões** , execute o seguinte comando
   - **chmod 400 keypair** (digite o nome do seu par de chaves)

![img](https://play.whizlabs.com/frontend/web/media/2021/05/19/screen_shot_2021-05-19_at_4.02.34_pm.png)

1. Para fazer SSH e conectar-se à instância EC2, digite o seguinte comando:
   - Sintaxe: **ssh -i keypair ec2-user @ publicIPAddress** (digite o endereço público que você salvou anteriormente)
   - Amostra: **ssh -i** **keypair** **ec2-user@107.21.198.65**
   - Em seguida, digite **sim** e pressione **Enter.** Você será conectado com êxito à instância EC2.

![img](https://play.whizlabs.com/frontend/web/media/2021/05/19/screen_shot_2021-05-19_at_4.04.53_pm.png)

##### Windows

1. ##### Baixe o putty e o puttygen neste link: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

2. Para converter seu par de chaves .pem em .ppk:

   - Aberto ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image36.png).
   - Clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image9.png).
   - Clique em **Todos os arquivos** para mostrar seu arquivo .pem e selecione o **arquivo .pem** .
   - Você receberá uma mensagem de sucesso se feito corretamente.

![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image23.png)

- Clique em **Salvar chave privada** .
- Digite o nome do ***par de chaves\*** e **salve** .
- **O** arquivo **keypairname.ppk** será salvo em sua máquina local.

1. Navegue até a página da instância EC2 e obtenha o IP público da máquina.
2. Aberto ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image33.png)
   - Nome do host: digite o endereço IP público

![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image6.png)

- Clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image8.png) , selecione ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image16.png) e clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image14.png) para selecionar a chave privada (.ppk) que você converteu do arquivo .pem.
- Clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image25.png).

![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image34.png)

- Selecione ![img](https://lh6.googleusercontent.com/NFlvMEs15U1z5w8L_IZ5iUjK875gVNdRSER65LwJRcoKP9cD-VpNlAZN6Iednkmkt17eHhw4o6Fd920h4uVRvTavG5ioBAI93Eudfe3UNu6s7QOKhMIDKHTemyn8o7awfgjxSCeg)para se conectar à máquina.

![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image27.png)

1. Se você estiver usando Linux AMI diferente do Ubuntu para o laboratório:
   - Insira o nome de usuário: **ec2-user** e pressione Enter.

![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image32.png)

**Nota:** Se você estiver usando o Ubuntu AMI para o laboratório: Digite o nome de usuário: ***ubuntu\*** e pressione Enter.

1. Você verá o console após um login bem-sucedido.

![img](https://play.whizlabs.com/frontend/web/media/2020/02/18/image28.png)

#### Tarefa 3: Execução de comandos

1. Mudar para usuário root: **sudo -s**
2. Execute atualizações usando o seguinte comando: 
   - **yum -y atualização**
3. Para encontrar seu diretório de trabalho atual, digite o comando **pwd**
4. Digite o comando **exit** e **saia** novamente para fazer logoff do Putty.

## Iniciando a máquina EC2 e conectando-se por meio de SSH baseado em navegador

![img](https://play.whizlabs.com/frontend/web/media/2020/06/04/task_id_145_launching_ec2_machine_and_connecting_through_browser-based_ssh_30_44.png)

Detalhes da Tarefa

1. Faça login no AWS Management Console.
2. Inicie uma instância do Amazon Linux a partir de um Amazon Linux AMI 2
3. Encontre sua instância no AWS Management Console.
4. Conectando-se à sua instância por meio do EC2 Instance Connect.
5. Validação do laboratório

### Etapas de laboratório

#### Tarefa 1: iniciando uma instância EC2

1. Certifique-se de que você está na região **us-east-1 do leste** dos **EUA (Virgínia do Norte)** .
2. Navegue até **EC2** clicando no ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image7.png) menu na parte superior e, a seguir, clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image4.png) na ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image27.png) seção.
3. Clique em **Instâncias** no painel esquerdo e clique em  **Iniciar Instância.**

1. **Pesquise e escolha Amazon Linux 2 AMI:** 

   ![img](https://play.whizlabs.com/frontend/web/media/2020/07/30/linux_2_ami_08_50.png)

2. **Escolha um tipo de instância:** selecione ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image15.png) e clique em Configurar detalhes da instância

3. **Configurar detalhes da instância:** Não há necessidade de alterar nada nesta etapa. Clique em **Next: Add Storage**

4. **Adicionar armazenamento: não** há necessidade de alterar nada nesta etapa. Clique em **Avançar: Adicionar Tags**

5. **Adicionar Tags:** Clique em **Adicionar Tag**

   - Chave: Digite o ***nome\***
   - Valor: Insira ***whizlabs\***
   - Clique em **Avançar: Configurar Grupo de Segurança**

6. Configure o Grupo de Segurança:

   - Atribua um grupo de segurança: Verifique (Criar um novo grupo de segurança)
   - Nome do grupo de segurança: Digite ***whizlabs_SG\***
   - Descrição: Insira uma descrição do grupo de segurança para o **whizlabs_SG**
   - Para adicionar **SSH:**
     - Fonte: Custom (Permitir endereço IP específico) ou Anywhere (De TODOS os endereços IP acessíveis).
     - Escolha o tipo: ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image3.png)
     - Depois disso, clique em **Review and Launch**

**Par de chaves:** como estamos usando SSH baseado em navegador, não precisamos de um par de chaves. Selecione **Prosseguir sem um par de chaves** , verifique a confirmação e clique em **Iniciar Instâncias** .

**Revisar e iniciar:** Revise todas as configurações e clique em **Iniciar** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/10/1.png)

1. **Status de inicialização:** sua instância agora está sendo iniciada. Clique em **Exibir instâncias.** No painel, encontre sua instância e aguarde a inicialização completa da instância até que o estado da instância mude para execução.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/01/whizlabs_ec2.jpg)

1. Sua instância foi iniciada com sucesso e está em execução.

#### Tarefa 2: conexão de instância EC2

1. Usando o EC2 Instance Connect, podemos nos conectar diretamente à nossa instância a partir do console.
2. Selecione sua instância.
3. Clique em **Conectar** .

1. Você verá 4 tipos de métodos de conexão. Escolha **EC2 Instance Connect (conexão SSH baseada em navegador)** e clique em **Connect** .

![img](https://play.whizlabs.com/frontend/web/media/2021/06/10/3.png)

1. Sua instância será conectada ao SSH por meio de seu navegador.

![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image18.png)

#### Tarefa 3: Execução de comandos

1. Mudar para usuário root: **sudo -s**
2. Execute atualizações usando o seguinte comando: 
   - **yum -y atualização**
3. Para encontrar seu diretório de trabalho atual, digite o comando **pwd**
4. Digite o comando **exit** e **saia** novamente para fazer logout.

Dessa forma, você pode se conectar à sua instância usando SSH do console sem usar um par de chaves.

## Alocando Elastic IP e Associando-o à Instância EC2

![img](https://play.whizlabs.com/frontend/web/media/2020/06/04/task_id_78_allocating_elastic_ip_and_associating_it_to_ec2_instance_17_53.png)

Detalhes da Tarefa

1. Crie uma instância do Amazon Linux a partir de um Amazon Linux AMI
2. SSH em sua instância e configure seu servidor como um servidor web.
3. Crie e publique um arquivo test.html de amostra.
4. Teste a página com o endereço IP público da Instância EC2 criada.
5. Aloque um Elastic IP e associe-o à instância EC2.
6. Teste a página com o endereço Elastic IP da instância EC2.
7. Validação do laboratório

Pré-requisitos

1. Baixe o putty e o puttygen neste link: [https://www.chiark.greenend.org.uk/~sgtatham/putty/ ](https://www.chiark.greenend.org.uk/~sgtatham/putty/releases/0.74.html)[releases / 0.74.html](https://www.chiark.greenend.org.uk/~sgtatham/putty/releases/0.74.html) 

### Etapas de laboratório

**Observação:** se você enfrentar qualquer problema, consulte as [**perguntas frequentes e a solução de problemas para laboratórios**](https://play.whizlabs.com/site/task_support/faqs-and-troubleshooting) .

#### Tarefa 1: iniciando uma instância EC2

1. Certifique-se de que você está na região **us-east-1 do leste** dos **EUA (Virgínia do Norte)** .
2. Navegue até **EC2** clicando no ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image35.png) menu na parte superior e, a seguir, clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image12_28_50.png) na ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image28.png) seção.
3. Navegue até **Instâncias** no painel esquerdo e clique em **Iniciar Instâncias.**
4. **Pesquise e escolha Amazon Linux 2 AMI:**
   ![img](https://play.whizlabs.com/frontend/web/media/2020/07/30/al_2_ami_41_09.png)
5. **Escolha um tipo de instância:** selecione ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image19_30_45.png) e clique em **Configurar detalhes da instância**
6. **Configurar detalhes da instância: não** há necessidade de alterar nada nesta etapa, clique em **Próximo: Adicionar armazenamento**
7. **Adicionar armazenamento: não** há necessidade de alterar nada nesta etapa, clique em **Próximo: Adicionar tags**
8. **Adicionar Tags:** Clique em **Adicionar Tag**
   - Chave: Digite o ***nome\***
   - Valor: Insira ***MyEC2Server\***
   - Clique em **Avançar: Configurar Grupo de Segurança**
9. Configure o Grupo de Segurança:
   - Atribua um grupo de segurança: Verifique (Criar um novo grupo de segurança)
   - Nome do grupo de segurança: Digite ***whizlabs_SG\***
   - Descrição: Insira uma descrição do grupo de segurança para o ***whizlabs_SG\***
   - Para adicionar **SSH** ,
     - Escolha o tipo: ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image36.png)
     - Fonte: ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image14_33_51.png) (Permitir endereço IP específico) ou ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image2_34_13.png)(Acessível a partir de TODOS os endereços IP).
   - Para **HTTP,**
     - Clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image22_33_24.png)
     - Escolha o tipo: **HTTP** 
     - Fonte: ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image14_33_51.png) (Permitir endereço IP específico) ou ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image2_34_13.png) (Acessível a partir de TODOS os endereços IP).
   - Depois disso, clique em **Review and Launch**
10. **Revisar e iniciar:** Revise todas as configurações e clique em **Iniciar** .
11. **Par de chaves:** Crie um novo par de chaves e clique em **Baixar** par de chaves e, em seguida, clique em **Iniciar instâncias** .
12. **Status de inicialização:** sua instância agora está sendo iniciada. Clique em **Exibir instâncias.** No painel, encontre sua instância e aguarde a inicialização completa da instância até que o estado da instância mude para execução.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/02/task_2_step_14_33_52.jpg)

1. Selecione a instância que você criou e, abaixo, em Detalhes, observe o endereço IP público IPv4 da instância EC2. Um exemplo é mostrado na imagem abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/02/task_2_step_15_34_27.jpg)

#### Tarefa 2: SSH na instância EC2

- Siga as etapas em [SSH para a instância EC2](https://play.whizlabs.com/site/task_support/ssh-into-ec-instance) .

#### Tarefa 3: instale um servidor Apache

1. Mudar para usuário root
   -  **sudo su**
2. Agora execute as atualizações usando o seguinte comando: 
   - **yum -y atualização**
3. Depois de concluído, vamos instalar e executar um servidor apache
   - Instale o servidor da web Apache: 
     - **yum install httpd**
   - Quando solicitado, pressione **"Y"** para confirmar.
   - Inicie o servidor web 
     - **systemctl start httpd**
   - Agora habilite httpd: 
     - **systemctl enable httpd**
   - Verifique o status do servidor web
     - **systemctl status httpd**
   - Você pode ver que o status ativo está em execução.
   - Você pode testar se o seu servidor da web está instalado e inicializado corretamente digitando o **endereço IPv4 público** da sua **instância EC2** na barra de endereços de um navegador da web. Se o seu servidor da web estiver em execução, você verá a página de teste do Apache. Se você não vir a página de teste do Apache, verifique se você seguiu as etapas acima corretamente e verifique suas regras de entrada para o grupo de segurança que você criou.
   - Certifique-se de que o **protocolo de URL** seja **http,** não https.

Sintaxe: **http: // <Your_Public_IPv4_Address>**

Exemplo: **http://3.80.149.180**

#### Tarefa 4: crie e publique a página

1. Depois de instalar o servidor apache, navegue até a pasta html onde colocaremos nossa página html para ser publicada. Use o comando:
   - **cd / var / www / html /**
2. Crie um arquivo **test.html de** amostra usando o editor nano: 
   - **nano** **test.html**
3. Insira o conteúdo HTML de amostra fornecido abaixo no arquivo e salve o arquivo com **Ctrl + X.** Clique em **Y** para confirmar o salvamento e pressione **Enter** para confirmar o nome do arquivo.
   - **<HTML> Olá Whizlabs, sou uma página pública </HTML>**
4. Reinicie o servidor da web usando o seguinte comando: 
   - **systemctl restart httpd**
5. Agora insira o nome do arquivo, ou seja, ***/test.html\*** após o **endereço IPv4 público** que você obteve ao criar a instância ec2 no navegador, e você poderá ver seu conteúdo HTML.
   - Certifique-se de que o **protocolo de URL** seja **http,** não https.
   - Sintaxe: **http: // <Your_Public_IPv4_Address> /test.html**
   - URL de amostra: **52.90.56.138/test.html**

​        *![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image15_39_57.png)*

 

1. Agora navegue até o painel de instâncias EC2, selecione **MyEC2Server** e clique em parar instância na seção de estado de instância. (Anote o endereço IP) 

![img](https://play.whizlabs.org/frontend/web/media/2021/11/16/instance_43_55.png)

1. Agora confirme clicando no botão **Parar** .

![img](https://play.whizlabs.org/frontend/web/media/2021/11/16/stop.png)

1. Espere até que a instância seja interrompida e agora clique no botão **Iniciar instância** na seção de estado da instância.

![img](https://play.whizlabs.org/frontend/web/media/2021/11/16/start.png)

1. Depois que a instância for iniciada, compare o novo endereço IP alocado com o novo, você pode observar que o endereço IP público da instância EC2 foi alterado.

#### Tarefa 5:  Alocando Endereço Elastic IP

1. Para usar um endereço Elastic IP, você precisa alocar um para sua conta e, em seguida, associá-lo à sua instância ou interface de rede.
2. Navegue até **EC2** . Sob ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image13_40_25.png) clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image16_47_42.png) sob ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image29.png) a seção.
3. Clique em **Allocate Elastic IP address**
4. Mantenha tudo como padrão e clique no botão **Alocar** .

![img](https://play.whizlabs.com/frontend/web/media/2021/07/02/task_6_step_4.jpg)

1. Você pode ver que o Elastic IP foi alocado com sucesso conforme mostrado abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/02/task_6_step_5.jpg)

#### Tarefa 6: Associando um endereço Elastic IP a uma instância em execução

1. Selecione o endereço Elastic IP criado e clique em **Ações** . Clique em **Associate Elastic IP address** .

![img](https://play.whizlabs.com/frontend/web/media/2021/07/02/task_7_step_1.jpg)

1. **Endereço de IP Elastic associado**
   - Tipo de recurso: Clique na **instância** 
   - Escolha sua instância no menu suspenso, conforme mostrado abaixo. 
   - Deixe os valores padrão para os campos restantes e clique em **Associar.**

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image24.png)

1. Agora você pode ver que a instância está associada ao endereço Elastic IP.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/02/task_7_step_3.jpg)

1. Vá para a instância **EC2** e verifique o IP público IPv4 e deve ser igual ao Elastic IP. 

![img](https://play.whizlabs.com/frontend/web/media/2021/07/02/task_7_step_4.jpg)

1. Em seguida, verificaremos a página da web inserindo o endereço Elastic IP em vez do IP público anterior.
   -  URL de amostra: **3.208.115.72/test.html**

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image10_53_44.png)

1. Agora navegue até o painel de instâncias EC2, selecione **MyEC2Server** e clique em parar instância na seção de estado de instância (anote o endereço IP) 

![img](https://play.whizlabs.org/frontend/web/media/2021/11/16/instance_51_54.png)

1. Agora confirme clicando no botão **Parar** .

![img](https://play.whizlabs.org/frontend/web/media/2021/11/16/stop.png)

1. Espere até que a instância seja interrompida e agora clique no botão **Iniciar instância** na seção de estado da instância.

![img](https://play.whizlabs.org/frontend/web/media/2021/11/16/start.png)

1. Espere até a instância iniciar. Agora você pode observar que, depois de anexar o IP elástico, mesmo depois de reiniciar, você pode ver o mesmo endereço IP público. Isso nos impede de mapear outro endereço, mesmo em caso de falhas nas instâncias.

## Crie, pare, inicie, reinicie e encerre uma instância EC2

![img](https://play.whizlabs.com/frontend/web/media/2020/06/13/task_id_79__create_stop_start_reboot_and_terminate_an_ec2_instance_(2).png)

Detalhes da Tarefa

1. Faça login no AWS Management Console.
2. Iniciando uma instância EC2
3. SSH na instância EC2
4. Instale um servidor Apache
5. Criar e publicar página
6. Interrompendo a instância em execução
7. Iniciando a instância interrompida
8. Reinicializar a instância em execução
9. Encerrando a instância em execução





### Etapas de laboratório

#### Tarefa 1: iniciando uma instância EC2

1. Certifique-se de estar na região da **Virgínia** .
2. Navegue até **EC2** clicando no ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image35.png) menu na parte superior e, a seguir, clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image12_28_50.png) na ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image28.png) seção.
3. Navegue até **Instâncias** no painel esquerdo e clique em **Iniciar Instâncias**
4. **Escolha uma Amazon Machine Image (AMI):** Pesquise **Amazon Linux 2 AMI** na caixa de pesquisa e clique no botão de **seleção** .
   ![img](https://play.whizlabs.com/frontend/web/media/2020/07/30/al_2_ami_39_34.png)
5. **Escolha um tipo de instância:** selecione ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image19_30_45.png) e clique em **Próximo: Configurar detalhes da instância**
6. **Configurar detalhes da instância: não** há necessidade de alterar nada nesta etapa, clique em **Próximo: Adicionar armazenamento**
7. **Adicionar armazenamento: não** há necessidade de alterar nada nesta etapa, clique em **Próximo: Adicionar tags**
8. **Adicionar Tags:** Clique em **Adicionar Tag** 
   - Chave: Digite o ***nome\***
   - Valor: Insira ***MyEC2Server\***
   - Clique em **Avançar: Configurar Grupo de Segurança**
9. Configure o Grupo de Segurança:
   - Atribua um grupo de segurança: Verifique (Criar um novo grupo de segurança)
   - Nome do grupo de segurança: Digite ***whizlabs_SG\***
   - Descrição: Insira uma descrição do grupo de segurança para o **whizlabs_SG**
   - Para adicionar **SSH:**
     - Escolha o tipo: ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image36.png)
     - Fonte: ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image14_33_51.png) (Permitir endereço IP específico) ou ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image2_34_13.png) (Acessível a partir de TODOS os endereços IP).
   - Para **HTTP:**
     - Clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image22_33_24.png)
     - Escolha o tipo: **HTTP** 
     - Fonte: ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image14_33_51.png) (Permitir endereço IP específico) ou ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image2_34_13.png) (Acessível a partir de TODOS os endereços IP).
   - Para **HTTPS:**
     - Clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image22_33_24.png)
     - Escolha o tipo: **HTTPS** 
     - Fonte: ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image14_33_51.png) (Permitir endereço IP específico) ou ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image2_34_13.png) (Acessível a partir de TODOS os endereços IP).
   - Depois disso, clique em **Review and Launch.**
10. **Revisar e iniciar:** Revise todas as configurações e clique em **Iniciar** .
11. **Par de chaves:** Selecione **Criar um novo par de chaves** , nomeie o par de chaves e clique em **Baixar par de chaves** . Depois disso, clique em **Launch Instances** .
12. **Status de inicialização:** sua instância agora está sendo iniciada. Clique em **Exibir instâncias.** No painel, encontre sua instância e aguarde a inicialização completa da instância até que o estado da instância mude para execução.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/30/task_2_step_14.jpg)

1. Selecione a instância que você criou e, abaixo, em Detalhes, observe o endereço IP público IPv4 da instância EC2. Um exemplo é mostrado na imagem abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/30/task_2_step_15.jpg)

#### Tarefa 2: SSH na instância EC2

- Siga as etapas em [SSH para a instância EC2](https://play.whizlabs.com/site/task_support/ssh-into-ec-instance) .

#### Tarefa 3: instale um servidor Apache

1. Mudar para usuário root
   - **sudo -s**
2. Agora execute as atualizações usando o seguinte comando: 
   - **yum -y u**
3. Depois de concluído, vamos instalar e executar um servidor apache
   - Instale o servidor da web Apache: 
     - **yum install httpd**
   - Quando solicitado, pressione **"Y"** para confirmar.
   - Inicie o servidor web 
     - **systemctl start httpd**
   - Habilite httpd: 
     - **systemctl enable httpd**
   - Verifique o status do servidor web
     - **systemctl status httpd**
   - Você pode ver que o status Ativo está em execução.
   - Você pode testar se o seu servidor da web está instalado e inicializado corretamente digitando o endereço IP público da sua instância EC2 na barra de endereços de um navegador da web. Se o seu servidor web estiver rodando, você verá a página de teste do Apache. Se você não vir a página de teste do Apache, verifique se você seguiu as etapas acima corretamente e verifique suas regras de entrada para o grupo de segurança que você criou.

#### Tarefa 4: crie e publique a página

1. Navegue até a pasta HTML onde colocaremos nossa página html para ser publicada.
   - **cd / var / www / html /**
2. Crie um arquivo **test.html de** amostra usando o editor nano: 
   - **nano** **test.html** 
3. Insira o conteúdo HTML de amostra fornecido abaixo no arquivo e salve o arquivo com **Ctrl + X** , clique em **Y** para confirmar o salvamento e pressione **Enter** para confirmar o nome do arquivo.
   - **<HTML> Olá Whizlabs, sou uma página pública </HTML>**
4. Reinicie o servidor da web usando o seguinte comando: 
   - **systemctl restart httpd**
5. Agora insira o nome do arquivo após o IP público de quando você criou a instância ec2 no navegador, e você pode ver seu conteúdo HTML.
   - URL de amostra: **52.90.56.138/test.html**

​        *![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image15_39_57.png)*

#### Tarefa 5: parando a instância em execução

- Selecione sua instância EC2, clique no **estado da instância** e selecione **Parar instância.**
- A instância executa um desligamento normal e para de funcionar. Seu status muda para **parando** e depois **parado** .
- Todos os volumes do Amazon EBS permanecem anexados à instância e seus dados persistem.
- Todos os dados armazenados na RAM do computador host ou nos volumes de armazenamento de instância do computador host são perdidos.
- Você pode alterar o tipo de instância, os dados do usuário e os atributos de otimização EBS de uma instância interrompida.
- A AWS não cobra pelo uso de uma instância interrompida ou taxas de transferência de dados, mas cobra pelo armazenamento de quaisquer volumes do Amazon EBS. Este recurso é útil para instâncias não utilizadas por algum tempo.
- Se você acessar a página da web e atualizar, haverá um TimeOut, pois o IP público IPv4 não existirá se uma instância for interrompida. 

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image24_26_09.png)

#### Tarefa 6: Iniciando a instância interrompida

- Selecione sua instância EC2, clique em **Estado da instância** e selecione **Iniciar instância** .
- O status muda de **parado** para **pendente** . Após alguns minutos, o status muda para executando
- Um novo IP público IPv4 será atribuído à instância.
- Se você abrir uma página da web com esse endereço IP, poderá ver seu conteúdo HTML
  - URL de amostra: **3.86.82.65/test.html**

![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image36_27_40.png)

#### Tarefa 7: reiniciando a instância em execução

- Uma reinicialização da instância é equivalente a uma reinicialização do sistema operacional. Na maioria dos casos, leva apenas alguns minutos para reinicializar sua instância. 
- Quando você reinicializa uma instância, ela permanece no mesmo host físico para que sua instância mantenha seu nome DNS público (IPv4), endereço IPv4 privado, endereço IPv6 (se aplicável) e quaisquer dados em seus volumes de armazenamento de instância.
- Para reinicializar, selecione a instância EC2, clique em **Estado da instância** e selecione **Reinicializar instância.**
- Escolha Sim, reinicializar quando for solicitada a confirmação.

Tarefa 9: Encerrando a instância em execução

- Você pode excluir sua instância quando não precisar mais dela. Isso é conhecido como encerramento de sua instância. 
- Para encerrar, selecione a instância EC2 , clique em **Estado da instância** e selecione **Encerrar instância** .

- Assim que o estado de uma instância muda para **encerrando** ou **encerrado** , você para de incorrer em cobranças por essa instância.
- Você não pode se conectar ou iniciar uma instância depois de encerrá-la. 
- **Observação: este laboratório não tem uma opção de validação. Agora você pode optar por encerrar o laboratório.**

## Crie uma instância EC2 e conecte-se a uma máquina Windows usando RDC

![img](https://play.whizlabs.com/frontend/web/media/2021/09/28/rdc_architecture.png)

Detalhes da Tarefa

1. Faça login no AWS Management Console.
2. Crie uma instância do Amazon Windows a partir do Microsoft Windows Server.
3. Conecte sua instância EC2 usando a Conexão de Área de Trabalho Remota.
4. Instalando o servidor IIS usando a linha de comando.
5. Testando a página da Web padrão.
6. Criando uma página da Web personalizada.
7. Validação do laboratório.

### Pré-requisitos

Para prosseguir com o laboratório, você deve ter um aplicativo Remote Desktop em seu computador.

#### Para usuários do Windows

1. Clique no botão **Iniciar** e pesquise **RDC** . Você encontrará o aplicativo Remote Desktop Connection.

![img](https://play.whizlabs.com/frontend/web/media/2021/05/19/open-remote-desktop-connection-by-search.png)

#### Para usuários de Mac

1. No Mac, temos que baixar o aplicativo Remote Desktop.
2. Vá para a App Store, pesquise por **Microsoft Remote Desktop** e baixe o seguinte aplicativo.

![img](https://play.whizlabs.com/frontend/web/media/2021/05/19/screen_shot_2021-05-19_at_11.59.44_am.png)

#### Para usuários Linux

1. No Linux, o **Remmina** geralmente está incluído na distribuição.
2. Caso contrário, vá para https://remmina.org/how-to-install-remmina/ e siga as instruções de instalação para qualquer distribuição Linux.





### Etapas de laboratório

#### Tarefa 1: iniciando uma instância EC2

1. Certifique-se de que você está na região **us-east-1 do leste** dos **EUA (Virgínia do** Norte).

2. Navegue até **EC2** clicando no ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image35.png) menu na parte superior e, a seguir, clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image12_28_50.png) na ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image28.png) seção.

3. Navegue até **Instâncias** e clique em **Iniciar Instâncias.**

4. **Escolha uma Amazon Machine Image (AMI):** Procure ***Windows*** e selecione esta AMI

   

5. **Escolha um tipo de instância:** Selecione ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image19_30_45.png) e clique em **Configurar detalhes da instância**

6. **Configurar detalhes da instância:** Não há necessidade de alterar nada nesta etapa. Clique em **Next: Add Storage**

7. **Adicionar armazenamento: não** há necessidade de alterar nada nesta etapa. Clique em **Avançar: Adicionar Tags**

8. **Adicionar Tags:** Clique em **Adicionar Tag**

   - Chave: Digite o ***nome\***
   - Valor: Insira ***MyEC2Server\***
   - Clique em **Avançar: Configurar Grupo de Segurança**

9. Configure o Grupo de Segurança:

   - Atribua um grupo de segurança: Verifique (Criar um novo grupo de segurança)
   - Nome do grupo de segurança: Digite ***whizlabs_SG\***
   - Descrição: Digite o ***grupo de segurança para o whizlabs_SG***
   - Para adicionar **RDP:**
     - Escolha o tipo: ![img](https://play.whizlabs.com/frontend/web/media/2020/01/21/rdp_sg.png)
     - Fonte: ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image14_33_51.png) (Permitir endereço IP específico) ou ![img](https://play.whizlabs.com/frontend/web/media/2020/01/20/image2_34_13.png) (Acessível a partir de TODOS os endereços IP).
   - Depois disso, clique em **Review and Launch**

10. **Revisar e iniciar:** Revise todas as configurações e clique em **Iniciar** .

11. **Par de chaves** - Escolha **Criar um novo par de chaves**

    - Tipo de par de chaves: Selecione **RSA**
    - Nome do par de chaves: digite **My_EC2_Key**

12. **Status de inicialização:** sua instância agora está sendo iniciada. Clique em **Exibir instâncias.** No painel, encontre sua instância e aguarde a inicialização completa da instância até que o estado da instância mude para execução.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/02/task_2_step_14_23_17.jpg)

   \13. Selecione a instância que você criou e, abaixo, em Detalhes, observe o endereço IP público IPv4 da instância EC2. Um exemplo é mostrado na imagem abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/02/task_2_step_15_23_41.jpg)

#### Tarefa 3: conectando instância EC2 com conexão de área de trabalho remota

1. Selecione sua instância **EC2** , clique em **Conectar** e clique em **Cliente RDP** na próxima tela.**![img](https://play.whizlabs.com/frontend/web/media/2021/09/08/capture.png)**

2. Clique em **Baixar arquivo da área de trabalho remota.** [ **I** **pf Passo** ]

3. Uma caixa de diálogo aparecerá conforme mostrado:

   

4. Clique em **Obter senha** para obter a senha, o que o ajudará a fazer o login ao iniciar a instância.

5. O par de chaves associado à sua instância será mostrado.

   

6. Para obter a senha, você deve descriptografar o par de chaves. Escolha a opção de **arquivo Key Pair baixado** em Key Pair Path e clique em **Decrypt Password** .

![img](https://play.whizlabs.com/frontend/web/media/2020/10/28/win1.png)

1. **O nome de usuário** e a **senha** serão exibidos na caixa de diálogo. Certifique- se de registrá-los em algum lugar para uso posterior .

![img](https://play.whizlabs.com/frontend/web/media/2021/04/21/screen_shot_2021-04-21_at_8.39.30_pm.png)

1. Certifique-se de que já possui um aplicativo Remote Desktop em seu computador.
2. Vá para o seu arquivo de download e clique para abri-lo.
   ![img](https://play.whizlabs.com/frontend/web/media/2020/10/28/4_05_22.png)
3. Cole a senha copiada aqui e clique em **OK** para iniciar a instância.

![img](https://play.whizlabs.com/frontend/web/media/2020/10/28/2_04_23.png)

1. Devido à natureza dos certificados autoassinados, você pode receber um aviso de que o certificado de segurança não pôde ser autenticado, se for o caso, escolha **Sim** ou **Continuar** para continuar se você confiar no certificado.
   ![img](https://play.whizlabs.com/frontend/web/media/2021/09/02/capture1.png)
2. Você será conectado ao Windows Server. No canto superior direito, você pode encontrar o IP público, IP privado, RAM, etc.
3. Para desconectar, clique em **Fechar** no topo. 

#### Tarefa 4: Instalando o servidor IIS usando a linha de comando

Nesta etapa, vamos instalar um servidor IIS para que possamos usá-lo para lançar uma página web.

1. Clique no botão Iniciar do Windows no canto esquerdo inferior e digite **cmd** .

2. Clique com o botão direito do mouse no prompt de comando e selecione **executar como administrador** .

   ![img](https://play.whizlabs.com/frontend/web/media/2021/09/24/cmd.png)

3. Clique em **SIM** na notificação pop-up.

4. Digite o comando ***DISM / online / enable-feature / featureName: IIS-DefaultDocument / All\*** e pressione Enter.

5. Assim que o progresso for 100%, você verá a mensagem “A operação foi concluída com sucesso”.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/09/24/100percent.png)

6. Feche o prompt de comando e clique no botão Iniciar novamente e digite **IIS** , agora você verá o **Internet Information Services Manager** instalado com sucesso.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/09/24/iis_search.png)

#### Tarefa 5: Testando a página da web padrão

Nesta etapa, tentaremos abrir a página da web padrão fornecida.

1. Clique em **Internet Information Services Manager** .

2. Sob as conexões, clique duas vezes no primeiro nome que você vê na **Página inicial** para expandi-lo, agora clique duas vezes em **Sites** novamente para ver **o Site padrão** .

   ![img](https://play.whizlabs.com/frontend/web/media/2021/09/25/connections.png)

3. Clique em **Default Web Site** e no lado direito do painel, em **Browse Website,** clique em **Browse \*: 80 (http)** .

4. Agora você será redirecionado para uma página da web padrão e se parece com a imagem mostrada abaixo e também observe o endereço da web da página da web padrão (localhost).

   

#### Tarefa 6: Criando uma página da web personalizada

Agora, nesta etapa, estaremos criando nossa própria página da web.

1. Digite *notepad* na barra de pesquisa perto do botão Iniciar e clique com o botão direito nele e selecione **executar como administrador** .

2. Clique em **SIM** na notificação pop-up.

3. Agora copie e cole o código html abaixo no bloco de notas para criar uma página da web personalizada:

    cópia de

   **<html>****<body>****<h1> Olá, usuário Whizlabs! </h1>****<h2> Você criou com sucesso uma página da web personalizada. </h2>****</body>****</html>**

4. Agora clique em Arquivo e selecione **Salvar como** , dê o nome do arquivo como ***index.html*** e selecione **Salvar como tipo** como **todos os arquivos** .

5. Agora, para o destino, clique duas vezes na **unidade C** (disco local no seu caso) no lado esquerdo, clique duas vezes em **inetpub** .

   

6. Na próxima tela, clique duas vezes em **wwwroot** e você verá dois arquivos com os nomes **iisstart** . Não faça nada e apenas clique em **Salvar** .

7. A razão pela qual escolhemos este destino é quando acessamos o mesmo URL novamente, desta vez seremos redirecionados para nossa página da web personalizada. 

8. Agora volte para a página da web padrão que você abriu na etapa anterior e clique em atualizar.

9. Agora você poderá ver nossa página html customizada, que se parece com a imagem mostrada abaixo.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/09/24/custom_html_page.png)
