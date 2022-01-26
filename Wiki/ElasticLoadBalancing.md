# ELB

A segurança da nuvem na AWS é a nossa maior prioridade. Como cliente da AWS, você se beneficiará de um datacenter e de uma arquitetura de rede criados para atender aos requisitos das empresas com as maiores exigências de segurança.

A segurança é uma responsabilidade compartilhada entre a AWS e você. O [modelo de responsabilidade compartilhada](http://aws.amazon.com/compliance/shared-responsibility-model/) descreve isso como a segurança da nuvem e a segurança na nuvem:

- **Segurança da nuvem**: a AWS é responsável pela proteção da infraestrutura que executa produtos da AWS na Nuvem AWS. A AWS também fornece serviços que podem ser usados com segurança. Auditores externos testam e verificam regularmente a eficácia da nossa segurança como parte dos [Programas de conformidade da AWS](http://aws.amazon.com/compliance/programs/). Para saber mais sobre os programas de conformidade que se aplicam ao Elastic Load Balancing, consulte[AWSServiços da no escopo por programa de conformidade](http://aws.amazon.com/compliance/services-in-scope/).
- **Segurança da nuvem**: sua responsabilidade é determinada pelo serviço da AWS que você usa. Você também é responsável por outros fatores, incluindo a confidencialidade de seus dados, os requisitos da sua empresa e as leis e regulamentos aplicáveis.

Esta documentação ajuda você a entender como aplicar o modelo de responsabilidade compartilhada ao usar o Elastic Load Balancing. Ela mostra como configurar o Elastic Load Balancing para atender aos objetivos de segurança e conformidade. Você também saberá mais sobre como usar outrosAWSServiços da que ajudam a monitorar e proteger os recursos do Elastic Load Balancing.

Com um[Gateway Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/gateway/), você é responsável por escolher e qualificar o software dos fornecedores de equipamentos. Você deve confiar no software do appliance para inspecionar ou modificar o tráfego do balanceador de carga, que opera na camada 3 do modelo de Interconexão de Sistemas Abertos (OSI), a camada de rede. Os fornecedores de equipamentos listados como[Elastic Load Balancing](http://aws.amazon.com/elasticloadbalancing/partners/)integraram e qualificaram seu software de equipamento comAWS. Você pode colocar um grau mais alto de confiança no software do appliance dos fornecedores nesta lista. No entanto,AWSnão garante a segurança ou a confiabilidade do software desses fornecedores.

- https://docs.aws.amazon.com/pt_br/pt_br/elasticloadbalancing/latest/userguide/load-balancer-vpc-endpoints.html)

## Tipos de balanceadores de carga

O Elastic Load Balancing oferece suporte aos seguintes tipos de balanceadores de carga: balanceadores de carga da aplicação, balanceadores de carga da rede e balanceadores de carga clássicos. Os serviços do Amazon ECS podem usar esses tipos de balanceador de carga.

### Balanceador de carga da aplicação

Um balanceador de carga da aplicação toma decisões de roteamento na camada da aplicação (HTTP/HTTPS), oferece suporte ao roteamento com base em caminho e pode encaminhar solicitações para uma ou mais portas em cada instância de contêiner no cluster. Os balanceadores de carga da aplicação oferecem suporte ao mapeamento de porta de host dinâmico. Por exemplo, se a definição de contêiner da tarefa especifica a porta 80 para uma porta de contêiner NGINX e a porta 0 para a porta do host, a porta do host é escolhida dinamicamente com base no intervalo de portas temporário da instância de contêiner (como entre 32768 e 61000 na AMI otimizado para Amazon ECS mais recente).

### Load balancer de rede

Um balanceador de carga da rede toma decisões de roteamento na camada de transporte (TCP/SSL). Ele pode processar milhões de solicitações por segundo. Após o load balancer receber uma conexão, ele seleciona um destino no grupo de destino para a regra padrão usando um algoritmo de roteamento de hash de fluxo. Ele tenta abrir uma conexão TCP para o destino selecionado na porta especificada na configuração do listener. Ele encaminha a solicitação sem modificar os cabeçalhos.

### Balanceadores de carga de gateway

Os balanceadores de carga de gateway permitem que você implante, escale e gerencie dispositivos virtuais, como firewalls, sistemas de detecção e prevenção de intrusões e sistemas de inspeção profunda de pacotes. Eles combinam um gateway de rede transparente (ou seja, um único ponto de entrada e saída para todo o tráfego) e distribui o tráfego enquanto escala os dispositivos virtuais segundo a demanda. Um balanceador de carga de gateway opera na terceira camada do modelo Open Systems Interconnection (OSI), a camada de rede. Ele escuta todos os pacotes IP em todas as portas e encaminha o tráfego para o grupo de destino especificado na regra do listener. Ele mantém a perdurabilidade dos fluxos para um dispositivo de destino específico usando 5 tuplas (para fluxos TCP/UDP) ou 3 tuplas (para fluxos não TCP/UDP).

## Atraso do cancelamento do registro

O Elastic Load Balancing interrompe o envio de solicitações aos destinos cujo registro está sendo cancelado. Por padrão, o Elastic Load Balancing aguarda 300 segundos antes de concluir o processo de cancelamento do registro, o que pode ajudar a solicitações em andamento para o destino a serem concluídas. Para alterar a quantidade de tempo que o Elastic Load Balancing aguarda, atualize o valor de retardo de cancelamento do registro.

O estado inicial de um destino que terá o registro cancelado é `draining`. Depois de decorrido o retardo de cancelamento do registro, processo será concluído e o estado do destino será `unused`. Se o destino for parte de um grupo do Auto Scaling, ele poderá ser encerrado e substituído.

Se um destino cujo registro estiver sendo cancelado não tiver solicitações em andamento nem conexões ativas, o Elastic Load Balancing concluirá imediatamente o processo de cancelamento de registro, sem aguardar o tempo de espera transcorrer. No entanto, mesmo que o cancelamento do registro de destino seja concluído, o status do destino é exibido como`draining`até que o tempo limite de atraso de cancelamento do registro expire. Depois que o tempo limite expirar, o destino faz a transição para um`unused`estado.

Se cancelar o registro de um destino encerrar a conexão antes de o retardo de cancelamento do registro passar, o cliente receberá uma resposta de erro de nível 500.

## Grupos de destino

Cada grupo de destino é usado para rotear solicitações para um ou mais destinos registrados. Ao criar cada regra do listener, especifique um grupo de destino e condições. Quando uma condição da regra é atendida, o tráfego é encaminhado para o grupo de destino correspondente. Você pode criar grupos de destino diferentes para tipos de solicitações diferentes. Por exemplo, você pode criar um grupo de destino para solicitações gerais e outros grupos de destino para solicitações para os microsserviços do aplicativo. Para obter mais informações, consulte Componentes Application Load Balancer.

## Algoritmo de roteamento

Por padrão, o algoritmo de roteamento de ida e volta é usado para rotear solicitações no nível do grupo de destino. Em vez disso, você pode especificar o algoritmo de roteamento de solicitações menos pendentes.