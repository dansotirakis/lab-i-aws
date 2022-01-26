

# AWS Virtual Private Network VPN

As soluções do AWS Virtual Private Network estabelecem conexões seguras entre redes locais, escritórios remotos, dispositivos de clientes e a rede global da AWS. O AWS VPN é composto por dois serviços: **AWS Site-to-Site** VPN e **AWS Client VPN**. Juntos, eles entregam uma solução de VPN na nuvem gerenciada, altamente disponível e elástica para proteger o tráfego da sua rede.

## O AWS Site-to-Site VPN 

- Cria túneis criptografados entre a sua rede e as Amazon Virtual Private Clouds ou os AWS Transit Gateways.

- Cria uma conexão segura entre o centro dos seus dados ou a filial e os seus recursos de nuvem da AWS. Para aplicativos distribuídos globalmente, a opção do Accelerated Site-to-Site VPN oferece maior desempenho trabalhando com o AWS Global Accelerator.

### Benefícios

1. **Altamente disponível** : O AWS Site-to-Site VPN oferece alta disponibilidade usando dois túneis em várias Zonas de disponibilidade na rede global da AWS.
2. **Seguro** : Com o AWS Site-to-Site VPN, você pode se conectar a um Amazon VPC ou ao AWS Transit Gateway da mesma maneira que se conecta a servidores locais.
3. **Monitoramento robusto** : O AWS Site-to-Site VPN lhe fornece a visibilidade da integridade da rede local e remota e monitora a confiabilidade e o desempenho de suas conexões VPN, integrando-se ao Amazon CloudWatch.
4. **Acelere aplicativos** : A opção do Accelerated Site-to-Site VPN melhora o desempenho da sua conexão VPN trabalhando com o AWS Global Accelerator.

![product-page-diagram_Accelerated-Site-to-Site-VPN_How-it-Works@2x](https://d1.awsstatic.com/diagrams/product-page-diagram_Accelerated-Site-to-Site-VPN_How-it-Works%402x.89c94ea4b307abe21f82d9fd453fe3c72cacb2a3.png)

### Preço

- Taxa de conexão do AWS Site-to-Site VPN: **você será cobrado pela sua conexão do AWS Site-to-Site VPN** de hora em hora, isto é, **por cada hora em que a conexão ficar ativa**. Para esta região da AWS, a taxa é de **0,05 USD por hora.**
- **Taxa de transferência de dados para fora**: seu primeiro GB é gratuito, você será cobrado por 499 GB a 0,09 USD por GB. O resultado será uma **cobrança de 44,91 USD.**
- O resultado será uma **cobrança total de 80,,91 USD**.

## AWS Client VPN

### Benefícios

1. **Totalmente gerenciado**: O AWS Client VPN automaticamente toma conta da implantação, do provisionamento de capacidades e de atualizações de serviços
2. **Autenticação avançada**: Muitas empresas exigem a multi-factor authentication (MFA) e autenticação federada de sua solução VPN.
3. **Elástico**: Os serviços tradicionais de VPN no local são limitados pela capacidade do hardware onde são executados. 
4. **Acesso remoto**: Diferentemente de outros serviços de VPN locais, o AWS Client VPN permite que os usuários se conectem à AWS e a redes locais utilizando uma única conexão de VPN.

![Como funciona](https://d1.awsstatic.com/diagrams/Product-Page-Diagram_Aws-Client-VPN-Connect%402x.7e31b8a9dc7f38312794b311d37faf145adc0f96.png)

### Preço

| Operação                                  | Preço             |
| ----------------------------------------- | ----------------- |
| Associação de endpoints do AWS Client VPN | 0,10 USD por hora |
| Conectividade do AWS Client VPN           | 0,05 USD por hora |

No AWS Client VPN, **você é cobrado pelo número de conexões de cliente ativas por hora e pelo número de sub-redes associadas ao Client VPN por hora.** Você começa criando um endpoints de Client VPN e associando sub-redes a esse endpoint.

- Você será cobrado pela associação ao endpoints do AWS Client VPN por hora. Para esta região da AWS, a taxa é de 0,10 USD por hora.
- **10 conexões ativas do Client VPN por 1 hora.** A cobrança da conexão do Client VPN **será de 0,50 USD**.
- O resultado será **uma cobrança de 0,60 USD**.

## Observações

A AWS VPN estabelece conexões seguras entre redes locais, escritórios remotos, dispositivos cliente e a rede global da AWS. A AWS VPN não é uma conexão dedicada.