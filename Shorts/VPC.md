# Criando uma nuvem privada virtual com o assistente VPC

## Diagrama de Arquitetura

![img](https://play.whizlabs.com/frontend/web/media/2020/07/14/task_id_149_creating_a_virtual_private_cloud_with_vpc_wizard.png)

### Detalhes da Tarefa

1. Faça login no AWS Management Console.
2. Crie um VPC usando o VPC Wizard.
3. Percorra os recursos criados pelo VPC.
4. Validação do laboratório.

## Etapas de laboratório

### Tarefa 1: crie um VPC usando o assistente de VPC

1. Certifique-se de estar na região da **Virgínia** .
2. Navegue até o ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image8_23_36.png) menu e clique em **VPC** em **Networking & Content Delivery.**
3. Clique em **Launch VPC wizard**
4. Escolha **VPC com uma única sub-rede pública** para nosso laboratório e clique em **Selecionar** .
5. O bloco CIDR IPv4 e o CIDR IPv4 da sub-rede pública serão atribuídos automaticamente a você. Insira o nome VPC como ***myfirstvpc*** .
6. Deixe os outros campos como padrão e clique em **Criar VPC** .

![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image2_25_22.png)

1. Seu VPC foi criado com sucesso. Clique **Ok** para fechar a mensagem.

![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image6_25_51.png)

### Tarefa 2: analise os recursos criados pelo VPC

1. No painel, clique em **Seu VPC** para ver o VPC que você criou.

![img](https://play.whizlabs.com/frontend/web/media/2021/06/21/2.png)

1. Navegue até **Sub** - **redes,** onde você pode ver a sub-rede pública que foi criada.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/08/task_3_step_2.jpg)

1. Navegue até as **tabelas de rota** . Você pode ver duas tabelas de rota (uma para a sub-rede pública e outra para a sub-rede privada).
2. **Observação** : a **tabela de rota principal** sempre será alocada com a sub-rede privada. Como estamos criando uma sub-rede pública, uma nova tabela de rota personalizada será alocada.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/08/task_3_step_4.jpg)

1. O gateway da Internet é criado e anexado à sub-rede pública. O gateway de Internet conecta seu VPC à Internet.

![img](https://play.whizlabs.com/frontend/web/media/2020/10/28/igw-list.png)