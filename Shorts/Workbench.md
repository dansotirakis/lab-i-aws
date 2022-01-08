# Crie uma tabela DynamoDB e execute várias operações de tabela usando NoSQL Workbench

## O que é AWS DynamoDB?

### Definição

- O DynamoDB é um banco de dados NoSQL rápido e flexível projetado para aplicativos que precisam de latência consistente de um único dígito em qualquer escala. Ele é um banco de dados totalmente gerenciado e suporta modelos de dados de documentos e valores-chave.
- Possui um modelo de dados muito flexível. Isso significa que você não precisa definir o esquema do banco de dados antecipadamente. Ele também tem um desempenho confiável.
- O DynamoDB é uma boa opção para jogos móveis, ad-tech, IoT e muitos outros aplicativos.

### Tabelas DynamoDB

As tabelas do DynamoDB consistem em:

- Itens (pense em uma linha de dados em uma tabela).
- Atributos ((pense em uma coluna de dados em uma tabela).
- Suporta valor-chave e estruturas de dados de documentos.
- Chave = o nome dos dados. Valor = os próprios dados.
- O documento pode ser escrito em JSON, HTML ou XML.

### DynamoDB - chaves primárias

- O DynamoDB armazena e recupera dados com base em uma chave primária

- O DynamoDB também usa chaves de partição para determinar se os dados de localização física são armazenados.
- Se você estiver usando uma chave de partição como chave primária, nenhum item terá a mesma chave de partição.
- As chaves compostas (chave de partição + chave de classificação) podem ser usadas em combinação.
- Dois itens podem ter a mesma chave de partição, mas devem ter uma chave de classificação diferente.
- Todos os itens com a mesma chave de partição são armazenados juntos e classificados de acordo com o valor da chave de classificação.
- O DynamoDB permite que você armazene vários itens com as mesmas chaves de partição.

## NoSQL Workbench

-  O NoSQL é basicamente um banco de dados não relacional, com muitas outras vantagens também.
- NoSQL Workbench é um ambiente de desenvolvimento e teste virtual para desenvolvedores em todo o mundo.
- Ele permite que os usuários testem seus modelos de dados em um grande número de aspectos de funcionalidade e também permite que desenvolvam seu software, desde o início, com facilidade.
- Em termos simples, o NoSQL Workbench é uma plataforma IDE que inclui modelagem de dados, visualização de dados e construção de operação.
- **Modelagem de dados: o** Workbench permite que os usuários construam novos modelos de dados do zero ou usando modelos de dados existentes.
- **Visualização de dados:** como o nome sugere, fornece a representação gráfica de informações e dados.
- **Operation Building:** Workbench é uma plataforma forte e confiável para a construção de aplicativos e também possui uma ótima interface gráfica de usuário que eventualmente torna a comunicação entre o banco de dados e o usuário mais fácil. 

## Diagrama de Arquitetura

  ![img](https://play.whizlabs.com/frontend/web/media/2021/10/21/dynamodb_nosql_architecture_diagram.png)

## Detalhes da Tarefa

1.  Faça login no AWS Management Console.
2. Crie uma tabela do DynamoDB por meio do AWS Console.
3. Conecte-se ao DynamoDB usando NoSQL Workbench.
4. Criando itens usando o console.
5. Adicionando novos itens à tabela usando NoSQL Workbench.
6. Excluindo um item usando NoSQL Workbench.
7. Atualizando um item usando NoSQL Workbench. 
8. Criação de uma nova tabela usando NoSQL Workbench.
9. Adicionando itens à nova tabela.
10. Enviando a tabela e seus dados para o Amazon DynamoDB.
11. Excluindo recursos da AWS.

## Pré-requisitos

1. Para trabalhar com este laboratório, é necessário baixar o NoSQL Workbench. Para fazer o download, acesse a página [Download NoSQL Workbench](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/workbench.settingup.html) . Com base no seu sistema operacional, selecione a respectiva opção no **link Download** . Depois de baixado, abra o arquivo e instale.

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/12/nosql_launch.png)

## Etapas de laboratório

### Tarefa 1: crie uma tabela DynamoDB por meio do AWS Console

Nesta tarefa, você criará uma tabela DynamoDB que é usada para adicionar itens e visualizar os dados no NoSQL Workbench.

1. Certifique-se de estar na região da **Virgínia** .
2. Navegue até **DynamoDB** clicando no ![img](https://lh3.googleusercontent.com/wG64RPJd2z-YgkhP69sc7wNL_dliQPdVXiA-Scv3ZKGZ9Nu2pEW1qr9xELtDo_41QAQzYQj5THTY8zIttaPBerh7BXXx4t0Neope-DkJB4uTvo5ucZX_ucMMz9cXjsGhV72-77sh) menu na parte superior e selecionando **DynamoDB** na seção **Banco de dados** .
3. Clique no ![img](https://play.whizlabs.org/frontend/web/media/2021/10/12/create_table.png) botão à direita.
4. Detalhes da mesa:
   - Nome da tabela: digite ***Student_Info***
   - Chave de partição: digite ***StudentId***
   - Chave de classificação: digite o nome do ***aluno***
5. Deixe tudo como padrão e clique no ![img](https://play.whizlabs.org/frontend/web/media/2021/10/12/create_table.png) botão.

## Tarefa 2: conecte-se ao DynamoDB usando NoSQL Workbench

Nesta tarefa, você configurará arquivos e passará as credenciais de acesso para se conectar ao DynamoDB usando o NoSQL Workbench e visualizar a tabela do DynamoDB após a conexão bem-sucedida. E as credenciais que você usará para fazer uma conexão são a **ID da chave de acesso** e a **Chave de acesso secreta** presentes no lado esquerdo da interface do laboratório sob o **nome de usuário** e a **senha do** **IAM** .

1. Abra o NoSQL Workbench que você baixou e instalou durante a etapa de pré-requisitos.

2. Clique no  botão **Iniciar** ao lado de Amazon DynamoDB.

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/12/nosql_launch_29_50.png)

3. No painel do lado esquerdo, clique em **Construtor de operação** e clique em **Adicionar conexão** no lado direito.

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/12/operation_builder_initial_add_connection.png)

4. Agora precisamos configurar dois arquivos em nosso PC local para conectar com sucesso ao nosso DynamoDB usando NoSQL Workbench.

5. Para usuários do **Windows** :

   - Vá para o destino ***% USERPROFILE% \. Aws*** em seu PC local.

6. Você poderá encontrar  arquivos de **configuração** e **credenciais** , que precisamos editar usando o bloco de notas.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/14/destination_path.png)

7. Abra o arquivo de **configuração** usando o bloco de notas e substitua o conteúdo existente pelo fornecido abaixo.

    cópia de

   **[padrão] region = us-east-1 output = json AWS_SDK_LOAD_CONFIG = 1**

8. Salve o arquivo usando **Ctrl + S** .

9. Agora abra o arquivo de **credenciais** usando o notepad e substitua o padrão **aws_access_key_id** e **aws_secret_access_key** pelo **ID da chave de acesso** e **chave de acesso secreta** presentes no lado esquerdo da interface do laboratório sob o **nome de usuário** e **senha do** **IAM** .

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/20/access_key_and_secret_key.png)

10. O arquivo depois de substituir suas credenciais se parece com isto. ( **Eu mascarei minha chave de acesso secreta como um protocolo de segurança** )

    

11. Salve o arquivo usando **Ctrl + S** .

12. Para usuários de **Mac** e **Linux** :

    - Abra seu Mac Terminal ou Linux Command Line.

    - Você pode usar o editor Vi ou nano para editar os arquivos de configuração e credenciais mencionados nas etapas acima.

    - Enter ***vi ~/.aws/config*** (or) ***nano ~/.aws/config***

      ***![img](https://play.whizlabs.com/frontend/web/media/2021/10/21/ubuntu_command.png)***

    - Now paste the content which is tabulated in the Step-7 inside this **~/.aws/config** file.

      ![img](https://play.whizlabs.com/frontend/web/media/2021/10/21/ubuntu_command_paste.png)

    - Save the file by pressing **Esc** button, and type ***:wq*** [If you are using Vi editor]

    - Press **Ctrl+X** and Press **Enter** to save the file [If you are using nano editor]

    - Now enter ***vi ~/.aws/credentials*** (or) ***nano ~/.aws/credentials***

      ***![img](https://play.whizlabs.com/frontend/web/media/2021/10/21/ubuntu_credentials_command.png)***

    - Now copy the below content and replace the default **aws_access_key_id** and **aws_secret_access_key** with the **Access Key ID** and **Secret Access Key** present on the left side of the lab interface under **IAM username** and **Password**. [Refer Step 9&10 to understand]

    -  Copy

      **[default] aws_access_key_id =** <Access Key ID> **aws_secret_access_key =** <Secret Access Key>

      

    - Save the file by pressing **Esc** button, and type ***:wq*** [If you are using Vi editor]

    - Press **Ctrl+X** and Press **Enter** to save the file [If you are using nano editor]

13. Now get back to the NoSQL Workbench and fill the following details:

    - Connection name : Enter ***Connection 3*** ( You can give any name of your choice)
    - Default AWS Region : Select **us-east-1**
    - Access Key ID : Paste your **Access Key ID** of the lab. (The same way you did in the Step 9)
    - Secret access key : Paste your **Secret Access Key** of the lab. (The same way you did in the Step 9)
    - Persist connection : **Check** the box

14. Click on the **Connect** button.

    

15. In the next screen, click on **Open** under your respective connection.

    

16. Now you will be able to see the table(**Student_Info)** we have created using AWS Console here in NoSQL Workbench.

### Task 3: Creating items using the console 

In this task, you will create a few items in the DynamoDB table through the console and try to see these items in the NoSQL Workbench.

1. Make sure you are in the **N.Virginia** Region.

2. Navigate to **DynamoDB** by clicking on the ![img](https://lh3.googleusercontent.com/wG64RPJd2z-YgkhP69sc7wNL_dliQPdVXiA-Scv3ZKGZ9Nu2pEW1qr9xELtDo_41QAQzYQj5THTY8zIttaPBerh7BXXx4t0Neope-DkJB4uTvo5ucZX_ucMMz9cXjsGhV72-77sh) menu at the top and selecting **DynamoDB** under the **Database** section.

3. On the left side panel, click on **Items** and select your table i.e **Student_Info**

4. Click on the **Create item** button on the right side.

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/create_item_button_in_console.png)

5. Attributes:

   - StudentId : Enter ***1***
   - StudentName : Enter ***Jay***
   - Click on **Add new attribute** and select **String**
   - Give Attribute name as ***FavoriteSport*** and Value as ***Cricket***
   - Click on ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/create_item.png) button.![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/create_jay_item.png)

6. Similarly create the following items shown below with their respective Attribute names and Values by following the above steps.

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/all_items_in_console.png)

7. Now you will be able to see three items returned in the **Student_Info** table in the console.

8. Now open the NoSQL Workbench window from your taskbar to see if these newly created items in the console are present in the NoSQL Workbench.

9. Go to **Operation builder > Tables > Student_Info** and click on the **Scan** button on the right side.

10. Now you will be able to see three items in the **Student_info** table in the Workbench.

    ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/nosql_item_visualization.png)

### Task 4: Adding new items to the table using NoSQL Workbench

In this task, you will add two new items to the existing table from NoSQL Workbench and see the reflections in the DynamoDB console.

1. Now on the top right corner click on **Expand operation** and click on **Choose** under **Interface-based operations**.

2. Build Operations:

   - Data plane operations : Select **PutItem** from the drop down menu
   - Table : Select **Student_Info**
   - Partition key : Enter ***4\***
   - Sort key : Enter ***Harsh***
   - Click on **+** sign next to **Other attributes**
   - Attribute name : Enter ***FavoriteSport***
   - Attribute type : Select **String** from the drop down menu
   - Attribute value : Enter ***Volleyball***

3. Now click on the **Save operation** button.

4. Scroll down a little and give the **Name** under Save operation as ***test1*** and click on the **Save** button.

5. You can give a name of your choice for Save operation as well, it does not matter.

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/put_item_from_nosql.png)

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/save_operation_21_32.png)

6. Now click on the **Run** button which is next to Clear form.

7. Expand the table by clicking on it to see the result. 

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/expand_table_to_view_new_items.png)

    

8. Click on the **Scan** button on the right side if you do not see any item.

9. Similarly add one more item from the NoSQL Workbench using **PutItem** operation:

   - StudentId as ***5\***
   - StudentName as ***Virat\***
   - FavoriteSport as ***Rugby***

10. The table looks something like this in the Workbench. Click on the **Scan** button on the right side if you do not see any items. 

    ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/5_items_in_nosql.png)

11. Now head back to the **DynamoDB console** and refresh the page to see these newly added items there.

    ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/dynamodb_console_after_adding_items.png)

### Task 5: Deleting an item using NoSQL Workbench

In this task, you will delete an item from the Workbench and see the reflections in the DynamoDB console.

1. Now get back to the NoSQL Workbench.

2. Scroll to the top and click on **Expand operation**.

3. Build Operations:

   - Data plane operations : Select **DeleteItem** from the drop down menu
   - Table : Select **Student_Info**
   - Partition key : Enter ***1\***
   - Sort key : Enter ***Jay\***

4. Now click on the **Save operation** button.

5. Scroll down a little and give the **name** under Save operation as ***test2*** and click on **Save** button.

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/delete_item_in_nosql_04_49.png)

6. Now click on the **Run** button which is next to Clear form.

7. Click on the table on the left side to expand it and see the result. Click on the **Scan** button on the right side if you do not see the result. 

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/resultant_table_in_nosql_after_del.png)

8. Now head back to the **DynamoDB console** and refresh the page to see if the item has been deleted here as well or not.

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/dynamodb_console_after_del_item.png)

### Task 7: Updating an item using NoSQL Workbench

In this task, you will update an existing item through NoSQL Workbench and see if it is reflected in the DynamoDB console as well.

1. Now get back to the NoSQL Workbench.

2. Scroll to the top and click on **Expand operation**.

3. Build Operations:

   - Data plane operations : Select **UpdateItem** from the drop down menu
   - Table : Select **Student_Info**
   - Partition key : Enter ***2\***
   - Sort key : Enter ***Robin\***
   - Update expression : Select **Set** from the drop down menu.
   - Click on **+** sign next to it.
   - Set:
     - Attribute name : Enter ***FavoriteSport***
     - Operators : Select **=** sign from the drop down menu.
     - Attribute type : Select **String** from the drop down menu.
     - Value : Enter ***Football*** in the <empty> box.

4. Now click on the **Save operation** button.

5. Scroll down a little and give the **name** under Save operation as ***test3*** and click on **Save** button.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/updating_robin_item_in_nosql.png)

6. Now click on the **Run** button which is next to Clear form.

7. Click on the table on the left side to expand it and see the result. Click on the **Scan** button on the right side if you do not see the update. 

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/table_in_nosql_afte_robin_update.png)

8. Now head back to the **DynamoDB console** and refresh the page to see if the item has been updated here as well or not.![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/table_in_console_after_robin_update.png)

### Task 6: Creating a new table using NoSQL Workbench

In this task, you will create a new table with **Movies** as its name using NoSQL Workbench to add a few items and see if it has been updated in the dynamoDB console as well.

1. Now get back to the NoSQL Workbench.

2. In the NoSQL workbench, click on the **Data modeler** below the Amazon DynamoDB section.

3. Click on **+** sign below Data model to create a new data model.

4. Create data model for Amazon DynamoDB:

   - Name : Enter ***Movies Name***
   - Author : Enter **<Your Name>**

5. Click on the **Create** button.

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/create_data_model.png)

6. Click on **+** sign next to **Tables** which is below Data model to create a new table (or) click on **+** **Create new table** option present on the right side.

7. Add DynamoDB table:

   - Table name : Enter ***Movies***
   - Partition key : Enter ***Id*** and select **Number** from the drop down menu.
   - Add sort key : **Check**
   - Sort key : Enter ***Name*** and select **String** from the drop down menu.
   - Other attributes : Click on **+ Add other attribute**
     - Attribute name : Enter ***FavoriteMovie*** and select **String** from the drop down menu.

   

8. Leave the other settings as default and click on **Add table definition** button.

   ![img](https://play.whizlabs.org/frontend/web/media/2021/10/13/add_table_definition.png)

9. The next screen you see will be something like this. 

   

### Task 7: Adding items into the new table

In this task, you will add a few new items into the newly created Movies table through NoSQL Workbench.

1. Click on the **Visualizer** option on the left side panel .

2. Click on the **Update** button next to the **Movies** table and click on **Add data** on the top right corner.

   

3. Adding data:

   - Under **Id** : Enter ***1***
   - Under **Name** : Enter ***Sherley***
   - Under **FavoriteMovie** : Enter ***Harry Potter***![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/1st_item_in_new_table_from_nosql.png)

4. Click on **+ Add new row** to add two other items as shown below. And once done, click on **Save** button on the top right corner.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/save_button_in_nosql_after_adding_3_items.png)

5. Now click on **Aggregate view** to see data stored in the table in aggregated form.

   

### Task 8: Commiting the table and its data to Amazon DynamoDB

In this task, you will commit the table and its items to the DynamoDB database in the console from NoSQL Workbench and see if it has been added to the DynamoDB console.

1. Click on **Commit to Amazon DynamoDB** button under Aggregate view.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/commit_changes_to_dynamodb_from_nosql.png)

2. In the next screen, select your **connection name** from the **Saved connections** drop down menu. [ In my case - Connection 3 ]

3. Now click on the **Commit** button. It will take a few seconds to process.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/commit_connection_selection.png)

4. Now in the next screen, under **Active connections**, click on **Open** under your connection name. [ In my case - Connection 3 ]

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/open_connection_button.png)

5. Now you will be able to find the **Movies** table under **Tables** section just above your **Student_Info** table.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/movies_tables_in_nosql_section.png)

6. Now click on the **Movies** table to expand it and see the items you have created earlier inside this table.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/viewing_items_of_new_table_in_nosql.png)

7. Now head back to the **DynamoDB console**, refresh the page and click on **Tables** on the left side panel.

8. You will see the **Movies** table present here in the DynamoDB console.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/viewing_movie_table_in_the_console.png)

9. Click on the **Items** section beneath the **Tables** on the left side panel and select **Movies** table.

10. You will be able to find the three items you have created through NoSQL Workbench, here in the console.

    ![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/viewing_items_of_new_table_in_console.png)

11. You can play around by updating and deleting items in the new table i.e **Movies**.

### Task 9: Delete AWS Resources

Deleting DyanamoDB Tables

1. Navegue até **DynamoDB** clicando no ![img](https://lh3.googleusercontent.com/wG64RPJd2z-YgkhP69sc7wNL_dliQPdVXiA-Scv3ZKGZ9Nu2pEW1qr9xELtDo_41QAQzYQj5THTY8zIttaPBerh7BXXx4t0Neope-DkJB4uTvo5ucZX_ucMMz9cXjsGhV72-77sh) menu na parte superior e selecionando **DynamoDB** na seção **Banco de dados** .

2. Clique em **Tabelas** no painel esquerdo.

3. Selecione as tabelas que você criou e clique no botão **Excluir** do lado direito.

   ![img](https://play.whizlabs.com/frontend/web/media/2021/10/13/delete_tables_in_console.png)

4. Na próxima tela, 

   - Exclua todos os alarmes do CloudWatch para as tabelas mostradas: **Verifique**
   - Crie backups de todas as tabelas mostradas antes de excluí-las: **Desmarque**
   - Digite ***deletar\*** na caixa de confirmação.

5. Clique no botão **Excluir tabelas** para excluir as tabelas.

   

### Conclusão e Conclusão

1. Você criou com êxito uma tabela do DynamoDB por meio do console do DynamoDB.
2. Você se conectou com êxito ao DynamoDB usando o NoSQL Workbench .
3. Você executou com êxito os métodos CRUD por meio do NoSQL Workbench e viu os reflexos no console do DynamoDB.
4. Você criou com sucesso uma tabela por meio do NoSQL Workbench e se comprometeu com o Amazon DynamoDB.