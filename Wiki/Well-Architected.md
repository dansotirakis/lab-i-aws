# AWS Well-Architected

Permite analisar e aprimorar as arquiteturas baseadas em nuvem e entender melhor o impacto comercial de suas decisões de projeto.

## 6 pilares Well-Architected framework

1. Segurança
2. Confiabilidade
3. Eficiência de performance
4. Otimização de custos
5. Excelência operacional
6. Sustentabilidade

### 1.  Segurança

O pilar Segurança apresenta uma visão geral dos princípios de design, melhores práticas e perguntas. Antes de projetar qualquer carga de trabalho, estabeleça práticas que influenciem a segurança.

#### Existem 7 princípios de segurnça do projeto para nuvem:

1. **Implementar uma forte base de identidade** : Implemente o princípio do privilégio mínimo e separe as tarefas com a autorização apropriada para cada interação com os recursos da AWS.
2. **Habilitar a rastreabilidade** : Monitore, alerte e audite ações e alterações em seu ambiente em tempo real.
3. **Aplicar segurança a todas as camadas** : Aplique uma abordagem de defesa detalhada com vários controles de segurança.
4. **Automatizar as melhores práticas de segurança** : Mecanismos de segurança baseados em software automatizados melhoram sua capacidade de ajustar a escala de forma segura, mais rápida e com custos reduzidos.
5. **Proteger dados em trânsito e em repouso** : Classifique seus dados em níveis de sensibilidade e use mecanismos, como criptografia, tokenização e controle de acesso, quando apropriado.
6. **Manter as pessoas afastadas dos dados** : Use mecanismos e ferramentas para reduzir ou eliminar a necessidade de acesso direto ou processamento manual de dados.
7. **Preparar-se para eventos de segurança** : Prepare-se para um incidente tendo políticas e processos de gerenciamento e investigação de incidentes alinhados aos requisitos organizacionais.

#### Melhores práticas

1. **Segurança** : Para operar sua carga de trabalho com segurança, você deve aplicar as melhores práticas gerais a todas as áreas de segurança. Use os requisitos e os processos que você definiu em excelência operacional em nível de carga de trabalho e também organizacional e aplique-os a todas as áreas.
2. **Identity and Access Management** : O Identity and Access Management é parte essencial de um programa de segurança da informação, que garante que apenas usuários autorizados e autenticados possam acessar seus recursos e somente da forma que você pretender.
3. **Detecção** : Você pode usar controles de detecção para identificar uma potencial ameaça ou incidente de segurança.
4. **Proteção de infraestrutura** : A proteção de infraestrutura abrange metodologias de controle, como defesa em profundidade, necessárias para atender às melhores práticas e obrigações organizacionais ou regulatórias.
5. **Proteção de dados** : Antes de criar a arquitetura de qualquer sistema, devem ser adotadas práticas fundamentais que influenciam a segurança.
6. **Resposta a incidentes** : Mesmo com controles preventivos e de detecção consolidados, sua organização ainda deve implementar processos para responder e mitigar o impacto potencial de incidentes de segurança.

#### Considerações

- SEC 1: Como você opera com segurança sua carga de trabalho?
- SEC 2: Como você gerencia identidades para pessoas e máquinas?
- SEC 3: Como você gerencia permissões para pessoas e máquinas?
- SEC 4: Como você detecta e investiga eventos de segurança?
- SEC 5: Como você protege seus recursos de rede?
- SEC 6: Como você protege seus recursos de computação?
- SEC 7: Como classificar meus dados?
- SEC 8: Como você protege seus dados em repouso?
- SEC 9: Como você protege seus dados em trânsito?
- SEC 10: Como você prevê, responde e se recupera de incidentes?

### 2. Confiabilidade

Para atingir a confiabilidade, você deve começar com as bases: um ambiente em que as cotas de serviço e a topologia de rede acomodam a carga de trabalho. Os requisitos fundamentais são aqueles que têm um escopo que vai além de uma única carga de trabalho ou projeto. Antes de criar a arquitetura de um sistema, é necessário instaurar os requisitos fundamentais que influenciam a confiabilidade

#### Os 5 Princípios de design para confiabilidade na nuvem

1. **Recuperação automática de falhas** :Ao monitorar os Key Performance Indicators (KPIs – Indicadores-chave de performance) de uma carga de trabalho, você pode acionar a automação quando um limite é ultrapassado.
2. **Teste os procedimentos de recuperação** :Em um ambiente no local, geralmente realiza-se o teste para provar que a carga de trabalho funciona em um cenário específico.
3. **Escale horizontalmente para aumentar a disponibilidade agregada da carga de trabalho** : Substitua um recurso grande por vários recursos pequenos para reduzir o impacto de uma única falha na carga de trabalho geral.
4. **Pare de tentar adivinhar sua capacidade** : Uma causa comum de falha nas cargas de trabalho no local é a saturação de recursos, quando as demandas impostas a uma carga de trabalho excedem a capacidade dela.
5. **Gerencie as alterações na automação** : As alterações na sua infraestrutura devem ser feitas por meio de automação.

#### Melhores práticas

1. **Fundamentos** : Os requisitos fundamentais são aqueles que têm um escopo que vai além de uma única carga de trabalho ou projeto.
2. **Arquitetura da carga de trabalho** : Uma carga de trabalho confiável começa com decisões iniciais de projeto que envolvem tanto o software quanto a infraestrutura.
3. **Gerenciamento de alterações** : As alterações na carga de trabalho ou no ambiente dela devem ser previstas e acomodadas para alcançar uma operação confiável da carga de trabalho.
4. **Gerenciamento de falhas** : Em qualquer sistema de complexidade razoável, espera-se que ocorram falhas. A confiabilidade exige que sua carga de trabalho reconheça as falhas no momento em que elas ocorrem e tome medidas para evitar que elas prejudiquem a disponibilidade.

#### Considerações

- REL 1: Como você gerencia as cotas e restrições de serviço?
- REL 2: Como você planeja sua topologia de rede?
- REL 3: Como você projeta sua arquitetura de serviços de carga de trabalho?
- REL 4: Como você projeta interações em um sistema distribuído para evitar falhas?
- REL 5: Como você projeta interações em um sistema distribuído para mitigar ou resistir a falhas?
- REL 6: Como você monitora recursos de carga de trabalho?
- REL 7: Como você projeta sua carga de trabalho para se adaptar às mudanças na demanda?
- REL 8: Como você implementa uma alteração?
- REL 9: Como você faz backup dos dados?
- REL 10: Como usar o isolamento de falhas para proteger sua carga de trabalho?
- REL 11: Como você projeta sua carga de trabalho para resistir a falhas de componentes?
- REL 12: Como testar a confiabilidade?
- REL 13: Como você planeja a recuperação de desastres (DR)?

### 3. Eficiência de performance

O pilar de eficiência de performance aborda as melhores práticas para gerenciar ambientes de produção. Este documento não aborda o projeto e o gerenciamento de ambientes e processos fora de produção, como integração ou entrega contínuas. 

#### Os 5 princípios de design do pilar de eficiência de performance

- **Democratizar tecnologias avançadas**: facilite a implementação de tecnologias avançadas para a sua equipe delegando tarefas complexas ao seu fornecedor de nuvem.
- **Tornar-se global em poucos minutos** a implantação de sua carga de trabalho em várias regiões da AWS em todo o mundo permite oferecer menor latência e uma melhor experiência para seus clientes a um custo mínimo.
- **Usar arquiteturas sem servidor** as arquiteturas sem servidor eliminam a necessidade de executar e manter servidores físicos para realizar atividades tradicionais de computação.
- **Experimentar com mais frequência** com recursos virtuais e automatizáveis, você pode executar rapidamente testes comparativos usando diferentes tipos de instâncias, armazenamento ou configurações.
- **Considerar a afinidade mecânica** use a abordagem tecnológica que se alinhe melhor às suas metas.

#### Melhores práticas

- **Seleção** : A solução ideal para uma carga de trabalho específica varia e, muitas vezes, as soluções combinam várias abordagens.
- **Análise** : As tecnologias de nuvem evoluem rapidamente e você deve garantir que os componentes da carga de trabalho estejam usando novas tecnologias e abordagens para melhorar continuamente a performance.
- **Monitoramento** : Após implementar sua carga de trabalho, é necessário monitorar a performance dela para que você possa corrigir todos os problemas antes que eles afetem seus clientes.
- **Concessões** : Ao arquitetar soluções, pense nas concessões para garantir uma abordagem ideal.

#### Considerações

- PERF 1: Como você seleciona a arquitetura de melhor performance?
- PERF 2: Como você seleciona sua solução de computação?
- PERF 3: Como você seleciona sua solução de armazenamento?
- PERF 4: Como você seleciona sua solução de banco de dados?
- PERF 5: Como você configura sua solução de redes?
- PERF 6: Como você aprimora sua carga de trabalho para aproveitar novas versões?
- PERF 7: Como você monitora seus recursos para garantir que eles estejam funcionando?
- PERF 8: Como você usa concessões para melhorar a performance?

### 4. Otimização de custos

#### Existem 5 princípios de design para otimização de custos na nuvem

1. **Implementar o gerenciamento financeiro na nuvem** : Para obter sucesso financeiro e acelerar a realização de valor empresarial na nuvem, você precisa investir em gerenciamento financeiro na nuvem/otimização de custos.
2. **Adotar um modelo de consumo** : Pague somente pelos recursos de computação necessários e aumente ou reduza o uso dependendo dos requisitos comerciais, não usando previsões elaboradas.
3. **Meça a eficiência geral** : Meça o resultado comercial da carga de trabalho e os custos associados com a sua entrega. Use essa medida para saber os ganhos obtidos com o aumento da saída e a redução de custos.
4. **Pare de gastar dinheiro em tarefas pesadas genéricas** : A AWS faz o trabalho pesado das operações de datacenter, como o armazenamento em rack, o empilhamento e a alimentação de servidores.
5. **Analisar e atribuir despesas** : A nuvem facilita a identificação precisa do uso e do custo dos sistemas, o que permite a atribuição transparente de custos de TI a proprietários de cargas de trabalho individuais.

#### Melhores práticas

1. **Praticar o gerenciamento financeiro na nuvem** : Com a adoção da nuvem, as equipes de tecnologia inovam mais rapidamente devido à redução dos ciclos de implantação de aprovação, aquisição e infraestrutura.
2. **Reconhecimento de despesas e usos** : A maior flexibilidade e agilidade que a nuvem permite incentiva a inovação, desenvolvimento e implantação em ritmo acelerado.
3. **Recursos econômicos** : Usar as instâncias e os recursos adequados para sua carga de trabalho é fundamental para economizar gastos.
4. **Gerenciar recursos de demanda e fornecimento** : Quando você passa para a nuvem, paga apenas pelo que precisa. Você pode fornecer recursos para atender à demanda da carga de trabalho no momento em que eles são necessários, o que elimina a necessidade de um provisionamento em excesso que é caro e desperdiça recursos.
5. **Otimizar ao longo do tempo** : Quando a AWS lança novos serviços e recursos, é recomendável analisar as escolhas de estruturas existentes para garantir que elas continuem sendo as mais econômicas.

#### Considerações

- COST 1: Como implementar o gerenciamento financeiro na nuvem?
- COST 2: Como você governa o uso?
- COST 3: Como você monitora o uso e os custos?
- COST 4: Como você desativa os recursos?
- COST 5: Como você avalia o custo ao selecionar serviços?
- COST 6: Como você atinge as metas de custo ao selecionar tamanho, número e tipo de recurso?
- COST 7: Como você usa os modelos de definição de preço para reduzir custos?
- COST 8: Como você planeja as cobranças de transferência de dados?
- COST 9: Como você gerencia a demanda e fornece recursos?
- COST 10: Como você avalia os novos serviços?

### 5. Excelência Operacional

O pilar Excelência operacional inclui como sua organização oferece suporte aos seus objetivos de negócios e sua capacidade de executar cargas de trabalho com eficácia, de obter insights sobre operações e de aprimorar continuamente processos e procedimentos de apoio para oferecer valor de negócios.

#### 5 princípios de design para excelência operacional na nuvem

1. **Execute operações como código** na nuvem, você pode aplicar a mesma disciplina de engenharia usada para o código do aplicativo em todo o ambiente.
2. **Faça alterações frequentes, pequenas e reversíveis** Faça alterações em pequenos incrementos que possam ser revertidos se não auxiliarem na identificação e resolução de problemas apresentados em seu ambiente (sem afetar os clientes quando possível).
3. **Refine os procedimentos operacionais com frequência** ao usar procedimentos de operação, procure oportunidades para melhorá-los.
4. **Antecipe falhas** execute exercícios “pré-mortem” para identificar as potenciais origens de falhas, para que assim elas possam ser removidas ou mitigadas.
5. **Aprenda com todas as falhas operacionais**  promova melhorias com as lições aprendidas em todos os eventos e falhas operacionais.

#### Melhores práticas

1. **Organizar** : Suas equipes precisam ter um entendimento compartilhado de toda a sua carga de trabalho, da função que desempenham em tudo isso e dos objetivos de negócios compartilhados a fim de definir as prioridades que permitirão o êxito dos negócios.
2. **Preparar** : Para se preparar para a excelência operacional, você precisa entender suas cargas de trabalho e os comportamentos esperados.
3. **Operar** : A operação bem-sucedida de uma carga de trabalho é medida pela obtenção de resultados de negócios e de clientes.
4. **Evoluir** : Você deve aprender, compartilhar e melhorar continuamente para manter a excelência operacional.

#### Considerações

- OPS 1: Como você determina quais são suas prioridades?
- OPS 2: Como você estrutura sua organização para dar suporte aos seus resultados comerciais?
- OPS 3: Como sua cultura organizacional oferece suporte aos resultados comerciais?
- OPS 4: Como você projeta sua carga de trabalho para entender o estado dela?
- OPS 5: Como você reduz defeitos, facilita a correção e melhora o fluxo na produção?
- OPS 6: Como você reduz os riscos de implantação?
- OPS 7: Como você sabe que está pronto para oferecer suporte a uma carga de trabalho?
- OPS 8: Como você compreende a integridade da sua carga de trabalho?
- OPS 9: Como você compreende a integridade de suas operações?
- OPS 10: Como você gerencia os eventos de carga de trabalho e operações?
- OPS 11: Como você evolui as operações?

### 6 Sustentabilidade

A sustentabilidade da nuvem permite que os clientes da AWS reduzam o uso de energia associado em quase 80% em relação a uma implantação local típica. isso é possível devido à utilização muito maior do servidor, eficiência de energia e refrigeração, design de data center personalizado e progresso contínuo no caminho para alimentar as operações da AWS com 100% de energia renovável até 2025.

#### 6 Princípios de design para sustentabilidade na nuvem

1. **Entenda seu impacto** : Avalie os resultados de negócios e o impacto de sustentabilidade relacionado para estabelecer indicadores de desempenho, avaliar melhorias e estimar o impacto das mudanças propostas ao longo do tempo.
2. **Estabeleça metas de sustentabilidade** : Estabeleça metas de longo prazo para cada carga de trabalho, modele o retorno sobre o investimento (ROI) e dê aos proprietários os recursos para investir em metas de sustentabilidade.
3. **Maximize a utilização** : Dimensione corretamente cada carga de trabalho para maximizar a eficiência energética do hardware subjacente e minimizar os recursos ociosos.
4. **Antecipe e adote novas ofertas de hardware e software mais eficientes** : Dê suporte a melhorias upstream feitas por seus parceiros, avalie continuamente as opções de hardware e software para eficiência e projete para flexibilidade para adotar novas tecnologias ao longo do tempo.
5. **Use serviços gerenciados** : Serviços compartilhados reduzem a quantidade de infraestrutura necessária para dar suporte a uma ampla variedade de cargas de trabalho.
6. **Reduza o impacto downstream de suas cargas de trabalho na nuvem** : Reduza a quantidade de energia ou recursos necessários para usar seus serviços e reduza a necessidade de seus clientes atualizarem seus dispositivos

#### Melhores práticas

1. **Otimize o posicionamento geográfico de cargas de trabalho para locais de usuários**
2. **Otimize áreas de código que consomem mais tempo ou recursos**
3. **Otimize o impacto nos dispositivos e equipamentos do cliente**
4. **Implementar uma política de classificação de dados**
5. **Use políticas de ciclo de vida para excluir dados desnecessários**
6. **Minimize a movimentação de dados entre redes**
7. **Otimize seu uso de GPUs**
8. **Adote métodos de desenvolvimento e teste que permitam a rápida introdução de potenciais melhorias de sustentabilidade**
9. **Aumente a utilização de seus ambientes de compilação** 

#### Considerações

## Well-Architected Tool

O AWS Well-Architected Tool foi projetado para ajudar você a revisar o estado de suas aplicações e workloads e proporciona um lugar central no qual podem ser reunidas práticas recomendadas e orientações.

### Preço

O AWS **Well-Architected Tool está disponível gratuitamente** no Console de Gerenciamento da AWS.

### Como funciona

#### Etapa 1: Definir carga de trabalho

As cargas de trabalho podem ser simples, como um site estático, ou complexas, como arquiteturas de microsserviços com vários armazenamentos de dados e muitos componentes.

#### Etapa 2: Conduzir uma revisão da arquitetura

Revise suas workloads com base nas práticas recomendadas da AWS respondendo a um conjunto de perguntas básicas, com a opção de criar as próprias lentes personalizadas.

#### Etapa 3: Aplicar práticas recomendadas

O AWS Well-Architected Tool fornece uma lista de problemas encontrados em suas workloads juntamente com orientações detalhadas para fazer melhorias.

### Acesso:

https://console.aws.amazon.com/wellarchitected/
