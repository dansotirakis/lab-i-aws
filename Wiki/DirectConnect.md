# AWS Direct Connect

​	Criar uma conexão de rede dedicada para a AWS! O serviço de nuvem AWS Direct Connect é o **caminho mais curto para seus recursos na AWS.**

​	Seu tráfego de rede permanece todo o tempo na rede global da AWS e **nunca entra na Internet pública.** Isso **reduz as probabilidades de gargalos** ou aumentos inesperados de latência. **Ao criar uma nova conexão**, você pode **escolher uma conexão hospedada fornecida por um parceiro de entrega do AWS Direct Connect ou uma conexão dedicada da AWS** e implantá-la em mais de 100 locais do AWS Direct Connect ao redor do mundo.

​	O AWS Direct Connect **está disponível em locais em todo o mundo** para garantir que você possa fazer conexões perto de onde você precisa.

**Conexões dedicadas** são conexões físicas entre sua porta de rede e uma porta na rede da AWS dentro de um local do AWS Direct Connect.

**Conexões hospedadas** são conexões lógicas que um parceiro de entrega do AWS Direct Connect provisiona em seu nome.

**A transferência de dados de saída (DTO)** é o tráfego de rede cumulativo que passa pelo AWS Direct Connect e é enviado para destinos fora da AWS.

**A transferência de dados de entrada** é o tráfego de rede enviado para a AWS de origens externas, passando pelo AWS Direct Connect.

## AWS Direct Connect SiteLink

- **Você pode enviar dados entre locais do AWS Direct Connect** para criar conexões privadas de rede entre os escritórios e datacenters na sua rede global.

## Velocidades de conexão de até 100 Gbps

- O AWS Direct Connect está **disponível em velocidades a partir de 50 Mbps e chegando até 100 Gbps** para que você possa encontrar sua conexão ideal.

## Opções de criptografia do MACsec e IPsec

- Adicione proteção extra às comunicações entre seus datacenters, filiais de escritório ou instalações de colocalização com as diversas opções de criptografia disponíveis.

## SiteLink

- O AWS Direct Connect SiteLink cria conexões de rede privadas de ponta a ponta entre escritórios, datacenters e instalações de colocalização na sua rede global.

## Várias opções de implantação

- As conexões dedicadas criam um link para a AWS usando uma porta Ethernet de 1 Gbps, 10 Gbps ou 100 Gbps.

## Conexão entre locais usando o SiteLink

- Quando você envia tráfego de rede de um point of presence (PoP – ponto de presença) do AWS Direct Connect para outro, por exemplo, ao conectar dois ou mais datacenters ou filiais de escritórios, há dois fatores que determinam custos adicionais: horas e transferência de dados do SiteLink.

## Preços

### Horas de portas: conexões dedicadas

| Capacidade | Tarifa de hora-porta (Excluindo o Japão) | Tarifa de hora-porta no Japão |
| :--------- | :--------------------------------------- | :---------------------------- |
| 1 Gbps     | USD 0,30/hora                            | USD 0,285/hora                |
| 10 Gbps    | USD 2,25/hora                            | USD 2,142/hora                |
| 100 Gbps   | USD 22,50/hora                           | USD 22,50/hora                |

### Horas de portas: Conexões hospedadas

| Capacidade | Tarifa de hora-porta (Excluindo o Japão) | Tarifa de hora-porta no Japão |
| :--------- | :--------------------------------------- | :---------------------------- |
| 50 Mbps    | USD 0,03/hora                            | USD 0,029/hora                |
| 100 Mbps   | USD 0,06/hora                            | USD 0,057/hora                |
| 200 Mbps   | USD 0,08/hora                            | USD 0,076/hora                |
| (Mbps)     | USD 0,12/hora                            | USD 0,114/hora                |
| (Mbps)     | USD 0,16/hora                            | USD 0,152/hora                |
| 500 Mbps   | USD 0,20/hora                            | USD 0,190/hora                |
| 1 Gbps*    | USD 0,33/hora                            | USD 0,314/hora                |
| 2 Gbps*    | USD 0,66/hora                            | USD 0,627/hora                |
| 5 Gbps*    | USD 1,65/hora                            | USD 1,568/hora                |
| 10 Gbps    | USD 2,48/hora                            | 2,361 USD/hora                |

## Cenários de conexão

| Cenário                                                | Método                                                       |
| :----------------------------------------------------- | :----------------------------------------------------------- |
| Conectar diretamente em um local do AWS Direct Connect | Conecte diretamente a um dispositivo da AWS de seu roteador em um [local do AWS Direct Connect](https://aws.amazon.com/pt/directconnect/locations/) usando conexões de 1 Gbps, 10 Gbps ou 100 Gbps. (Confira [esta página](https://aws.amazon.com/pt/directconnect/locations/) para ver se a sua localização preferida oferece suporte a conexões de 10 e 100 Gbps). |
| Conexão a partir de suas instalações                   | Trabalhe com um parceiro da [Rede de parceiros da AWS](https://aws.amazon.com/pt/directconnect/partners/) (APN) ou um provedor de rede que ajudará a conectar um roteador de um datacenter, escritório ou ambiente de colocalização para um [local do AWS Direct Connect](https://aws.amazon.com/pt/directconnect/locations/). O provedor de rede não precisa ser um membro do APN para essa conexão. |
| Conexão hospedada por um parceiro AWS Direct Connect   | Trabalhe com um parceiro da [Rede de parceiros da AWS](https://aws.amazon.com/pt/directconnect/partners/) (APN) que criará uma conexão hospedada para você. Cadastre-se na AWS e siga as instruções para [aceitar uma conexão hospedada](https://docs.aws.amazon.com/directconnect/latest/UserGuide/getting_started.html#get-started-accept-hosted-connection). |