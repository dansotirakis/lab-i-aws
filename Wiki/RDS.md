# Amazon Relational Database Service

O Amazon Relational Database Service (Amazon RDS) é um serviço da web que facilita a configuração, a operação e escalabilidade de um banco de dados relacional na nuvem. Fornece capacidade econômica e redimensionável para um banco de dados relacional padrão do setor e gerencia tarefas comuns de administração de banco de dados.

O Amazon RDS **é um serviço de banco de dados gerenciado.** Ele é responsável pela maioria das tarefas de gerenciamento. Ao **eliminar tarefas manuais tediosas**, o Amazon RDS libera você para se concentrar na aplicação e nos usuários.

Recomenda-se o Amazon RDS no lugar do Amazon EC2 como opção padrão para a maioria das implantações de banco de dados.

## Vantagens específicas 

### Em relação às implantações de banco de dados que não são totalmente gerenciadas

- Você pode usar os produtos de banco de dados já conhecidos com: MySQL, MariaDB, PostgreSQL, Oracle, Microsoft SQL Server.
- O Amazon RDS gerencia backups, patches de software, detecção automática de falhas e recuperação.

- Você pode ativar backups automatizados ou pode criar manualmente seus próprios snapshots de backup.

- Você pode obter alta disponibilidade com uma instância primária e uma instância secundária síncrona que pode ser usada para failover em caso de problemas.

- Além da segurança no seu pacote de banco de dados, você pode ajudar a controlar quem pode acessar seus bancos de dados do RDS usando o AWS Identity and Access Management (IAM) para definir usuários e permissões.

## Amazon RDS Custom for Oracle e Microsoft SQL Server

Para o Oracle Database e o Microsoft SQL Server, o RDS Custom combina a automação do Amazon RDS com a flexibilidade do Amazon EC2.

| Recurso                                               | Gerenciamento do Amazon RDS | Gerenciamento do RDS Custom |
| :---------------------------------------------------- | :-------------------------- | :-------------------------- |
| Otimização de aplicações                              | Cliente                     | Cliente                     |
| Escalabilidade                                        | AWS                         | Compartilhado               |
| Alta disponibilidade                                  | AWS                         | Compartilhado               |
| Backups de banco de dados                             | AWS                         | Compartilhado               |
| Aplicação de patches de softwares para banco de dados | AWS                         | Compartilhado               |
| Instalação de softwares para banco de dados           | AWS                         | Compartilhado               |
| Aplicação de patches de sistema operacional           | AWS                         | Compartilhado               |
| Instalação do sistema operacional                     | AWS                         | Compartilhado               |
| Manutenção do servidor                                | AWS                         | AWS                         |
| Ciclo de vida do hardware                             | AWS                         | AWS                         |
| Energia, rede e desaquecimento                        | AWS                         | AWS                         |

Com o modelo de responsabilidade compartilhada do RDS Custom, você tem mais controle do que no Amazon RDS, mas também mais responsabilidades.

## Instâncias de banco de dados

- Uma instância de banco de dados é um ambiente isolado de banco de dados na Nuvem AWS. 
- Sua instância de banco de dados pode conter um ou mais bancos de dados criados pelo usuário. 
- É possível acessar a instância de banco de dados usando as mesmas ferramentas e os mesmos aplicativos usados com uma instância de banco de dados independente.

## Mecanismos de banco de dados

Um mecanismo de banco de dados é o software de banco de dados relacional específico que é executado na sua instância de banco de dados. Atualmente, o Amazon RDS oferece suporte aos seguintes mecanismos:

### MySQL

### MariaDB

### PostgreSQL

### Oracle

### Microsoft SQL Serverb 