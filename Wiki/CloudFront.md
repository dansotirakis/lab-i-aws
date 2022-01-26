# Amazon CloudFront

![  				Como o CloudFront funciona  			](https://docs.aws.amazon.com/pt_br/AmazonCloudFront/latest/DeveloperGuide/images/how-you-configure-cf.png)

O Amazon CloudFront agiliza a distribuição do seu conteúdo web estático e dinâmico, como arquivos .html, .css, .php e arquivos de imagem e mídia. Quando os usuários solicitam seu conteúdo, o CloudFront o fornece por meio de uma rede mundial de pontos de presença que fornecem baixa latência e alto desempenho.

O CloudFront acelera a distribuição do seu conteúdo encaminhando cada solicitação de usuário por meio da rede de estrutura da AWS para o local da borda capaz de veicular melhor seu conteúdo. Normalmente, esse é um servidor de borda do CloudFront que fornece a entrega mais rápida ao visualizador.

Ao desenvolver o site ou a aplicação, use o nome de domínio fornecido pelo CloudFront para seus URLs.

Ex:. ` d111111abcdef8.cloudfront.net` =  `http://d111111abcdef8.cloudfront.net/[object-name]`

## Como configurar

1. Especifique os servidores de origem, como um bucket do Amazon S3 ou seu próprio servidor HTTP, dos quais o CloudFront obtém os arquivos que serão distribuídos de pontos de presença do CloudFront no mundo todo.
2. Faça upload dos seus arquivos nos servidores de origem.
3. Crie uma distribuição do CloudFront, que informa ao CloudFront de quais servidores de origem obter os arquivos quando os usuários os solicitam no site ou na aplicação.
4. O CloudFront atribui um nome de domínio à nova distribuição que pode ser visto no console do CloudFront ou que é retornado na resposta a uma solicitação programática, por exemplo, uma solicitação de API.
5. O CloudFront envia a configuração (mas não o conteúdo) da distribuição a todos os pontos de presença ou POPs, que são conjuntos de servidores em datacenters geograficamente dispersos nos quais o CloudFront armazena cópias dos objetos em cache.

Opcionalmente, é possível configurar o servidor de origem para adicionar cabeçalhos aos arquivos a fim de indicar o tempo de permanência dos arquivos no cache dos pontos de presença do CloudFront. Por padrão, cada arquivo permanece em um ponto de presença por 24 horas antes de expirar.