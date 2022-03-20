# VPCs

Uma Virtual Private Cloud (VPC) é uma rede virtual dedicada à sua conta da AWS. Ela é isolada de maneira lógica de outras redes virtuais na Nuvem da AWS.

![ 				Uma VPC que abrange as zonas de disponibilidade para sua região. 			](https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/images/vpc-diagram.png)

Depois de criar uma VPC, você pode adicionar uma ou mais sub-redes em cada zona de disponibilidade.

## Conceitos básicos sobre sub-redes

Uma *sub-rede* é uma gama de endereços IP na VPC. Você pode iniciar recursos da AWS, como instâncias do EC2, em uma sub-rede específica. Ao criar uma sub-rede, você especifica o bloco CIDR IPv4 para a sub-rede, o qual é um subconjunto do bloco CIDR da VPC.

## Tipos de sub-redes

- **IPv6-only** (Somente IPv4): a sua VPC será associada a um CIDR IPv4 ou a CIDRs IPv4 e IPv6.
- **Pilha dual** (IPv4 e IPv6): a sua VPC é associada a um CIDR IPv4 ou a CIDRs IPv4 e IPv6.
- **IPv6-only** (Somente IPv6): a sua VPC será associada a CIDRs IPv4 e IPv6.

## Configurações de sub-redes

**Auto-assign IP settings** (Atribuir configurações de IP automaticamente): esta opção permite que você defina a atribuição automática das configurações de IP para solicitar automaticamente um endereço IPv4 ou IPv6 público para uma nova interface de rede nesta sub-rede.

**Configurações de nomes baseados em recursos (RBN)**: permitem que você especifique o tipo de nome do host para as instâncias do EC2 nesta sub-rede e configure como as consultas de registros DNS A e AAAA são geridas.

## Diagrama de sub-redes e VPCs

![ 					VPC com múltiplas zonas de disponibilidade 				](https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/images/subnets-diagram.png)

- 1A, 2A e 3A representam as instâncias na sua VPC.
- A sub-rede 1 é uma sub-rede pública, a sub-rede 2 é uma sub-rede privada e a sub-rede 3 é uma sub-rede somente VPN.
- Um bloco CIDR IPv6 está associado à VPC e um bloco CIDR IPv6 está associado à sub-rede 1.
- Um gateway de Internet permite comunicação através da Internet; uma conexão de rede privada virtual (VPN) permite comunicação com a rede corporativa.



## Segurança de sub-rede

A AWS fornece dois recursos que você pode usar para aumentar a segurança da VPC: grupos de segurança e ACLs da rede. Os grupos de segurança controlam o tráfego de entrada e de saída de suas instâncias e as Network ACL controlam o tráfego de entrada e de saída de suas sub-redes.

