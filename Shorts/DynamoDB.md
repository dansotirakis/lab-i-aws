# Criação do DynamoDB e adição de itens à tabela

## Diagrama de Arquitetura

![img](https://play.whizlabs.com/frontend/web/media/2020/07/14/task_id_147_creating_dynamodb_and_adding_items_to_the_table.png)

## Detalhes da Tarefa

1. Crie uma tabela do DynamoDB.
2. Adicione itens à tabela do DynamoDB.

## Etapas de laboratório

### Tarefa 1: Criando Tabela DynamoDB

1. Certifique-se de que você está na região **us-east-1 do leste** dos **EUA (Virgínia do** Norte).
2. Navegue até a ![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/l2.png)página clicando no ![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/l3.png)menu na parte superior. **DynamoDB** está disponível na ![img](https://play.whizlabs.com/frontend/web/media/2021/10/08/l1.png)seção.
3. Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/l4.png)no painel
   - Nome da tabela: digite ***whizlabs\***
   - Chave de partição: insira o número do ***rolo*** e selecione![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/l5.png)
   - Mantenha as outras opções como **padrão** .
   - Role para baixo e clique em **![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/l4_41_32.png)**.
4. Sua mesa será criada em **2-3 minutos** .
5. Você verá o status da tabela mudar para **Ativo** .

![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/table.png)

### Tarefa 2: adicione itens à tabela DynamoDB

1. A seguir, vamos inserir alguns dados na tabela que criamos.
2. Clique na sua mesa para ver os detalhes da sua mesa.
3. Para adicionar novos itens à mesa, clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/l6.png)no canto superior direito.
4. Agora role para baixo e clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/l7.png).

1. Criar item:

- Roll No: Digite ***1\***
- Clique em **Adicionar novo atributo** e selecione **String** no menu suspenso.
  - Nome do atributo **:** Digite o ***nome\***
  - Valor: Enter ***Deep\***
  - **Nota: O nome do atributo da tabela faz distinção entre maiúsculas e minúsculas, ou seja, "Nome" e "nome" serão tratados como dois atributos diferentes.**

![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/t1.png)

- Clique em ![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/l8.png)no canto inferior direito.

1. Da mesma forma, crie mais 2 itens na tabela com os nomes **Nikhil** e **Pavan** .

![img](https://play.whizlabs.com/frontend/web/media/2021/10/06/t2.png)