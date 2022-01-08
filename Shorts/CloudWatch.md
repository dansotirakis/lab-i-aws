# Creating a CloudWatch Dashboard for EC2 Instance

# Diagrama de Arquitetura

![img](https://play.whizlabs.com/frontend/web/media/2020/07/14/task_id_146_creating_a_cloudwatch_dashboard_for_ec2_instance.png)

# Detalhes da Tarefa

1. Faça login no AWS Management Console.
2. Inicie uma instância EC2.
3. Crie um painel do CloudWatch.
4. Crie widgets diferentes para a mesma métrica para ver a diferença.
5. Validação do laboratório

# Etapas de laboratório

## Tarefa 1: inicie uma instância EC2

1. Certifique-se de estar na região da **Virgínia** .

2. Navegue até EC2 clicando no ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image7_37_32.png) menu na parte superior e, a seguir, clique em **EC2** na  seção **Computar** .

3. Navegue até **Instâncias** no menu do lado esquerdo e clique no botão **Iniciar Instâncias** .

4. **Escolha uma Amazon Machine Image (AMI):** Pesquise **Amazon Linux 2 AMI** na caixa de pesquisa e clique no  botão de **seleção** .

   **![img](https://play.whizlabs.com/frontend/web/media/2020/07/30/linux_2_ami_33_06.png)**

5. **Escolha um tipo de instância:** selecione ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image9_38_59.png) e clique em **Próximo: Configurar detalhes da instância**

6. **Configurar detalhes da instância: não** há necessidade de alterar nada nesta etapa, clique em **Próximo: Adicionar armazenamento**

7. **Adicionar armazenamento: não** há necessidade de alterar nada nesta etapa, clique em **Próximo: Adicionar tags** 

8. **Adicionar Tags:** Clique em **Adicionar Tag**

   - Chave: Digite o ***nome\***
   - Valor: Insira ***whizlabs\***
   - Clique em **Avançar: Configurar Grupo de Segurança**

9. Configure o Grupo de Segurança:

   - Para adicionar **SSH:**
     - Escolha o tipo: ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image21_41_07.png)
     - Fonte: Custom (Permitir endereço IP específico) ou Anywhere (De TODOS os endereços IP acessíveis).
   - Depois disso, clique em **Revisar e lançar**

10. **Revisar e iniciar:** Revise todas as configurações e clique em **Iniciar** .

11. **Par de Chaves:** Selecione **Criar um novo par de chaves**

    - Tipo de par de chaves: Selecione **RSA**
    - Nome do par de chaves: digite ***whiz_key***
    - Clique em ![img](https://play.whizlabs.com/frontend/web/media/2020/02/19/image14_42_05.png). 
    - Depois disso, clique em **Launch Instance.**

12. **Status de inicialização:** sua instância agora está sendo iniciada. Clique no ID da instância e aguarde a inicialização completa da instância (até que o status mude para Executando).
    ![img](https://play.whizlabs.com/frontend/web/media/2021/07/13/2021-07-13_23_31_14-window.png)

13. Observe o **endereço IPv4 público** e a **ID** da instância da instância EC2. Um exemplo é mostrado na imagem abaixo.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/28/cld1.png)

## Tarefa 2: Criando um painel CloudWatch

1. **Aguarde 5 a 10 minutos para que o CloudWatch reúna as matrizes da instância do EC2.**
2. Navegue até o **CloudWatch** clicando no ![img](https://lh3.googleusercontent.com/qc6Lj4EBmczfWiB5n9-XJBWDq6eBfR-rrSeBm6rl5mbrFUr3tzuQc-Ik08Co10vaDLIzhGfkSnyc9oQCIczBY_wsUaOBFORRg8iZbSZz8YHX4n8fOrYxz6AfoTVw9md5PBWa2f7v)menu na parte superior da página e, a seguir, clique em CloudWatch na seção Gerenciamento e governança.
3. Clique em **Dashboards** no painel esquerdo.
4. Clique em **Experimente a nova interface** para usar a nova interface da AWS do CloudWatch .
   ![img](https://play.whizlabs.com/frontend/web/media/2021/07/15/2021-07-15_10_03_16-window.png)
5. Clique em .![img](https://lh4.googleusercontent.com/ebU_VfhDEZU0r3jvg1lCAFq_jNN3M2oNHy6QfP-TxNp59pgFoI3t1MTvfBYgjAUPrEoR3vGi1EqXq9T0sH2ScH8udbbYsX08ZSI2sR-OEHtyMc6WVioyogKjDsv_QPKFviNCRfmM)
6. Dê um nome ao seu painel.

- Nome do painel: Digite **MyEC2**
- Clique em **Criar painel.**

![img](https://play.whizlabs.com/frontend/web/media/2021/07/15/2021-07-15_10_07_06-window.png)

1. Temos que selecionar um tipo de widget para configurar e adicionar a este painel. Selecione **Linha** .

![img](https://play.whizlabs.com/frontend/web/media/2021/07/15/2021-07-15_10_09_29-window.png)

1. Selecione **Metrics** como fonte de dados.
   **![img](https://play.whizlabs.com/frontend/web/media/2021/07/15/2021-07-15_10_10_55-window.png)**
2. Você verá um gráfico de métricas. Em **Todas as métricas** , pesquise e escolha **EC2 (** já que vamos observar as métricas de EC2 que criamos anteriormente).
3. Em EC2, escolha **Métricas por instância** .
   ![img](https://play.whizlabs.com/frontend/web/media/2021/07/15/2021-07-15_10_15_13-window.png)
4. **Cole o ID da Instância copiado** na barra de pesquisa e selecione **CPUUtilization** nas métricas e clique em ![img](https://lh5.googleusercontent.com/p4T-xzvACKN3FruNYyovqXVz2epZpFxRNHWXlqQXHZUUIsz54YkzkzxnMiIFvho8xpvt0sF0xKm6lD-CTqJ-D55NM7AbND1ebW2RtEuJKPG5iSXflITLMO4LpZvAKzWTaarZtS2h).
   ![img](https://play.whizlabs.com/frontend/web/media/2021/07/28/cld2.png)
5. **Observação: se você não vir as métricas CPUUtilization, aguarde 5 minutos.**
6. Você criou com êxito um **widget de linha** para utilização da CPU.

![img](https://play.whizlabs.com/frontend/web/media/2021/07/15/2021-07-15_10_19_55-window.png)

## Tarefa 3: criando widgets diferentes para a mesma métrica

Área Empilhada

1. No painel, clique em **Adicionar widget** e selecione **Área empilhada.** Clique em **Configurar** .

2. Você verá um gráfico de métricas. Em **Todas as métricas** , pesquise e escolha **EC2** (já que vamos observar as métricas de EC2 que criamos anteriormente).

3. Em EC2, escolha **Métricas por instância** .

4. Pesquise e selecione **CPUUtilization** nas métricas e clique em ![img](https://lh5.googleusercontent.com/p4T-xzvACKN3FruNYyovqXVz2epZpFxRNHWXlqQXHZUUIsz54YkzkzxnMiIFvho8xpvt0sF0xKm6lD-CTqJ-D55NM7AbND1ebW2RtEuJKPG5iSXflITLMO4LpZvAKzWTaarZtS2h).

5. Você criou com êxito um **widget de Área Empilhada** para Utilização da CPU.

    

![img](https://play.whizlabs.com/frontend/web/media/2021/07/15/2021-07-15_10_24_28-window.png)

Número

1. No painel, clique em **Adicionar widget** e selecione **Número.** Clique em **Configurar** .

2. Você pode ver um gráfico métrico. Em **Todas as métricas** , pesquise e escolha **EC2 (** já que vamos observar as métricas de EC2 que criamos anteriormente).

3. Em EC2, escolha **Métricas por instância** .

4. Pesquise e selecione **CPUUtilization** nas métricas e clique em ![img](https://lh5.googleusercontent.com/p4T-xzvACKN3FruNYyovqXVz2epZpFxRNHWXlqQXHZUUIsz54YkzkzxnMiIFvho8xpvt0sF0xKm6lD-CTqJ-D55NM7AbND1ebW2RtEuJKPG5iSXflITLMO4LpZvAKzWTaarZtS2h).

5. Você criou com êxito um **widget de número** para utilização da CPU.
   ![img](https://play.whizlabs.com/frontend/web/media/2021/07/15/2021-07-15_10_26_15-window.png)

6. Clique em ![img](https://lh3.googleusercontent.com/vRudAxF7PMyHwphmu9kVVlgWn65y321xWxMoAgRVItg9DFKcLOS0RAdFIj0P8Ecr9ttKX98tF5CDwdivnCJvXEuOTbPOi_STYPxDED-Eobv247XDkkctDadXBnjKc6xnz-bBOyW1)para salvar os widgets.

7. Atualize a página até que o valor da métrica seja mostrado.

8. Usando essas etapas, você pode usar os widgets para criar seu próprio painel de métricas.

9. **Observação:** a métrica real gerada depende da utilização da CPU.

    

   