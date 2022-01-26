# AWS Storage Gateway

AWS Storage GatewayO conecta um dispositivo de software local a um armazenamento em nuvem para oferecer uma integração perfeita e segura entre um ambiente de TI local e oAWSInfraestrutura de armazenamento Você pode usar esse serviço para armazenar dados no Amazon Web Services Cloud para armazenamento escalável e econômico que ajuda a manter a segurança dos dados.

## Amazon S3 File Gateway

## Amazon FSx File Gateway

## Gateway de fitas

## Gateway de volumes

## Planejamento da implantação Storage Gateway

1. **Sua solução de armazenamento** – Escolha uma das seguintes soluções de armazenamento:

   - **Gateway de arquivos**— Você pode usar um gateway de arquivo para ingerir arquivos no Amazon S3 para uso por carga de trabalho baseada em objeto e armazenamento econômico para aplicativos de backup tradicionais. 
   - **Gateway de volume**— Ao usar gateways de volume, você pode criar volumes de armazenamento na Nuvem Amazon Web Services. Seus aplicativos locais podem acessá-los como destinos Internet Small Computer System Interface (iSCSI).
   - **Gateway de fita**— Se estiver procurando uma alternativa externa econômica, duradoura e de longo prazo para arquivamento remoto, dados, você pode implantar um gateway de fita. 

   **Opção de hospedagem**— Você pode executar o Storage Gateway localmente como máquina virtual (VM) ou dispositivo de hardware ou noAWSComo uma instância do Amazon EC2. Para obter mais informações, consulte 

[Requirements](https://docs.aws.amazon.com/pt_br/storagegateway/latest/userguide/Requirements.html). Se seu datacenter ficar off-line e você não tiver um host disponível, poderá implantar um gateway em uma Instância EC2. O Storage Gateway fornece uma Imagem de máquina da Amazon (AMI) que contém a imagem da VM do gateway.

O Storage Gateway **não é compatível diretamente com a replicação entre regiões**.