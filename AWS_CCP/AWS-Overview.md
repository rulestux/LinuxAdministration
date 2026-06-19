# Computação em Nuvem

- É a entrega **sob demanda** \(on demand) de recursos de computação, banco de dados, armazenamento, aplicações ou qualquer outro recurso de tecnologia entregue por uma **plataforma** via internet, onde o pagamento e o preço são baseados em **consumo** \(pay as you go).


## Vantagens

### Mudança na modalidade gastos
- muda da modalidade de despesas de capital, [CAPEx](https://pt.wikipedia.org/wiki/CAPEX) ou despesa de aquisição de bens, para modelo de despesa variável, [OPEx](https://pt.wikipedia.org/wiki/OPEX) ou depesa operacional.

### Economia de escala
- com a computação em nuvem, você pode chegar a um custo variável menor do que seria possível por conta própria. Como o uso de centenas de milhares de clientes é agregado à nuvem, os provedores como a AWS têm redução de custos, através da alta escala de aquisição de hardware para a infraestrutura, o que se converte em um menor preço pago em função do uso.

### Capacidade
- você cresce ou diminui a capacidade necessária para atender às suas demandas, pagando apenas o que consumir.

### Agilidade e velocidade
- recursos estão disponíveis imediatamente; alta disponibilidade.

### Economia
- você deixa de gastar dinheiro para comprar e manter data centers.

### Global em poucos minutos
- permite que você tenha recursos disponíveis globalmente em poucos minutos, com baixa latência e custo, melhorando a experiência do cliente, através de Content Delivery Network \(CDN).


## Tipos de Cloud Computing

### IaaS - Infrastructure as a Service
	- contratante gerencia os servidores físicos ou virtuais;
	- contratante gerencia os sistemas operacionais e softwares adicionais;
	- o datacenter não tem responsabilidade com o que você faz com os recursos;

### PaaS - Platform as a Service
	- datacenter é responsável pelos recursos físicos ou virtuais, SOs, softwares e alguns itens de segurança;
	- contratante é responsável pela aplicação e sua configuração;
	
### SaaS - Software as a Service
	- toda a responsabilidade é do provedor, como no caso do Gmail, Office 365, Salesforce etc..


## Modelos de Implantação de Cloud Computing

### Public Cloud
	- AWS, Azure, Google Cloud;

### Private Cloud
	- datacenter próprio da empresa \(on-premises), como uma infraestrutura de TI antigam, com recursos dedicados privados;

### Hybrid Cloud
	- Combinação entre Public Cloud e Private Cloud \(on-premises);


# Infraestrutura Global da AWS

- a [infraestrutura global da AWS](https://aws.amazon.com/pt/about-aws/global-infrastructure) é uma plataforma de nuvem e oferece mais de 200 serviços completos de datacenter em todo o mundo.

## Regiões \(Regions)
- são as localidades físicas onde a AWS está disponível ao redor do mundo.

## Zonas de disponibilidades \(Availability Zone - AZ)
- é a quantidade de datacenters que a AWS tem em cada uma das regiões para prover serviços e produtos. No mínimo, são duas zonas de disponibilidade por região, a fim de proporcionar **alta disponibilidade**, **tolerância a falhas**, *desempenho*, *disaster recovery* e **escalabilidade**.

## Pontos de presença \(Edge Locations)
- uma *edge location* é basicamente um pequeno servidor de cache. Eles estão localizados na maioria das principais cidades do mundo e são usados especificamente pelo **CloudFront** \(CDN da AWS) para distribuir conteúdo ao usuário final e reduzir a latência do acesso.


# AWS Management Interfaces

## AWS Management Console
- interface gráfica com suporte para a maioria dos serviços da AWS. Pode ser usada via navegador ou aplicativo.


## AWS Command Line Interface - CLI
- acesso aos serviços via linha de comando. Facilidade, flexibilidade e precisão para uso de scripts de automação.

### AWS CloudShell
- funcionalidade que pode ser encontrada ao lado da barra de pesquisa no Console de gerenciamento da AWS, fornece um shell baseado em navegador que é pré-autenticado com as credenciais do console.


## Software Development Kit - SDK
- suporta diversas linguagens de programação e permite a incorporação de serviços AWS em aplicações.


# AWS Core Design Architecture

## AWS Well-Architected Framework

- [Well Architected Framework](https://aws.amazon.com/pt/architecture/well-architected) ajuda você a entender como projetar e operar sistemas confiáveis, seguros, eficientes e econômicos na nuvem AWS. Através de um conjunto de questões documentadas, ele fornece uma maneira de avaliar de forma consistente suas arquiteturas em relação às melhores práticas e identificar áreas para melhorias.

### 5 Pilares do AWS Well-Architected Framework

- **I - Excelência operacional \(Operational Excellence)**: se concentra em executar e monitorar sistemas para entregar valor empresarial e melhorar continuamente processos e procedimentos. Principais Serviços:

	- AWS Config:
		- proporciona um inventário de recursos da AWS, um histórico de configuração e notificações de alteração de configuração para possibilitar a segurança e a governança;
	- Amazon Cloudwatch:
		- fornece a você dados e insights acionáveis para monitorar aplicações, entender e reagir a alterações de performance em todo o sistema, otimizar a utilização de recursos e ter uma visualização unificada da integridade operacional;
	- AWS CloudFormation:
		- oferece aos desenvolvedores e administradores de sistemas uma maneira fácil de criar e gerenciar um conjunto de recursos relacionados na AWS, fornecendo provisionamento e atualização de uma forma organizada e previsível;

- **II - Segurança \(Security)**: se concentra em proteger informações e sistemas. Principais Serviços:

	- AWS Identity and Access Management \(IAM):
		- Gerencie com segurança as identidades e o acesso a serviços e recursos da AWS;
	- AWS CloudTrail: 
		- Acompanhe a atividade dos usuários e o uso da API na AWS e em ambientes híbridos e multinuvem;
	- AWS Web Application Firewall \(WAF):
		- Proteja suas aplicações da Web contra explorações comuns;
	- AWS Key Management Service \(KMS):
		- acilita a criação e o gerenciamento de chaves criptográficas e o controle de seu uso em uma ampla variedade de serviços AWS e em seus aplicativos;

- **III - Confiabilidade \(Reliability)**: se concentra em garantir que uma carga de trabalho execute sua função pretendida corretamente e de modo consistente quando esperado. Principais Serviços:

	- AWS CloudFormation;
	- Amazon Cloudwatch;
	- Amazon Simple Storage Service \(S3):
		- é um serviço de armazenamento de objetos que oferece escalabilidade líder do setor, disponibilidade de dados, segurança e performance;
	- Amazon Glacier;

- **IV - Eficiência de desempenho \(Performance Efficiency)**: se concentra no uso eficiente de recursos de TI e computação pelos clientes. Principais Serviços:
	
	- Amazon EC2 Auto Scaling:
		- ajuda você a manter a disponibilidade do aplicativo e permite que você adicione ou remova instâncias EC2 automaticamente, de acordo com as condições definidas por você;
	- Amazon Cloudwatch;
	- Amazon CloudFront:
		- fornece dados, vídeos, aplicativos e APIs para clientes em todo o mundo com baixa latência e altas velocidades de transferência, tudo em um ambiente amigável ao desenvolvedor;

- **V - Otimização de custos \(Cost Optimization)**: se concentra em evitar custos desnecessários. Principais Serviços:

	- Tag Resources;
	- AWS Cost Explorer: 
		- permite visualizar, entender e gerenciar seus custos e uso das soluções da AWS ao longo do tempo;


## Outros Serviços Relacionados ao AWS Core Design Architecture

### AWS Well-Architected Tool
- é a ferramenta que facilita a verificação da conformidade de uma arquitetura desenvolvida pelo contratante, através da metodologia de perguntas e respostas do Framework.

### AWS Trusted Advisor
- é um recurso on-line que auxilia na redução de custos, no aumento de performance e na *melhoria da segurança* por meio da otimização do seu ambiente da AWS. O Trusted Advisor fornece orientações em tempo real para auxiliar você no provisionamento de recursos com base nas práticas recomendadas da AWS. O número de métricas analisadas depende do nível de suporte contratado.


# AWS Core Services

## Computing Services

### EC2 - Elastic Compute Cloud
- *Amazon Elastic Compute Cloud \(Amazon EC2)* é um serviço web que fornece capacidade computacional segura e redimensionável na nuvem.

- **AMI - Amazon Machine Image** é a instância EC2. A AMI é definida por:

- quantidade e tipo de **CPU**;

- quantidade de **RAM**;

- tamanho e tipo de disco **EBS - Elastic Block Storage**;

- **modalidade** de custo:
	- *On-Demand*:
		- sob demanda; pay as you go; T2.micro -> Free Tier;

	- *Reserved Instance*:
		- reservada por 1 ou 3 anos, com até 75% de desconto, com pagamento à vista ou entrada mais restante mensal;

	- *Spot Request*:
		- leilão para uso de capacidade ociosa da AWS; o lance sendo aceito, a instância é provisionada;

	- *Dedicated Hosts*:
		- servidor físico dedicado pago por hora; descontos de até 70%;

- **Tipos de instância**: os tipos de instância EC2 são otimizados para tarefas diferentes;

| Tipos                          | Características                                                                                                                                           |
|:-------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Uso geral`                    | fornecem um equilíbrio de recursos de computação, memória e rede;                                                                                         |
| `Computação acelerada`         | usam aceleradores de hardware, ou coprocessadores, para executar algumas funções de forma mais eficiente do que é possível no software executado em CPUs; |
| `Otimizada para memória`       | são projetadas para fornecer rápida performance para cargas de trabalho que processam grandes conjuntos de dados na memória;                              |
| `Otimizada para computação`    | são ideais para aplicações vinculadas à computação que se beneficiam de processadores de alta performance;                                                |
| `Otimizada para armazenamento` | são projetadas para cargas de trabalho que exigem alto acesso sequencial de leitura e gravação a grandes conjuntos de dados no armazenamento local;       |


## Storage Services

### S3 - Simple Storage Service
- [S3](https://aws.amazon.com/pt/s3) é o principal serviço de armazenamento da AWS, permite armazenar e recuperar qualquer quantidade de informações via internet, pagando apenas pelo que usar;

- armazenamento de objetos:
	- cada objeto suportado até um máximo de **5TB de tamanho**;

- alta durabilidade 99.999999999%, disponibilidade 99.99% e escalabilidade;

- flexibilidade;

- segurança;

- baixo custo;

- ideal para objetos estáticos, sites e outros;

- provê **interface web** \(console);

- **acesso CLI e SDK**;

- **conceitos importantes**:

	- os objetos são armazenados em **buckets** \(baldes, algo semelhante a diretórios):
		- a definição da Região de armazenamento de um bucket é difinida na sua criação;
		- o nome do bucket deve:
			- ser único em todo o Amazon S3;
			- ter entre 3 e 63 caracteres;
			- estar sem caracteres maiúsculos;
			- começar com uma letra minúscula ou um número;

	- o nome dado ao objeto é sua **object key**;

	- possui **versionamento**, com custo adicional, e cada versão de um objeto recebe uma **version ID**;

	- o endereço \(URL) de um objeto é um **link address**:

		- ``` https://s3amazonaws.com/bucket-name/object-key.fileformat ```;

- **Storage Class**:

	- a classe de armazenamento é definida por:
		- **frequência de acesso** de seus objetos pelos usuários de uma aplicação;
		- **tempo de recuperação**;
		- **preço**;

	- classe **S3 Standard**:
		- padrão de armazenamento, para acesso frequente e imediato;
		- ideal para aplicações em nuvem, websites, games, big data, videos etc.;

	- classe **S3 Standard for infrequent access**:
		- *standard* para acesso não frequente, mas imediato;
		- menor custo;
		- ideal para backups, disaster recovery, dados de vida longa;

	- classe **One Zone for infrequent access**:
		- para acesso não frequente, mas imediato;
		- menor custo;
		- mantido em apenas **uma** Zona de Disponibilidade \(AZ);
		- usada para dados não críticos;

	- classe **Glacier**:
		- archiving;
		- acesso **não** frequente e **não** imediato;
		- alta durabilidade, disponibilidade e escalabilidade;
		- segurança;
		- menor custo;
		- ideal para objetos arquivados, backups, logs etc.;

	- classe **Reduced Redundancy**:
		- archiving;
		- acesso frequente e imediato;
		- baixa redundância;
		- usado para dados que podem ser novamente reproduzidos, como livros eletrônicos;

	- classe **Intelligent-Tiering**:
		- move automaticamente os objetos não usados para *infrequent access*;
		- acesso imediato, quando o objeto tiver em *infrequent access* ele é movido imediatamente para *standard*;
		- possui custo para a automação;
		- ideal para objetos cuja frequência de utilização não esteja clara;

- **Ciclo de Vida**:
	- S3 permite que ações de gerenciamento de ciclo de vida de objetos possam ser criadas a partir de regras;

- **Transition Actions**:
	- os objetos podem ser movidos entre classes de armazenamento após certo período, otimizando os custos de armazenamento a partir de regras;

- **Policies**:
	- as políticas de acesso a buckets e objetos são definidas em arquivos de políticas, definindo quem pode e quando pode acessá-los;

- **Criptografia**:
	- pode ser habilitada para armazenamento ou transmissão;

- **Cross-Region Replication**:
	- funcionalidade que permite a replicação de objetos entre buckets em diferentes regiões;
	- o versionamento precisa estar habilitado;
	- útil para backup, redução de latência e atendimento de requisitos legais;

- **Transfer Acceleration**:
	- funcionalidade para a transferência de grande volume de dados através de longas distâncias;
	- **Edge Locations** e **CloudFront** são utilizados para otimizar o processo;

### EBS - Elastic Block Storage
- o [EBS](https://aws.amazon.com/pt/ebs) é um tipo de **armazenamento em blocos**, persistente e customizável para instâncias EC2;
- possui *Snapshot*, que permite criar várias cópias do volume;
- alta disponibilidade e escalabilidade;
- segurança;
- permite habilitar encriptação \(Encryption on Rest);
- usado em instâncias *EC2*;

### EFS - Elastic File System
- o [EFS](https://aws.amazon.com/pt/efs) é um serviço de armazenamento que aumenta e diminui automaticamente conforme você adiciona e remove arquivos, sem a necessidade de gerenciamento ou provisionamento;
- alta disponibilidade e escalabilidade;
- segurança;
- baixo custo;
- usado para compartilhamento de arquivos entre instâncias *EC2* e entre essas e Data Centers On-Premises \(local) via *Direct Connect*;

### Storage Gateway
- armazenamento híbrido \(objeto ou bloco; local ou em nuvem);
- segurança;

### Snowball
- dispositivo físico para transferência de grandes volumes de dados locais para a nuvem AWS;
- capacidade de petabytes;
- criptografia;
- rastreamento;
- Amazon envia e coleta;

### Snowball Edge
- dispositivo físico para processamento de serviços como *EC2* e *Lambda*, permitindo utilização da nuvem AWS em locais sem acesso à Cloud e posterior sincronização;
- suporta 100TB
- segurança;
- gerenciamento;
- ideal para Navios, Fábricas, Desertos etc.;

### Snowmobile
- caminhão com container contendo um "mini datacenter móvel" da AWS que suporta até 100PB, para transferência de altíssimo volume de dados;
- criptografia;
- rastreamento;


## Network Services

### Virtual Private Cloud \(VPC)
- a [VPC](https://aws.amazon.com/pt/vpc) é uma Rede Privada isolada para os clientes da AWS, criada por padrão para cada conta AWS em cada Região, com configurações básicas e novas funcionalidades podem ser adicionadas;

- **subnets** são criadas para cada AZ e podem ser configuradas para terem acesso público ou privado;

- **Route Tables** controlam o tráfego das subnets;

- **Internet Gateway \(IGW)** permite que a rede VPC tenha acesso à internet;

- **NAT Gateway** permite que subnets tenham conexão com a internet, através de tradução de endereços;

- **Natwork Access Control List \(NACL)** controla o acesso a subnets;

- **Security Groups** controlam o acesso a instâncias EC2 e RDS, agindo como Firewall;

- novas redes \(redes não padrão) podem ser criadas e configuradas conforme a necessidade do cliente em cada Região;

- **Virtual Private Network - VPN**: a [VPN](https://aws.amazon.com/pt/vpn) é um serviço que estabelece conexões seguras entre redes locais, escritórios remotos, dispositivos de clientes e a rede global da AWS.


# AWS Integrated Services

## Database Services

### AWS DynamoDB
- o [DynamoDB](https://aws.amazon.com/pt/dynamodb) é um banco de dados **NoSQL**, sem servidor \(**serverless**) e **totalmente gerenciado**, projetado para executar aplicações de alto desempenho em qualquer escala \(**escalável**);

- **estrutura chave-valor** \(NoSQL);

- **arquitetura serverless**: não sendo necessário aprovisionar servidores;

- segurança: **controle de acesso** e **criptografia** de dados ociosos;

- monitoramento de uso: **métricas operacionais** com CloudWatch;

- custo: **Pay as you Go**;

- é **gerenciado**:
	- possui presença global, em diversas Regiões;
	- capacidade adaptável;
	- alta escalabilidade;
	- backup e recuperação sob demanda e point-in-time;
	- TTL que permite definir a vida útil do dado;

- **DAX - DynamoDB Accelerator**: recurso de cache de memória gerenciado e altamente disponível, que otimiza o tempo de resposta;

- **Índices**: índices secundários para flexibilização de consultas;

- **Uso Local**: permite desenvolver e testar localmente;

- **Trigger**: executa código *Lambda* automaticamente, baseado numa condição;

- **Streams**: permite criar sequências quando alterações acontecem nas tabelas do DynamoDB;

- **acessibilidade**: AWS Console, AWS CLI, AWS SDK;

### AWS RDS - Relational Database Service
- o [RDS](https://aws.amazon.com/pt/rds) é um serviço de banco de dados relacional gerenciado, escalável e de alta disponibilidade; o RDS oferece seis mecanismos de bancos de dados comuns, incluindo **Amazon Aurora**, PostgreSQL, MySQL, MariaDB, Oracle Database e SQL Server;
	- configurável via AWS Console, CLI ou SDK;
	- atualização patching automática, gerenciada pela AWS;
	- recomandações de melhores práticas \(tamanho da instância, storage e rede);
	- alta performance com discos GEneral Purpose SSD e Provisioned IOPS SSD;
	- alta escalabilidade \(Compute, Storage e **Read Replicas**);
	- alta disponibilidade \(Backups Automáticos, Snapshots e **Multi-AZ Deployments**);
	- Seguro com dados criptografados em storage e em trânsito;
	- isolamento de rede;
	- monitoramento \(Eeventos e Métricas);

- **Read Replicas**:
- recurso relacionado a *performance, desempenho e redução de latência*, consistindo em um Snapshot do DB atualizado de forma síncrona entre diferentes Zonas de Disponibilidade e Regiões, comportando-se como CDN;

- **Multi-AZ Deployments**:
- recurso relacionado a Disaster Ricover, mantendo réplicas constantemente sincronizadas em mais de uma Zona de Disponibilidade; o redirecionamento de acesso é automático, quando for necessário, apontando para uma segunda instância entre 60-120 segundos;

- **Amazon Aurora**:
- o [Aurora](https://aws.amazon.com/pt/rds/aurora) é um banco de dados relacional desenvolvido e gerenciado pela AWS, compatível com MySQL e PostgreSQL; o Aurora é até cinco vezes mais rápido que bancos de dados MySQL padrão e três vezes mais rápido que bancos de dados PostgreSQL padrão;

- características:
	- armazenamento distribuído;
	- tolerante a falhas e com recuperação automática;
	- replicação entre três zonas de disponibilidade;

### AWS Redshift
- o [Redshift](https://aws.amazon.com/pt/redshift) é um banco de dados colunar \(column-oriented) da AWS, de alta escalabilidade, baixa latência, processamento massivo e paralelo, e armazenamento em escala, para o processamento de dados; simples de usar, custo efetivo para utilização em **Data Warehouse** e **Data Lakes**;

- características:
	- fácil implementação e configuração;
	- Pay As You Go;
	- Escalabilidade em Petabytes e leituras no S3 em Exabytes;
	- Integra-se com ferramentas de terceiros;

### Neptune
- o [Neptune](https://aws.amazon.com/pt/neptune) é um serviço de banco de dados gráfico rápido, confiável e totalmente gerenciado que facilita a criação e a execução de aplicativos;

### Database Migration Service - DMS
- o [DMS](https://aws.amazon.com/pt/dms) é um serviço que permite migrar bancos de dados relacionais, bancos de dados não relacionais e outros tipos de armazenamentos de dados; o banco de dados de origem permanece totalmente operacional
durante a migração, minimizando o tempo de inatividade de aplicações que dependem do banco de dados;


## Computing Services

### AWS Lambda
- o [Lambda](https://aws.amazon.com/pt/lambda) é um serviço de computação sem servidor \(serverless) e orientado a eventos que permite executar código para praticamente qualquer tipo de aplicação ou serviço de backend sem provisionar ou gerenciar servidores;

- **Lambda functions** é um microsserviço \(código) que roda na plataforma do AWS Lambda baseado em eventos, em um conceito conhecido como **Function as Service - FaaS**;

- a *programação orientada a eventos* segue o padrão:

	- evento \(trigger) -> função -> ação;

- linguagens suportadas:
	- NodeJS;
	- Python;
	- Java;
	- C#;
	- Ruby;
	- Go;

### Elastic Load Balancing - ELB
- o [ELB](https://aws.amazon.com/pt/elasticloadbalancing) é um serviço que distribui automaticamente o tráfego de aplicações de entrada entre vários destinos e dispositivos virtuais em uma ou mais zonas de disponibilidade (AZ);

- *Classic Load Balancing*: distribui entre instâncias EC2;

- *Network Load Balancing*: distribui o tráfego através da camada 4 \(TCP/UDP) através de instâncias EC2 e contêineres;

- *Application Load Balancing*: distribui o tráfego através da camada 7 \(protocolos de aplicação), através de instâncias EC2, contêineres e lambdas;

### Auto Scaling
- o [Auto Scaling](https://aws.amazon.com/pt/autoscaling) é um serviço que monitora os aplicativos e ajusta automaticamente a capacidade para manter um desempenho constante e previsível pelo menor custo possível, em instâncias pré-configuradas, usando tráfego ou processamento \(CPU) como critério de gatilho;

### Elastic Beanstalk
- o [Elastic Beanstalk](https://aws.amazon.com/pt/elasticBeanstalk) é um serviço que permite a implantação de aplicações apenas fornecendo o código-fonte, sem conhecimento ou definição prévia da infraestrutura; trata-se de um serviço **PaaS - Platform as a Service**;

- suporta aplicações em Go, Java, .NET, PHP, Python e Ruby;
- monitoração com CloudWatch e X-Ray;
- escalabilidade automática;
- recursos personalizados;


## Management Services

### AWS CloudTrail
- o [CloudTrail](https://aws.amazon.com/pt/cloudtrail) é um serviço de segurança que monitora, registra e retém todas as atividades e ações realizadas em uma conta AWS na infraestrutura e serviços AWS; ele registra **quem** fez **o que**, em **qual recurso** e **quando**; é usado principalmente para auxílio a governança, auditoria, segurança, análise de riscos e outros;

### AWS CloudWatch
- o [CloudWatch](https://aws.amazon.com/pt/cloudwatch) é um serviço de monitoramento de recursos integrado da AWS que permite coleta, monitoração, análise e ação sobre os comportamentos dos recursos da AWS; Ele coleta dados de monitoramento e operações na forma de logs, métricas e eventos;

### AWS X-Ray
- o X-Ray é um serviço que facilita a análise de *comportamento* e *rastreamento* completo de Aplicações Distribuídas \(em microsserviços);

- *instrumentação* em Aplicativos usados no EC2, ECS, Lambda e Beanstalk.

### AWS Config
- o [Config](https://aws.amazon.com/pt/config) é um serviço que permite acessar, auditar e avaliar as configurações dos recursos da AWS; o Config monitora e grava continuamente registros das configurações de recursos da AWS e lhe permite automatizar a avaliação das configurações registradas com base nas configurações desejadas;

- disponibiliza regras para avaliação de recursos, seja através de **Regras Gerenciadas**, criadas e mantidas pela AWS, ou através de **Regra Personalizadas** feitas pelo cliente;

- as configurações ficam salvas em histórico, de forma a permitir recuperação dessas configurações após alguma alteração;

### Amazon Simple Notification Service
- o [Amazon SNS](https://aws.amazon.com/pt/sns) é um serviço de notificação totalmente gerenciado, altamente disponível, seguro e durável, que permite o desacoplamento de microsserviços, sistemas distribuídos e aplicativos sem servidor;


## Network Services

### AWS CloudFront
- o [CloudFront](https://aws.amazon.com/pt/cloudfront) é um serviço de rede de entrega de conteúdo (CDN) criado para alta performance, segurança e conveniência do desenvolvedor.


## Development Tools

### AWS Cloud9
- o Cloud9 é um serviço de IDE acessível via browser que permite desenvolvimento colaborativo integrado com o AWS CLI, facilitando o desenvolvimento serverless-lambda e suportando 40 linguagens de programação;

### AWS CodeCommit
- o CodeCommit é um serviço de repositório baseado em GIT, com repositórios ilimitados e integrado com AWS CLI e AWS SDK;

### AWS CodeBuild
- o CodeBuild é um serviço de Integração Contínua \(CI) totalmente gerenciado e extensível, permitindo o uso de ferramentas externas à AWS; pay-as-you-go; permite monitoramento pelo AWS CloudWatch

### AWS CodeDeploy
- o CodeDeploy é um serviço de implementação automática de aplicações, integrado com as demais ferramentas da AWS;

### AWS CodePipeline
- o CodePipeline é um serviço de Entrega Contínua \(CD), feito uma esteira ou workflow para inserção de tarefas do ciclo de desenvolvimento, integrado com as demais ferramentas da AWS e com diversos plugins para as principais soluções do mercado;

### AWS CodeStar
- o CodeStar é um serviço que permite acessar outros serviços num mesmo ambiente; inclui serviços como Cloud9, CodeCommit, CodeBuild e CodeDeploy ofertados pré-configurados;


## Security Services

### AWS Rekognition
- o Rekognition é um serviço de API que faz análise de imagens e vídeos utilizando Machine Learning e retornando informações categorizadas e classificadas;






