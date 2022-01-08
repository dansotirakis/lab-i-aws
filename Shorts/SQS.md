# SQS (Simple Queue Service)

**Curiosidade: esta foi a primeira oferta de serviço da AWS disponibilizada publicamente.**

1. Amazon SQS é um **serviço de enfileiramento confiável**, fácil de gerenciar e escalonável. SQS é um aplicativo de nuvem simples e econômico.
2. O AWS SQS **pode ser usado para transmitir qualquer quantidade de dados, em qualquer nível de taxa de transferência, sem perder mensagens.** Ele não interrompe outros serviços quando executado continuamente.
3. O SQS ajuda a reduzir as tarefas administrativas ao dimensionar os clusters de mensagens de alta disponibilidade. Enquanto pagamos apenas pelo que usamos. O AWS SQS nos ajuda a salvar dados importantes que podem ser perdidos se um aplicativo inteiro cair ou se algum componente ficar indisponível. 
4. A fila SQS atua como um buffer entre os componentes do aplicativo que recebem os dados e as outras partes que processam os dados no sistema.
5. SQS é usado para arquitetura orientada a mensagens. Se o servidor de processamento não puder processar o trabalho rápido o suficiente (por qualquer motivo), o trabalho será enfileirado para que os servidores de processamento possam trabalhar nele quando tiverem recursos disponíveis para processar a solicitação. Isso significa que o trabalho não é perdido devido a recursos insuficientes.
6. O Amazon SQS padrão garante que cada mensagem seja entregue pelo menos uma vez.
7. Existem dois tipos de filas:

![img](https://play.whizlabs.com/frontend/web/media/2020/01/07/image16.png)

![img](https://play.whizlabs.com/frontend/web/media/2020/07/14/task_id_48_introduction_to_simple_queuing_service_(sqs).png)

## Estudo de caso:

1. Considere um exemplo de uma grande venda relâmpago em um site de comércio eletrônico onde as pessoas compram e vendem uma ampla gama de produtos. A exigência é que todas as solicitações, no que diz respeito ao comprador e ao vendedor, sejam processadas na ordem em que são recebidas pela fila. Para cumprir esse requisito, usaremos a fila FIFO.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/07/image13.png)

1. Uma empresa de telefonia móvel está realizando uma venda relâmpago de seu novo modelo com ótimos recursos e ao melhor preço. Espera-se que um grande número de compradores faça pedidos. A empresa mantém ações por um período limitado, por isso é importante rastrear o pedido que chega primeiro. Sua venda relâmpago recebe uma grande resposta e agora está previsto que apenas os compradores que fizerem o pedido primeiro receberão o produto.
2. Vamos entender como as mensagens entram e saem de nossa fila FIFO. Suponha que o aplicativo de consumo solicite um lote de até 300 mensagens, o AWS SQS começa a preencher o lote com a mensagem mais antiga (REQ A1) e continua enchendo a fila até que o lote esteja cheio. Em nosso caso, suponha que o lote contém apenas três solicitações e agora a fila está vazia. Depois que o lote de mensagens sai da fila, o SQS considera o lote em **andamento** até que seja completamente processado ou que o tempo limite de visibilidade expire.

![img](https://play.whizlabs.com/frontend/web/media/2020/01/07/image4.png)

1.  Quando você tem um único aplicativo de consumo para a saída da fila, isso é fácil de processar. Receberá as mensagens, fará o seu processamento e apagará as mensagens. Agora, o aplicativo de consumo está pronto para processar o próximo lote de mensagens. Você também pode adicionar um grupo de dimensionamento automático para dimensionar seu poder de processamento, dependendo dos requisitos.

**Observação: o** SQS não libera o próximo lote de mensagens até que o primeiro lote seja excluído.

Detalhes da Tarefa

1. Faça login no AWS Management Console.
2. Crie FIFO e fila padrão usando o console.
3. O que é Long Polling e configuração de Long Polling para a fila.
4. O que é Visibility Timeout e configurando Visibility Timeout.
5. O que é Delay Queue e configurar Delay Queue.
6. Limpe a fila e verifique o mesmo.
7. Pontos SQS a serem lembrados.
8. Validação do laboratório.





## Etapas de laboratório

### Tarefa 1: crie FIFO e fila padrão usando o console

1. Navegue até o menu Serviços na parte superior, procure **SQS** e selecione-o. Você será redirecionado para a página do console SQS. Clique no link **Criar fila** .
   ![img](https://lh4.googleusercontent.com/fJTp2RkAy3w-Ba6HVZnLexz3tr0YPVgzWUG49roXBRAk97raTgn3oQ2l_2F8_qO0U_DDm7gOBMfwdoJdg4HE4FBSVfl97wG7YI9Vqo9sWysuQv7smevmT3fwyVTyGtI4tsOcJHg9=s0)
2. Certifique-se de que você está na região de **N. Virginia** .
3. **Detalhes :**  
   - Tipo: Selecione **FIFO**    
   - Nome: Digite ***MyWhizQueue.fifo\***

- **Nota** O nome de uma fila FIFO deve terminar com o sufixo **.fifo** .

![img](https://lh5.googleusercontent.com/MYnAYgEkcYYdF1ehK_mhIe8Ekx85g9ERr-fNxWW1ZIjwpbLNcyfC2laiRXz-2nIzFCYQU8sjMyzsHp-oq8ftE5fwTwKU0ecctiQCxu7DLfETJtVInNCJJ61B8JyoA6ff-ho8ibxz=s0)

1. Deixe tudo como **padrão** e clique em![img](https://lh4.googleusercontent.com/rkzG3Iq2qUfOBuwssqLgcP4V4ZTkki1KsZLlcWI9KZF9i5SMSzSVjK4ZGEr2kmd677R5Zbiq1jcqWyEmpwzrcWvoYhCW2UxjHTlfogw9WgFGiN3pd33RTlnfoGaquXbRSct3KrwB=s0)

![img](https://lh4.googleusercontent.com/O_tPqHGGxXpAYxaRKz-6Sz5XlDzPDX-JRHoddpEvXbbepJ4SyPdJ5ddo4WGNkMOvUXoak0au8758CGE3xyWKjTHgChyovlYo4yyHTukS7V6WKNWCnLFZXI5Ks9D-ma-5heaozOTV=s0)

1. Depois de clicar em **Criar fila,** você receberá uma mensagem de sucesso *.* Volte para o painel de filas, uma fila FIFO é criada conforme mostrado na imagem abaixo.

   ![img](https://lh5.googleusercontent.com/i_VAExf3DuR0iahLUSRIFKt9jqIvH3lQFF9QcRVZEmTGLTALS5ZRNcqb33cvV8sAYx5-EVULse2PKjS2q-5nKiMHa6azwrZpZgiM6zTP-hpI_4GwHfa7l24esD-bUEPEkkB89i_8=s0)

2. Estaremos criando uma **fila padrão** , com todas as opções padrão. A única diferença é que não fornecemos o sufixo **.fifo** ao criar a fila. Encontre a imagem abaixo.

![img](https://lh4.googleusercontent.com/jbZA6K0wDQlz8SFxbXIaFdEIiBclGZj0w8A-kJyMmiN3fZQmSXpuxRh6yN8v4GKQ7Aoe6tZT0TMzYkVopoIQKhnGviO4_DjF1-l0J0n7deAIEeZQQSJ2LUNpne-KDgByWm77tFVP=s0)

1. A coluna **Tipo** ajuda a distinguir a fila padrão da fila FIFO rapidamente. Para uma fila FIFO, a coluna de **deduplicação baseada em conteúdo** exibe se **cada uma de suas mensagens tem um corpo exclusivo** ativado ou não.
2. Clique em **MyWhizQueue.fifo** para obter informações detalhadas sobre todos os parâmetros importantes, incluindo **ARN, nome e URL** da fila.

1. Estaremos agora enviando uma mensagem de nossa fila FIFO.
2. Clique em **Enviar e receber mensagens** .

![img](https://play.whizlabs.com/frontend/web/media/2021/09/16/fifo_36_01.png)

1. Enviar mensagem

- Corpo da mensagem: Digite ***minha primeira mensagem de fila***
- ID do grupo de mensagens: digite ***group123\***
- ID de eliminação de duplicação de mensagens: digite ***id23\***

1. Agora clique em **Enviar mensagem.**

1. Depois de enviar uma mensagem, você receberá uma confirmação.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/16/send_message_40_09.png)

1. Depois de enviar a mensagem, podemos ver que a **mensagem disponível** muda para 1.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/16/receive_message.png)

1. Da mesma forma, enviar mais algumas mensagens com diferentes **Corpo da mensagem** , **mensagem de grupo ID** e **desduplicação mensagem** .
2. Após o envio das mensagens, **Mensagem disponível** muda para o número de mensagens enviadas.
3. Agora, para obter todas as mensagens enviadas, clique em **Pesquisar mensagens** na seção **Receber mensagens** .
4. Agora podemos ver que a coluna da mensagem foi preenchida com as mensagens.
5. Em seguida, clique na mensagem para ver seu corpo.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/22/fifo_queue_56_54.png)

![img](https://play.whizlabs.com/frontend/web/media/2021/09/22/fifo_msg.png)

1. **Portanto, enviamos e recebemos mensagens no console com sucesso.**
2. Da mesma forma, tentaremos com a fila **Padrão** para enviar a mensagem.
3. Clique em **Enviar e receber mensagens** .

![img](https://lh6.googleusercontent.com/FyiFHL1DgUvL5VcD7sd1vm7bVErdle8IVURNuKmRNHOVXVNidpi8UvN3sR2EdXKm7_1I5a-B52yPMZkQcLAI-d69H9Uyoi9i-sLS3XtoxsN2mTOsB1ewdX-OmMfdpllz8FYwTDNG=s0)

1.  Enviar mensagem:

- Corpo da mensagem: Insira ***minha primeira fila de mensagens padrão***
- Agora clique em **Enviar mensagem**

1. Assim que a mensagem for entregue, você receberá uma confirmação de entrega bem-sucedida.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/16/send_message_standard.png)

1. Depois de enviar a mensagem, podemos ver que a **mensagem disponível** muda para 1.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/16/receive_message_47_42.png)

1. Da mesma forma, envie mais algumas mensagens com um **corpo de mensagem** diferente .
2. Após o envio das mensagens, **Mensagem disponível** muda para o número de mensagens enviadas.
3. Agora, para obter todas as mensagens enviadas, clique em **Pesquisar mensagens** na seção **Receber mensagens** .
4. Em seguida, clique nas mensagens para ver seu corpo.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/22/standard_queue_00_57.png)

![img](https://play.whizlabs.com/frontend/web/media/2021/09/22/standard_message.png)

1. **Portanto, enviamos e recebemos mensagens no console com sucesso.**
2. Vamos tentar entender os outros parâmetros como **Long Polling** e como ele funciona no SQS. Antes de ir para o laboratório, tente se concentrar no que é exatamente a pesquisa longa e quando deve ser usada.

### Tarefa 2: O que é Long Polling e Configurando Long Polling

1. **Sondagem longa:** vamos tentar entender por quanto tempo a pesquisa funciona e por que devemos usá-la. 

- Por exemplo, se nosso aplicativo requer mensagens SQS, ele chamará a  função **RecieveMessage** em segundo plano. **O ReceiveMessage** verificará a presença de quaisquer mensagens na fila e retornará imediatamente, com ou sem mensagens.
- Chamar uma  função **ReceiveMessage** em nosso aplicativo está bem de acordo com o requisito, mas e se o cliente SQS verificar repetidamente a mensagem na fila para novas mensagens. Isso é um problema, pois as chamadas contínuas para a  função **ReceiveMessage** exigirão muitos ciclos de CPU e amarrarão um encadeamento. Nessa situação, usaremos pesquisas longas. A única modificação que precisamos fazer é atualizar nosso argumento **WaitTimeSeconds** para 1-20 segundos.
- Agora, se a fila estiver vazia, a chamada aguardará **WaitTimeSeconds** para que uma mensagem entre na fila antes de retornar. Se as mensagens chegarem antes do tempo limite, a chamada retornará a mensagem imediatamente.

1. Lembre-se de que se o tempo de espera para a  ação da API **ReceiveMessage** for maior que 0, a sondagem longa está em vigor. A sondagem longa é econômica porque você não está pesquisando constantemente uma fila vazia.
2. Por padrão, o Amazon SQS usa pesquisa curta, consultando apenas um subconjunto de seus servidores (com base em uma distribuição aleatória ponderada) para determinar se alguma mensagem está disponível para uma resposta.

1. Vamos tentar fazer isso funcionar em nossa fila existente configurando Long Polling. Selecione qualquer fila (padrão ou FIFO) da lista e clique em **Editar** para fazer alterações em nossa fila. Estaremos selecionando a fila FIFO como exemplo.
   ![img](https://play.whizlabs.com/frontend/web/media/2021/05/06/edit_option.png)
2. Depois de selecionar **Editar Fila,** atualize o parâmetro **Tempo de Espera de Recebimento de Mensagens** . Pode ser qualquer valor entre 0 a 20 segundos. Em nosso exemplo, mudamos para **10 segundos** . Isso fará com que nossa longa votação entre em vigor. Se mantivermos o valor como 0 ou padrão, é considerada uma pesquisa curta. Depois de fazer as alterações, clique em **Salvar alterações** .

![img](https://play.whizlabs.com/frontend/web/media/2020/07/31/screenshot_15.png)

### Tarefa 3: O que é o tempo limite de visibilidade e configuração do tempo limite de visibilidade

1. O tempo limite de visibilidade é uma duração de tempo em que o AWS SQS evita que os outros componentes recebam e processem as mensagens.
2. **Estudo de caso:** 
   - Vamos tentar entender a definição por um exemplo. Portanto, se você mantiver o tempo limite de visibilidade em 1 minuto para um trabalho de big data, o que acontecerá é que a mensagem voltará para a fila porque não será concluída em 1 minuto.
   - Digamos que demore cinco minutos para realmente processar uma grande quantidade de dados. A mensagem ficará visível na fila e, em seguida, outra instância do EC2 irá capturá-la. Por causa disso, você pode entregar suas mensagens várias vezes porque o tempo limite de visibilidade é muito baixo.
3. O tempo limite de visibilidade padrão é **30 segundos** .
4. Aumente-o se sua tarefa levar> **30 segundos** .
5. O máximo que pode chegar é de **12 horas** .
6. Vamos tentar fazer isso funcionar em nossa fila existente, configurando o tempo limite de visibilidade. Selecione qualquer fila (padrão ou FIFO) da lista e clique em **Editar** para fazer alterações em nossa fila. Estaremos selecionando a fila FIFO como exemplo.
   ![img](https://play.whizlabs.com/frontend/web/media/2021/05/06/edit_option.png)
7. Depois de selecionar **Editar,** atualize o parâmetro **Tempo limite de visibilidade padrão** . Pode ser qualquer valor entre 0 segundos e 12 horas. Em nosso exemplo, mudamos para **5 minutos** . 
8. Depois de fazer a alteração, clique em **Salvar** na parte inferior para trazer as alterações com efeito .

![img](https://play.whizlabs.com/frontend/web/media/2020/07/31/screenshot_16.png)

### Tarefa 4: O que é fila de atraso e configuração da fila de atraso

1. A fila de espera nos permite atrasar / adiar a entrega de uma nova mensagem por um determinado período de tempo. Podemos facilmente transformar qualquer fila em uma fila de atraso configurando **SetQueueAttributes** para definir o atributo **DelaySeconds** da fila . 
   - Se criarmos uma fila de atraso, qualquer mensagem enviada para essa fila permanecerá invisível para o consumidor pelo tempo de atraso configurado.
   - Para criar uma fila de atraso, defina o atributo **DelaySeconds** com um valor entre 0 e 900 segundos.
2. **Estudo de caso:** 
   - Vamos tentar entender a definição por um exemplo. Considere um caso em que um aplicativo está tentando inserir milhões de dados em um banco de dados. O aplicativo enviará uma mensagem sobre a disponibilidade desses novos dados que foram recentemente inseridos em outros subsistemas, que por sua vez processam essa mensagem e, posteriormente, fazem atualizações na mesma linha. Agora existe uma dependência de que até que o primeiro lote conclua seu trabalho e seja confirmado após as atualizações, o próximo lote não deve ser acionado. Se a mensagem for disparada antes que as atualizações sejam concluídas, ela falhará no próximo lote. Nesse caso, o atraso na entrega ajuda.
3. Vamos tentar fazer isso funcionar em nossa fila existente configurando o **Atraso** na **entrega** . Selecione qualquer fila (padrão ou FIFO) da lista e clique em **Editar** para fazer alterações em nossa fila. Estaremos selecionando a fila FIFO como exemplo.
   ![img](https://play.whizlabs.com/frontend/web/media/2021/05/06/edit_option.png)
4. Depois de selecionar **Editar,** atualize o parâmetro **Atraso** na **entrega** . Pode ser qualquer valor entre 0 segundos e 15 minutos. Em nosso exemplo, mudamos para **60 segundos** .
5. Depois de alterar, clique em **Salvar** na parte inferior para que as alterações tenham efeito.

![img](https://play.whizlabs.com/frontend/web/media/2020/07/31/screenshot_18.png)

### Tarefa 5: limpe a fila e verifique a mesma

1. Neste tópico, tentaremos limpar a fila. Antes de passarmos para a limpeza, vamos entender primeiro o que acontece se limparmos uma fila.

- A opção Purge Queue nos permite excluir as mensagens na fila.
- O processo de exclusão da mensagem pode levar até 60 segundos, dependendo do tamanho da fila.
- **Observação** : depois de chamar a ação **Limpar filas** , as mensagens não podem ser recuperadas da fila.

1. Vamos tentar fazer essa alteração em nossa fila existente. Clique em Queue Option e em **Actions** selecione **Purge** .

**![img](https://play.whizlabs.com/frontend/web/media/2021/05/06/purge.png)**

1. Depois de selecionar a  opção de **eliminação** , será solicitada uma confirmação. Digite a frase **purge** e clique em purge.

   ![img](https://play.whizlabs.com/frontend/web/media/2020/07/31/screenshot_20.png)

2. Para verificar se a eliminação ocorreu na fila fifo, clique em enviar e receber mensagens e, a seguir, clique em Pesquisar mensagens.

3. Ele não mostrará nenhuma mensagem que verifique se a limpeza foi bem-sucedida.

![img](https://play.whizlabs.com/frontend/web/media/2021/09/16/purge.png)

1. Da mesma forma, repita a eliminação na fila padrão e verifique o mesmo.

### Tarefa 6: pontos SQS para lembrar

1. A diferença básica entre **Delay Queue** e **Visibility Timeout** é que a Delay Queue oculta a mensagem quando ela é adicionada pela primeira vez na fila, enquanto o Visibility Timeout oculta uma mensagem somente depois que a mensagem é recuperada da fila.
2. **As mensagens a bordo** são mensagens no SQS que foram recebidas por um consumidor, mas ainda não foram excluídas.
3. No máximo 120.000 mensagens podem permanecer na fila.
4. O tamanho da mensagem é **256 KB** .
5. Tem um período de retenção padrão.
6. O SQS é baseado em pull, não em push.