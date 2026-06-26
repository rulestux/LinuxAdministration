# Computação em Nuvem

- é a entrega **sob demanda** \(on demand) de recursos de computação, banco de dados, armazenamento, aplicações ou qualquer outro recurso de tecnologia entregue por uma **plataforma** via internet, onde o pagamento e o preço são baseados em **consumo** \(pay as you go).


## Vantagens
- as 6 Vantagens Oficiais da Nuvem:

### Mudança na modalidade gastos
- muda da modalidade de despesas de capital, [CapEx](https://pt.wikipedia.org/wiki/CAPEX) ou despesa de aquisição de bens \(**despesa de capital**), para modelo de despesa variável, [OpEx](https://pt.wikipedia.org/wiki/OPEX) ou **depesa operacional**.

[Gemini](https://gemini.google.com/) comments:
- **CAPEX \(Capital Expenditure):** Dinheiro gasto adiantado em ativos físicos (comprar servidores, construir datacenters). Prende capital e gera custos de depreciação.
- **OPEX \(Operational Expenditure):** Despesas operacionais cotidianas. Na nuvem, você paga apenas pelo que consome, transformando um custo fixo previsível/alto em um custo variável escalável.

- *Conceitos Importantes para Fixar (Padrão NIST)*:
	- **On-demand self-service \(Autoatendimento sob demanda):** O usuário provisiona recursos sozinho, via console/API, sem precisar solicitar a um atendente.
	- **Measured Service \(Serviço mensurado):** Sistemas de nuvem controlam e otimizam o uso de recursos automaticamente, fornecendo relatórios precisos do que foi consumido (transparência de custos).

### Economia de escala massiva
- com a computação em nuvem, você pode chegar a um custo variável menor do que seria possível por conta própria \(Benefit from massive economies of scale); 

- como o uso de centenas de milhares de clientes é agregado à nuvem, os provedores como a AWS têm redução de custos, através da alta escala de aquisição de hardware para a infraestrutura, o que se converte em um menor preço pago em função do uso;

### Capacidade
- você cresce ou diminui a capacidade necessária para atender às suas demandas, pagando apenas o que consumir;

### Agilidade e velocidade
- recursos estão disponíveis imediatamente; alta disponibilidade;

### Economia
- você deixa de gastar dinheiro para comprar e manter data centers;

### Global em poucos minutos
- permite que você tenha recursos disponíveis globalmente em poucos minutos, com baixa latência e custo, melhorando a experiência do cliente, através de Content Delivery Network \(CDN);


## Tipos de Cloud Computing

### IaaS - Infrastructure as a Service
- o Provedor de Nuvem gerencia os servidores físicos ou virtuais;
- o contratante gerencia os sistemas operacionais e softwares adicionais;
- o Provedor de Nuvem não tem responsabilidade com o que você faz com os recursos;
- **Exemplo na AWS:** **Amazon EC2**, Amazon EBS, Amazon VPC;

### PaaS - Platform as a Service
- o provedor é responsável pelos recursos físicos ou virtuais, SOs, softwares e alguns itens de segurança;
- o contratante é responsável pela aplicação e sua configuração;
- **Exemplo na AWS:** **AWS Elastic Beanstalk**, Amazon RDS;

### SaaS - Software as a Service
- toda a responsabilidade é do provedor;
- **Exemplos comuns:** Gmail, Microsoft Office 365, Salesforce;


## Modelos de Implantação de Cloud Computing

### Public Cloud
- os recursos de computação (como servidores e armazenamento) pertencem e são operados por um provedor terceirizado (como a AWS) e entregues pela internet.
- AWS, Azure, Google Cloud;

### Private Cloud
- datacenter próprio da empresa \(on-premises. on-prem, private cloud ou infraestrutura local), como uma infraestrutura de TI antiga, com recursos dedicados privados;

### Hybrid Cloud
- Combinação entre Public Cloud e Private Cloud \(on-premises);
- serviços AWS para nuvem híbrida:
	- **AWS Outposts:** hardware físico da AWS instalado dentro do datacenter local do cliente para rodar serviços da AWS de forma nativa e local;
	- **AWS Direct Connect:** conexão de rede física direta dedicada entre a infraestrutura local e as instalações da AWS, contornando a internet pública;
	- **AWS Storage Gateway:** integração de armazenamento híbrido, permitindo que servidores locais usem o Amazon S3 com segurança;

## Modelo de Responsabilidade Compartilhada (Shared Responsibility Model)
- **responsabilidade DA nuvem \(Segurança DA Nuvem - AWS):** a AWS protege a infraestrutura global que executa todos os serviços oferecidos;
    - **o que engloba:** segurança física dos datacenters, instalações, hardware \(servidores, discos), software de virtualização \(hypervisors) e a rede física das Regiões e Zonas de Disponibilidade \(AZs);

- **Responsabilidade NA nuvem \(Segurança NA Nuvem - Cliente):** o cliente é responsável por como configura e utiliza os recursos provisionados;
    - **O que engloba:** dados do cliente, gerenciamento de identidades e acessos \(IAM), configuração de firewalls \(Security Groups e NACLs), criptografia de dados \(em repouso e em trânsito) e o gerenciamento/patches do Sistema Operacional \(em serviços IaaS como instâncias EC2);


---------------------------------------------------------------------

# Infraestrutura Global da AWS

- a [infraestrutura global da AWS](https://aws.amazon.com/pt/about-aws/global-infrastructure) é uma plataforma de nuvem e oferece mais de 200 serviços completos de datacenter em todo o mundo;

## Regiões \(Regions)
- são as localidades físicas, totalmente isoladas e independentes umas das outras, onde a AWS está disponível ao redor do mundo;

- *Critérios para escolha de uma Região:*
  1. **Conformidade/Legislação \(Compliance):** atender a requisitos legais de retenção de dados no país de origem \(ex: LGPD no Brasil, GDPR na Europa);
  2. **Proximidade \(Latência):** reduzir o tempo de resposta de rede para os usuários finais;
  3. **Custo:** os preços dos serviços variam de acordo com a Região devido a impostos e infraestrutura local \(ex: a Região de São Paulo é historicamente mais cara que a de Virgínia do Norte devido a impostos locais);
  4. **Disponibilidade de Serviços:** verificar se o serviço desejado já está homologado naquela região;

## Zonas de Disponibilidades \(Availability Zone - AZ)
- consiste em **um ou mais datacenters discretos** que a AWS tem, com energia, refrigeração e segurança física redundantes dentro de uma mesma Região, para prover serviços e produtos, ; no mínimo, são duas zonas de disponibilidade por região, a fim de proporcionar **alta disponibilidade**, **tolerância a falhas**, *desempenho*, *disaster recovery* e **escalabilidade**.

- por padrão, cada Região possui no mínimo 3 AZs, focando em resiliência tripla, com raras exceções históricas com 2;

- **Conectividade:** as AZs de uma mesma região são interconectadas por redes de fibra óptica privadas, de altíssima velocidade e baixa latência;

## Pontos de Presença \(Edge Locations)
- uma **edge location** é basicamente uma infraestrutura de computadores/servidores de tamanho menor localizados nas principais metrópoles do mundo, fora das Regiões centrais, funcionando como um pequeno servidor de cache; 

- eles estão localizados na maioria das principais cidades do mundo e são usados especificamente pelo **Amazon CloudFront** \(CDN da AWS) para distribuir conteúdo ao usuário final e reduzir a latência do acesso a conteúdos estáticos e dinâmicos \(vídeos, imagens, arquivos);

- **Regional Edge Caches:** Uma camada intermediária de cache localizada entre as Edge Locations e as Regiões, usada para armazenar conteúdos de acesso menos frequente.


---------------------------------------------------------------------

# AWS Management Interfaces

## AWS Management Console
- interface gráfica com suporte para a maioria dos serviços da AWS; pode ser usada via navegador ou aplicativo;
- é ideal para iniciantes, atividades visuais, testes rápidos, visualização de custos e tarefas não automatizada;
- **Autenticação:** usuário, senha e MFA \(Múltiplo Fator de Autenticação);


## AWS Command Line Interface - CLI
- acesso aos serviços via linha de comando; 
- facilidade, flexibilidade e precisão ideais para uso de scripts de automação; requer instalação local;
- **Autenticação:** utiliza **Chaves de Acesso** \(Access Key ID e Secret Access Key);

### AWS CloudShell
- funcionalidade que pode ser encontrada ao lado da barra de pesquisa no console de gerenciamento da AWS, fornece um shell baseado em navegador que é pré-autenticado com as credenciais do console;
- apresenta a AWS CLI e outras ferramentas \(como Git, Python, etc.) já instaladas de fábrica;


## Software Development Kit - SDK
- conjunto de bibliotecas e ferramentas de desenvolvimento para integrar serviços da AWS diretamente no código-fonte; suporta diversas linguagens de programação e permite a incorporação de serviços AWS em aplicações;
- **Autenticação:** utiliza **Chaves de Acesso** embutidas de forma segura no ambiente da aplicação;


---------------------------------------------------------------------

# AWS Core Design Architecture

## AWS Well-Architected Framework

- [Well Architected Framework](https://aws.amazon.com/pt/architecture/well-architected) ajuda você a entender como projetar e operar sistemas confiáveis, seguros, eficientes e econômicos na nuvem AWS; através de um conjunto de questões documentadas, ele fornece uma maneira de avaliar de forma consistente suas arquiteturas em relação às melhores práticas e identificar áreas para melhorias;

### 5 Pilares do AWS Well-Architected Framework

- **I - Excelência operacional \(Operational Excellence)**: se concentra em executar e monitorar sistemas para entregar valor empresarial e melhorar continuamente processos e procedimentos; palavras-chave: "Executar a infraestrutura como código \(IaC)" e "Evoluir procedimentos com frequência"; Principais Serviços:

	- **AWS CloudFormation**:
		- oferece aos desenvolvedores e administradores de sistemas uma maneira fácil de criar e gerenciar um conjunto de recursos relacionados na AWS, fornecendo provisionamento e atualização de uma forma organizada e previsível; é o campeão desse pilar por permitir tratar infraestrutura como código \(IaC);
	- **AWS Config**:
		- proporciona um inventário de recursos da AWS, um histórico de configuração e notificações de alteração de configuração para possibilitar a segurança e a governança;
	- **Amazon Cloudwatch**:
		- fornece a você dados e insights acionáveis para monitorar aplicações, entender e reagir a alterações de performance em todo o sistema, otimizar a utilização de recursos e ter uma visualização unificada da integridade operacional;

- **II - Segurança \(Security)**: se concentra em proteger informações e sistemas; Principais Serviços:

	- AWS Identity and Access Management \(IAM):
		- gerencie com segurança as identidades e o acesso a serviços e recursos da AWS;
	- AWS CloudTrail: 
		- acompanhe a atividade dos usuários e o uso da API na AWS e em ambientes híbridos e multinuvem;
		- lembrar: o CloudTrail audita quem fez o quê \(chamadas de API/histórico de ações); o CloudWatch monitora performance e métricas \(uso de CPU, logs de aplicação);
	- AWS Web Application Firewall \(WAF) e AWS Network Firewall:
		- proteja suas aplicações da Web contra explorações comuns;
	- AWS Shield:
		- proteção contra ataques DDoS;

	- AWS Key Management Service \(KMS):
		- facilita a criação e o gerenciamento de chaves criptográficas e o controle de seu uso em uma ampla variedade de serviços AWS e em seus aplicativos;
	- AWS Artifact: 
		- serviço gratuito onde você baixa os relatórios de conformidade da AWS \(como ISO, PCI, SOC) para provar a auditores que a nuvem é segura;

	- AWS Inspector:
		- análise de vulnerabilidades;
	- AWS GuardDuty:
		- monitoramento de ameaças baseado em Machine Learning;
	- AWS Cognito:
		- gestão de acesso para aplicativos móveis integrada com Facebook, AWS, Active Directory etc.;
	- Security Groups:
		- firewall para instâncias EC2 e RDS, incluído na VPC da AWS;
	- Network ACL \(NACL):
		- controle de acesso à rede baseado em regras;

- **III - Confiabilidade \(Reliability)**: se concentra em garantir que uma carga de trabalho execute sua função pretendida corretamente e de modo consistente quando esperado; foco em Alta Disponibilidade e Redundância; Principais Serviços:

	- AWS CloudFormation;
	- Amazon Cloudwatch;
	- Amazon Simple Storage Service \(S3):
		- é um serviço de armazenamento de objetos que oferece escalabilidade líder do setor, disponibilidade de dados, segurança e performance;
	- Amazon S3 Glacier;
	- Amazon Route 53;
	- Elastic Load Balancing \(ELB);
	- AWS Backup;

- **IV - Eficiência de desempenho \(Performance Efficiency)**: se concentra no uso eficiente de recursos de TI e computação pelos clientes; palavras-chave: "Selecionar os recursos certos com base na carga de trabalho"; Principais Serviços:
	
	- Amazon EC2 Auto Scaling:
		- ajuda você a manter a disponibilidade do aplicativo e permite que você adicione ou remova instâncias EC2 automaticamente, de acordo com as condições definidas por você;
	- Amazon Cloudwatch;
	- Amazon CloudFront:
		- fornece dados, vídeos, aplicativos e APIs para clientes em todo o mundo com baixa latência e altas velocidades de transferência, tudo em um ambiente amigável ao desenvolvedor;
	- AWS Lambda;

- **V - Otimização de custos \(Cost Optimization)**: se concentra em evitar custos desnecessários. Principais Serviços:

	- Tag Resources;
	- AWS Cost Explorer: 
		- permite visualizar, entender e gerenciar seus custos e uso das soluções da AWS ao longo do tempo;

- **VI - Sustentabilidade (Sustainability)**: concentra-se em minimizar os impactos ambientais da execução de cargas de trabalho na nuvem;
	- *Conceito-chave:* entender o impacto compartilhado \(a AWS otimiza os datacenters e o cliente otimiza o código/arquitetura), maximizar a utilização dos servidores para reduzir o consumo de energia por unidade de trabalho;
	- *Recomendações:* escolher tipos de instâncias eficientes \(como processadores AWS Graviton) ou usar arquiteturas serverless para reduzir o desperdício de recursos ligados sem uso;


## Outros Serviços Relacionados ao AWS Core Design Architecture

### AWS Well-Architected Tool
- é a ferramenta que facilita a verificação da conformidade de uma arquitetura desenvolvida pelo contratante, através da metodologia de perguntas e respostas do Framework;

- é um questionário conceitual guiado pelo cliente da AWS; o cliente entra nela e responde perguntas sobre os processos da sua equipe para que a ferramenta gere um relatório de riscos de design;

### AWS Trusted Advisor
- é um recurso on-line que auxilia na redução de custos, no aumento de performance e na *melhoria da segurança* por meio da otimização do seu ambiente da AWS; 
- o Trusted Advisor fornece orientações em tempo real para auxiliar você no provisionamento de recursos com base nas práticas recomendadas da AWS; 
- o número de métricas analisadas depende do nível de suporte contratado;
- é um scanner automatizado que varre a conta AWS de forma programática atrás de coisas mal configuradas no código da infraestrutura \(ex: volumes de disco soltos e sem uso);

- 5 pilares/categorias de inspeção do Trusted Advisor:

	- Otimização de Custos \(Cost Optimization):
		- identifica recursos ociosos \(como instâncias EC2 subutilizadas) para economizar dinheiro;

	- Desempenho \(Performance);
		- sugere melhorias de throughput e configurações de rede;
		
	- Segurança \(Security);
		- avalia permissões perigosas \(como buckets S3 públicos por engano) e configurações de firewall expostas;

	- Tolerância a Falhas \(Fault Tolerance);
		- verifica se os backups estão ativos e se há redundância de AZs configurada;

	- Limites de Serviço \(Service Limits): 
		- avisa quando você está prestes a estourar o teto padrão de recursos da conta \(como limite de instâncias EC2 rodando em uma região); 
		- monitora o uso da sua conta em relação aos limites padrão impostos pela AWS para evitar travamentos operacionais;

- **Regra de Suporte:** contas com suporte *Basic* ou *Developer* têm acesso a regras limitadas de segurança e limites de serviço; o acesso completo a todas as verificações exige suporte técnico nível *Business* ou *Enterprise*:

	- Nível Gratuito (Basic/Developer Support): dá acesso limitado, cobrindo apenas verificações básicas de segurança (como portas abertas de Security Groups ou falta de MFA na conta raiz) e os limites de serviço;

	- Nível Completo (Business/Enterprise Support): desbloqueia o monitoramento completo com todas as centenas de regras automatizadas de infraestrutura em tempo real;


## Frameworks de Adoção e Migração para Nuvem

### AWS Cloud Adoption Framework \(AWS CAF)
- o CAF ajuda as organizações a criarem um plano abrangente para a transformação digital na nuvem através de **6 Perspectivas** fundamentais divididas em dois blocos:

 	- **Perspectivas de Negócios \(Foco em capacidades de negócios e pessoas):**
		- I. *Business \(Negócios):* alinhamento da TI com as estratégias e resultados de negócios;
		- II. *People \(Pessoas):* evolução da cultura, competências e liderança para a nuvem;
		- III. *Governance \(Governança):* gerenciamento e medição de investimentos em nuvem para maximizar o valor;
	- **Perspectivas Técnicas \(Foco em capacidades tecnológicas e de engenharia):**
		- IV. *Platform \(Plataforma):* arquitetura de ambientes de nuvem e padrões de infraestrutura;
		- V. *Security \(Segurança):* garantia de conformidade, visibilidade e controle de riscos na nuvem;
		- VI. *Operations \(Operações):* saúde, monitoramento e entrega de serviços de TI em escala de nuvem;

### Estratégias de Migração \(os 7 R's)
- quando uma empresa decide migrar sua infraestrutura local \(on-premises) para a AWS, cada aplicação deve seguir uma destas estratégias:

	- **I. Rehost \(Lift-and-Shift):** mover a aplicação para a nuvem exatamente como ela está, sem modificações \(ex: migrar uma VM local diretamente para o EC2); rápido, mas não otimizado;
	- **II. Relocate \(Hypervisor-Level Shift):** mover cargas de trabalho baseadas em virtualização local \(geralmente VMware) diretamente para uma solução de nuvem compatível \(como *VMware Cloud on AWS*), sem precisar alterar configurações operacionais ou converter o formato das VMs;
	- **III. Replatform \(Lift-Tinker-and-Shift):** mover para a nuvem fazendo pequenas otimizações para aproveitar recursos gerenciados, sem alterar o código principal \(ex: mover um banco de dados local para o Amazon RDS);
	- **IV. Refactor / Re-architect \(Rearquitetar):** modificar o código ou arquitetura para torná-la nativa da nuvem \(ex: transformar uma aplicação monolítica em microsserviços usando AWS Lambda);
	- **V. Repurchase \(Recomprar):** mudar para um produto ou modelo comercial diferente, geralmente migrando para um SaaS \(ex: abandonar um CRM local e assinar o Salesforce);
	- **VI. Retain \(Reter):** manter a aplicação rodando no ambiente local \(on-premises) por enquanto, seja por razões de conformidade ou porque passou por uma migração recente;
	- **VII. Retire \(Aposentar):** identificar e desativar aplicações que não são mais úteis ou necessárias para o negócio;


---------------------------------------------------------------------

# AWS Core Services

## Computing Services

### EC2 - Elastic Compute Cloud
- *Amazon Elastic Compute Cloud \(Amazon EC2)* é um serviço web que fornece capacidade computacional \(servidores virtuais chamados "Instâncias") segura e redimensionável na nuvem;

- **AMI - Amazon Machine Image** é o template de inicialização \(gabarito) para instâncias EC2; uma AMI contém o Sistema Operacional \(Linux, Windows), configurações de inicialização e softwares/aplicações pré-instalados;

- tipos de instâncias determinam o hardware físico do computador host usado para a sua instância \(CPU, RAM, Armazenamento e Capacidade de Rede); são otimizados para diferentes cenários por:

- quantidade e tipo de **CPU**;

- quantidade de **RAM**;

- tamanho e tipo de disco **EBS - Elastic Block Storage**;

- **modalidade** de custo \(EC2 Purchasing Options):
	- *On-Demand*:
		- sob demanda; pay as you go; T2.micro -> Free Tier;
		- ideal para **aplicações de curto prazo**, cargas de trabalho imprevisíveis ou sistemas que estão sendo testados pela primeira vez e não podem ser interrompidos.

	- *Reserved Instance*:
		- reservada por 1 ou 3 anos, com até 72% de desconto, com pagamento à vista ou entrada mais restante mensal;
		- ideal para **cargas de trabalho previsíveis** e de estado estacionário (steady-state) que rodam continuamente;

	- *Savings Plans*:
		- oferece os mesmos descontos das RIs \(até 72%), mas o cliente se compromete com um **valor de consumo por hora** \(ex: \$10/hora) por 1 ou 3 anos;
		- é muito mais flexível que a RI porque o desconto se aplica automaticamente mesmo se o cliente mudar o tamanho da instância, região, ou migrar do EC2 para AWS Lambda e AWS Fargate;

	- *Spot Request*:
		- permite arrematar a capacidade computacional ociosa da AWS com até 90% de desconto; a AWS pode recuperar a instância com um aviso prévio de apenas **2 minutos** se precisar da capacidade de volta; o lance sendo aceito, a instância é provisionada;
		- ideal para cargas de trabalho **tolerantes a falhas e interrupções** \(processamento em lote, filas de background, renderização de imagens);

	- *Dedicated Hosts*:
		- servidor físico totalmente dedicado pago por hora; descontos de até 70%;
		- dá controle total sobre os sockets e cores físicos; usado estritamente por motivos de **conformidade regulatória rígida** ou para reaproveitar licenças de software corporativas existentes vinculadas ao hardware (modelo **BYOL - Bring Your Own License**);

- **Tipos de instância**: os tipos de instância EC2 são otimizados para tarefas diferente:

- `Uso geral`
	- fornecem um equilíbrio de recursos de computação, memória e rede;
	- usado em servidores web básicos, servidores de desenvolvimento e testes;

- `Otimizada para computação`
	- são ideais para aplicações vinculadas à computação que se beneficiam de processadores de alta performance; foco em processamento;
	- usado em servidores de jogos, codificação de vídeo, modelagem científica;

- `Computação acelerada`
	- usam aceleradores de hardware \(GPUs), ou coprocessadores, para executar algumas funções de forma mais eficiente do que é possível no software executado em CPUs; 
	- usado em treinamento de Inteligência Artificial (LLMs), Machine Learning, gráficos 3D;

- `Otimizada para memória`
	- são projetadas para fornecer rápida performance para cargas de trabalho que processam grandes conjuntos de dados na memória;
	- usado em bancos de dados relacionais de alta performance, caches em memória \(ElastiCache);

- `Otimizada para armazenamento`
	- são projetadas para cargas de trabalho que exigem alto acesso sequencial de leitura e gravação a grandes conjuntos de dados no armazenamento local;
	- usado em sistemas de Big Data, Data Warehousing, sistemas de arquivos distribuídos;


## Storage Services

### S3 - Simple Storage Service
- [S3](https://aws.amazon.com/pt/s3) é o principal serviço de armazenamento da AWS, permite armazenar e recuperar qualquer quantidade de informações via internet, pagando apenas pelo que usar;

- armazenamento de objetos:
	- cada objeto suportado até um máximo de **5TB de tamanho**;

- armazenamento infinito via internet \(API), não é montado nativamente como um sistema de arquivos local do SO;

- alta durabilidade 99.999999999%, disponibilidade 99.99% e escalabilidade;

- flexibilidade;

- segurança: aplica criptografia do lado do servidor \(SSE-S3) automaticamente como padrão para todos os novos objetos, sem custo adicional e sem precisar que você configure manualmente;

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

		- ``` https://bucket-name.s3.amazonaws.com/object-key ```;

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

	- classe **S3 Glacier**:
		- archiving;
		- acesso **não** frequente e **não** imediato;
		- alta durabilidade, disponibilidade e escalabilidade;
		- segurança;
		- menor custo;
		- ideal para objetos arquivados, backups, logs etc.;

	- classe **Intelligent-Tiering**:
		- move automaticamente os objetos não usados para *infrequent access*;
		- acesso imediato, quando o objeto tiver em *infrequent access* ele é movido imediatamente para *standard*;
		- possui custo para a automação;
		- não cobra taxa de recuperação \(diferente das classes IA);
		- ideal para objetos cuja frequência de utilização não esteja clara;

- **Ciclo de Vida**:
	- S3 permite que ações de gerenciamento de ciclo de vida de objetos possam ser criadas a partir de regras de tempo \(ex: após 30 dias):
	- **Transition Actions**:
		- os objetos podem ser movidos entre classes de armazenamento após certo período, otimizando os custos de armazenamento a partir de regras;
	- **Expiration Actions**:
		- servem para deletar objetos permanentemente após 'X' dias \(muito usado para apagar logs antigos de auditoria);

- **Versionamento \(Versioning)**:
 	- mantém múltiplas variantes de um objeto no mesmo bucket; permite recuperar arquivos deletados por engano ou sobrescritos; *gera custos adicionais pois cada versão conta como armazenamento*;

- **Políticas de Acesso (Policies)**:
	- **Bucket Policies:** regras em formato JSON anexadas diretamente ao bucket para autorizar/negar acessos em massa \(ex: tornar uma pasta do bucket pública para a internet);
	- **S3 Block Public Access:** trava de segurança global que impede que qualquer bucket seja exposto publicamente, mesmo se houver erro em uma Bucket Policy;

- **Criptografia**:
	- por padrão, todos os novos buckets e uploads de objetos no S3 são criptografados automaticamente do lado do servidor \(Server-Side Encryption);

- **Cross-Region Replication**:
	- funcionalidade que permite a replicação de objetos entre buckets em diferentes regiões;
	- o versionamento precisa estar habilitado;
	- útil para backup, redução de latência e atendimento de requisitos legais;

- **S3 Transfer Acceleration**:
	- funcionalidade para a transferência de grande volume de dados através de longas distâncias;
	- **Edge Locations** e **CloudFront** são utilizados para otimizar o processo;

### EBS - Elastic Block Storage
- o [EBS](https://aws.amazon.com/pt/ebs) é um tipo de **armazenamento em blocos**, persistente e customizável para instâncias EC2;
- possui *Snapshot*, que permite criar várias cópias do volume;
- alta disponibilidade e escalabilidade;
- segurança;
- permite habilitar encriptação \(Encryption at Rest);
- usado em instâncias *EC2*;

- um volume EBS padrão só pode ser anexado a uma única instância EC2 por vez \(com raras exceções de volumes específicos chamados Multi-Attach, mas a regra geral de prova é 1 para 1) e eles devem estar na mesma Zona de Disponibilidade \(AZ) da instância; equivale a um DAS;

- **tipos**:
	- SSD \(Solid State Drives): focado em performance de IOPS (operações de leitura/escrita por segundo); ideal para Bancos de dados e volumes de boot do Sistema Operacional; tipos comuns: gp3, io2;
	- HDD \(Hard Disk Drives): focado em throughput \(taxa de transferência de dados em MB/s); ideal para Big Data, Log-streaming e cargas de trabalho sequenciais de baixo custo onde a velocidade de IOPS não é crítica; tipos comuns: st1, sc1;

### EFS - Elastic File System
- o [EFS](https://aws.amazon.com/pt/efs) é um serviço de armazenamento que aumenta e diminui automaticamente conforme você adiciona e remove arquivos, sem a necessidade de gerenciamento ou provisionamento;
- alta disponibilidade e escalabilidade;
- segurança;
- baixo custo;
- usado para compartilhamento de arquivos entre instâncias *EC2* e entre essas e Data Centers On-Premises \(local) via *Direct Connect*;

- pode ser montado e compartilhado por centenas de instâncias EC2 simultaneamente, inclusive distribuídas em múltiplas AZs; equivale a um NAS;

### Storage Gateway
- armazenamento híbrido \(objeto ou bloco; local ou em nuvem);
- segurança;

- tipos de arquitetura que ele assume na ponta \(On-premises):
	- File Gateway: expõe um compartilhamento de arquivos local \(NFS/SMB) que salva os arquivos diretamente como objetos no Amazon S3;
	- Volume Gateway: expõe volumes de bloco locais \(iSCSI) para seus servidores locais e tira snapshots assíncronos deles para o EBS na nuvem;
	- Tape Gateway: substitui fitas magnéticas físicas de backup locais \(VTL) por armazenamento virtual seguro no S3 Glacier;

### AWS Snow Family
- dispositivos físicos e blindados enviados pela AWS via correio para cenários com conectividade de internet limitada ou inexistente;
- Migração de Dados e Computação de Borda
- capacidade de petabytes;
- criptografia;
- rastreamento;
- Amazon envia e coleta;

### AWS Snowcone
- o menor e mais leve dispositivo da família \(ultra-portátil, pesa ~2 kg);
- suporta armazenamento de até 14 TB e possui recursos básicos de computação local; usado para ambientes táticos e remotos;

### AWS Snowball Edge
- dispositivo físico para processamento de serviços como *EC2* e *Lambda*, permitindo utilização da nuvem AWS em locais sem acesso à Cloud e posterior sincronização;
- segurança;
- gerenciamento;

- **Snowball Edge Storage Optimized** suporta 100TB; ideal para transferência de dados em massa \(até 80/100 TB) de servidores locais para o S3;
- **Snowball Edge Compute Optimized** fornece forte capacidade de computação local \(incluindo instâncias EC2 e funções AWS Lambda locais) para locais isolados \(*Edge Computing*) como navios, fábricas ou áreas de desastre, permitindo processar os dados localmente e sincronizar com a AWS mais tarde;

### Snowmobile \(serviço descontinuado)


## Network Services

### Virtual Private Cloud \(VPC)
- a [VPC](https://aws.amazon.com/pt/vpc) é uma Rede Privada isolada para os clientes da AWS, criada por padrão para cada conta AWS em cada Região, com configurações básicas e novas funcionalidades podem ser adicionadas;

- **subnets** são criadas para cada AZ e podem ser configuradas para terem acesso público ou privado;

	- um VPC para cada Região e uma Subnet para cada AZ;

- **Route Tables** conjunto de regras \(rotas) que determinam para onde o tráfego de rede das sub-redes ou gateways deve ser direcionado; controlam o tráfego das subnets;

- **Internet Gateway \(IGW)** componente redundante e altamente disponível que permite que a rede VPC tenha acesso à internet;

- **NAT Gateway** permite que subnets tenham conexão com a internet, através de tradução de endereços;

- **VPC Peering** é uma conexão de rede que permite rotear o tráfego diretamente entre duas VPCs \(da sua conta ou de contas terceiras) usando endereços IP privados, fazendo com que elas se comuniquem como se estivessem na mesma rede; não é transitivo \(se A conecta com B, e B com C, A não fala com C automaticamente);

- **Security Groups** 
	- atuam como firewall virtual para as **Instâncias EC2** \(nível de host);
	- **Stateful \(Com estado)**: se uma regra de entrada \(Inbound) for permitida, o tráfego de retorno na saída \(Outbound) é liberado automaticamente;
	- Suporta apenas regras de **Permissão** \(Allow).

- **Natwork Access Control List \(NACL)** controla o acesso a subnets;
	- atua como um firewall de borda para as **Sub-redes** \(nível de subnet); camada adicional de segurança;
	- **Stateless (Sem estado):** as regras de entrada e saída são isoladas; se permitir a entrada, deve configurar explicitamente a permissão de saída;
	- suporta regras de **Permissão (Allow)** e **Negação (Deny)**; avaliado em ordem numérica;
	- novas redes \(redes não padrão) podem ser criadas e configuradas conforme a necessidade do cliente em cada Região;

### AWS Site-to-Site VPN
-  a [VPN](https://aws.amazon.com/pt/vpn) é um serviço que estabelece conexões seguras entre redes locais, escritórios remotos, dispositivos de clientes e a rede global da AWS;

- estabelece um túnel criptografado seguro \(IPsec) entre a rede local da sua empresa \(On-premises) e a VPC da AWS **através da internet pública**; é rápido de implantar e econômico, mas sujeito às oscilações da internet;

### AWS Direct Connect
- o [Direct Connect](https://aws.amazon.com/pt/directconnect/) é o serviço de rede que estabelece uma conexão de rede física dedicada e exclusiva entre o datacenter local da sua empresa e a AWS, **contornando totalmente a internet**;

- fornece **largura de banda** consistente, **latência ultra-baixa e estável**, e segurança de rede máxima para migrações massivas ou ambientes de missão crítica;

---------------------------------------------------------------------

# AWS Integrated Services

## Database Services

### AWS DynamoDB
- o [DynamoDB](https://aws.amazon.com/pt/dynamodb) é um banco de dados **NoSQL**, sem servidor \(**serverless**) e **totalmente gerenciado**, projetado para executar aplicações de alto desempenho em qualquer escala \(**escalável**);

- **estrutura chave-valor** \(NoSQL) e documentos JSON;

- **arquitetura serverless**: não sendo necessário aprovisionar servidores;

- segurança: **controle de acesso** e **criptografia** de dados ociosos;

- monitoramento de uso: **métricas operacionais** com CloudWatch;

- custo: **Pay as you Go**; pode ser configurado em modo *On-Demand* \(paga por leitura/escrita exata) ou *Provisioned* \(você define o limite de processamento para ganhar previsibilidade de custo);

- é **gerenciado**:
	- possui presença global, em diversas Regiões;
	- capacidade adaptável;
	- alta escalabilidade;
	- backup e recuperação sob demanda e point-in-time;
	- TTL que permite definir a vida útil do dado \(ideal para limpar sessões de usuários ou logs antigos);

- **DAX - DynamoDB Accelerator**: recurso de cache de memória gerenciado e altamente disponível, que otimiza o tempo de resposta de milissegundos para **microssegundos**; ideal para tabelas com altíssima intensidade de leitura \(ex: catálogo de produtos de um e-commerce na Black Friday);

- **DynamoDB Global Tables \(Tabelas Globais)**: funcionalidade que replica suas tabelas de forma automática, assíncrona e bidirecional entre **múltiplas Regiões da AWS**; garante que usuários globais acessem os dados com latência local e provê excelente resiliência de Disaster Recovery;

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
- recurso relacionado a *performance, desempenho e redução de latência*, consistindo em um Snapshot do DB atualizado de forma assíncrona \(**replicação assíncrona**) entre diferentes Zonas de Disponibilidade e Regiões, comportando-se como servidores adicionais de consulta \(somente leitura) que podem estar na mesma AZ, em outra AZ ou em outra Região.;

- **Multi-AZ Deployments**:
- recurso relacionado a Disaster Ricover, mantendo réplicas constantemente sincronizadas \(**replicação síncrona**) em mais de uma Zona de Disponibilidade; o redirecionamento de acesso é automático, quando for necessário, apontando para uma segunda instância entre 60-120 segundos;

- **caso de uso**: por que uma empresa escolheria o RDS em vez de instalar o MySQL dentro de uma instância EC2?

	- se escolher EC2: o cliente é responsável por patches do S.O., backups manuais, configurar cluster de alta disponibilidade e escaneamento do disco local \(Nível do S.O. para cima);

	-s e escolher RDS \(Gerenciado): a AWS cuida do provisionamento do hardware, aplicação de patches do S.O. e do motor do banco, além de backups automatizados; o cliente não tem acesso ao sistema operacional \(SSH) em uma instância RDS tradicional;

### Amazon Aurora
- o [Aurora](https://aws.amazon.com/pt/rds/aurora) é um banco de dados relacional desenvolvido e gerenciado pela AWS, compatível com MySQL e PostgreSQL; o Aurora é até cinco vezes mais rápido que bancos de dados MySQL padrão e três vezes mais rápido que bancos de dados PostgreSQL padrão;

- características:
	- armazenamento distribuído;
	- tolerante a falhas e com recuperação automática;
	- replica os dados de forma síncrona em 3 Zonas de Disponibilidade, mas armazena 2 cópias dos dados em cada AZ, totalizando 6 cópias dos seus dados;

### Amazon Redshift
- o [Redshift](https://aws.amazon.com/pt/redshift) é um banco de dados colunar \(column-oriented) da AWS, de alta escalabilidade, baixa latência, processamento massivo e paralelo, e armazenamento em escala, para o processamento de dados; simples de usar, custo efetivo para utilização em **Data Warehouse** e **Data Lakes**;

- características:
	- fácil implementação e configuração;
	- Pay As You Go;
	- Escalabilidade em Petabytes e leituras no S3 em Exabytes;
	- Integra-se com ferramentas de terceiros;

### Amazon Neptune
- o [Neptune](https://aws.amazon.com/pt/neptune) é um serviço de banco de dados gráfico rápido \(baseado em grafos), confiável e totalmente gerenciado que facilita a criação e a execução de aplicativos; 

- usado em Redes sociais \(mapear conexões de amigos), motores de recomendação ou sistemas de detecção de fraude financeira \(rastrear caminhos de transações);

### Database Migration Service - DMS
- o [DMS](https://aws.amazon.com/pt/dms) é um serviço que permite migrar bancos de dados relacionais, bancos de dados não relacionais e outros tipos de armazenamentos de dados; o banco de dados de origem permanece totalmente operacional durante a migração, minimizando o tempo de inatividade de aplicações que dependem do banco de dados;

### Amazon ElastiCache
- o [ElastiCache](https://aws.amazon.com/pt/elasticache/) é um serviço de armazenamento de dados **em memória \(In-memory cache)** totalmente gerenciado, compatível com Redis e Memcached;
- usado para **melhorar a latência e o desempenho de leitura** de aplicações, aliviando a carga de bancos de dados relacionais (RDS) ao armazenar em cache os resultados das consultas mais frequentes na memória RAM;

### Amazon Athena
- o Athena é um serviço de consulta interativo e **Serverless** \(sem servidor) que permite analisar dados diretamente no Amazon S3 usando **SQL padrão**;
- você aponta o Athena para o seu bucket do S3 onde estão armazenados os arquivos \(como CSV, JSON, Apache Parquet ou logs), escreve uma consulta SQL comum e ele exibe o resultado em segundos;
- **Usecases**:
	- cenários onde a equipe de TI precisa analisar e filtrar grandes volumes de logs de segurança \(como logs do **CloudTrail** ou **VPC Flow Logs**) armazenados no S3;
	- extrair informações de arquivos de dados sem a necessidade de criar, gerenciar ou pagar por um banco de dados relacional \(RDS) ou data warehouse \(Redshift);
- você não paga pelo serviço parado; a cobrança é feita exclusivamente **por terabyte de dados escaneados** durante a execução das suas consultas SQL;

### Amazon QuickSight
- o QuickSight é um serviço de **Business Intelligence (BI)** totalmente gerenciado, rápido e em escala de nuvem \(é o "Power BI / Tableau" da AWS);
- ele se conecta a diversas fontes de dados da AWS \(como Amazon S3, Athena, RDS, Redshift) ou locais \(arquivos Excel, bancos de dados on-premises) para extrair informações e transformá-las em recursos visuais;
- **Usecases**:
	- **Dashboards e Relatórios:** cenários em que a empresa precisa criar **painéis interativos e gráficos visuais** para que executivos e equipes de negócios analisem dados e tomem decisões estratégicas;
	- **QuickSight Q**: recurso baseado em Machine Learning que permite aos usuários fazer perguntas complexas sobre os dados usando **linguagem natural** \(frases comuns) e receber respostas visuais imediatas;
- **Vantagem Arquitetural**: totalmente **Serverless** e de fácil compartilhamento, permitindo embutir os gráficos criados dentro de portais ou aplicativos da própria empresa;

### Amazon OpenSearch Service
- o OpenSearch é um serviço gerenciado que facilita a implantação, operação e escalabilidade de ferramentas de **busca de texto, análise de logs e monitoramento de infraestrutura em tempo real** \(Sucessor do *Amazon Elasticsearch Service*);
- ele ingere dados estruturados e não-estruturados em altíssima velocidade, indexa esses dados e permite que você realize pesquisas complexas quase instantaneamente;
- **Usecases**:
	- para cenários onde um aplicativo precisa de uma barra de ferramentas para **pesquisa de texto avançada e rápida** \(ex: busca em catálogo de produtos);
	- **Análise de Logs em Tempo Real**: para equipes de segurança e infraestrutura que precisam analisar logs operacionais de servidores e redes continuamente para identificar falhas ou ataques no exato momento em que acontecem;
- **Visualização Integrada**: inclui o *OpenSearch Dashboards* \(evolução do Kibana), permitindo criar gráficos e painéis interativos para monitorar a saúde dos sistemas em tempo real;

### Amazon CloudSearch
- o CloudSearch um serviço totalmente gerenciado na nuvem da AWS que facilita a configuração, o gerenciamento e a escalabilidade de um **mecanismo de busca personalizado** para sites ou aplicativos;
- **Recursos Nativos**: suporta funcionalidades clássicas de barras de pesquisa, como realce de sintaxe \(*highlighting*), preenchimento automático \(*autocomplete*), busca facetada \(filtros por categoria) e correções tipográficas;
- **Usecases**:
	- para cenários que exigem a implantação de uma **solução de busca simples, rápida e com o menor esforço operacional possível**, sem que o desenvolvedor precise entender de administração de clusters ou servidores de busca complexos;


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

- o Lambda cobra baseado no número de solicitações \(requisições) e na duração \(o tempo que o código leva para executar, medido em milissegundos), combinado com a quantidade de memória RAM alocada para a função; se o código não está rodando \(esperando um evento), o custo é rigorosamente ZERO;

- uma função Lambda tem um tempo máximo de execução de 15 minutos; se o processamento demorar mais que isso, o Lambda não serve \(precisa usar EC2 ou containers);

### AWS Elastic Load Balancing - ELB
- o [ELB](https://aws.amazon.com/pt/elasticloadbalancing) é um serviço que distribui automaticamente o tráfego de aplicações de entrada entre vários destinos e dispositivos virtuais em uma ou mais zonas de disponibilidade (AZ);

- *Classic Load Balancing*: **descontinuado**;

- *Application Load Balancing \(ALB)*: distribui o tráfego através da camada 7 \(protocolos de aplicação), com roteamento inteligente baseado no conteúdo da requisição HTTP/HTTPS através de instâncias EC2, contêineres e lambdas;

- *Network Load Balancing \(NLB)*: distribui o tráfego pela camada 4 \(TCP/UDP) através de instâncias EC2 e contêineres; ultra-alta performance, latência extremamente baixa e capacidade de lidar com milhões de requisições por segundo;

- *Gateway Load Balancer \(GWLB)*: opera na Camada 3 (Rede) e é usado especificamente para implantar, dimensionar e gerenciar appliances virtuais de terceiros \(como Firewalls de rede de fornecedores como Palo Alto, CheckPoint, ou sistemas de detecção de intrusão - IDS/IPS); *caso de uso*: inserir um appliance de firewall de terceiros ou inspeção profunda de pacotes antes do tráfego chegar à aplicação;

### Auto Scaling
- o [Auto Scaling](https://aws.amazon.com/pt/autoscaling) é um serviço que monitora os aplicativos e ajusta automaticamente a capacidade para manter um desempenho constante e previsível pelo menor custo possível, em instâncias pré-configuradas, usando tráfego ou processamento \(CPU) como critério de gatilho;

### AWS Elastic Beanstalk
- o [Elastic Beanstalk](https://aws.amazon.com/pt/elasticBeanstalk) é um serviço que permite a implantação de aplicações apenas fornecendo o código-fonte, sem conhecimento ou definição prévia da infraestrutura; trata-se de um serviço **PaaS - Platform as a Service**;

- serviço gratuito \(paga apenas pelos recursos subjacentes - instâncias EC2, buckets S3, instâncias RDS - que ele cria para rodar o código);

- *caso de uso*: um desenvolvedor quer implantar uma aplicação web rapidamente na AWS, não quer se preocupar com o provisionamento da infraestrutura subjacente, mas deseja manter o controle total sobre os recursos caso precise ajustar o sistema operacional ou o servidor web mais tarde;

- suporta aplicações em Go, Java, .NET, PHP, Python e Ruby;
- monitoração com CloudWatch e X-Ray;
- escalabilidade automática;
- recursos personalizados;

### Amazon EventBridge
- o EventBridge é um barramento de eventos \(*Event Bus*) totalmente gerenciado e **Serverless** que facilita a construção de aplicações orientadas a eventos em escala;
- ele recebe eventos de fontes emissoras \(serviços AWS, aplicações próprias ou sistemas SaaS de terceiros) e aplica **Regras (Rules)** para rotear esses dados para alvos específicos \(como AWS Lambda, SQS, SNS ou instâncias EC2).

- **Usecases**:
	- **Ações Agendadas (Cron na Nuvem):** permite programar a execução de tarefas automáticas em horários ou intervalos de tempo fixos \(ex: disparar um script Lambda de limpeza de logs toda madrugada);
	- **Reação a Eventos de Infraestrutura:** monitora mudanças de estado de recursos AWS em tempo real \(ex: disparar um alerta se uma instância EC2 parar inesperadamente);

- ele substitui e expande o antigo serviço conhecido como *Amazon CloudWatch Events*;


## Observability and Management Services

### AWS CloudTrail
- o [CloudTrail](https://aws.amazon.com/pt/cloudtrail) é um serviço de segurança que monitora, registra e retém todas as atividades e ações realizadas em uma conta AWS na infraestrutura e serviços AWS; ele registra em logs **quem** fez **o que**, em **qual recurso** e **quando**; é usado principalmente para auxílio a governança, auditoria, segurança, análise de riscos e outros;

### AWS Config
- o [Config](https://aws.amazon.com/pt/config) é um serviço que permite acessar, auditar e avaliar as configurações dos recursos da AWS; o Config monitora e grava continuamente registros das configurações de recursos da AWS e lhe permite automatizar a avaliação das configurações registradas com base nas configurações desejadas;

- disponibiliza regras para avaliação de recursos, seja através de **Regras Gerenciadas**, criadas e mantidas pela AWS, ou através de **Regra Personalizadas** feitas pelo cliente;

- as configurações ficam salvas em histórico, de forma a permitir recuperação dessas configurações após alguma alteração;

- enquanto o CloudTrail registra oum evento de alteração \(ex: "o usuário X rodou o comando para alterar o Security Group"), o AWS Config registra o impacto físico daquela alteração no recurso ao longo do tempo \(ex: "o Security Group X mudou do estado 'Seguro' para o estado 'Inseguro' porque a porta 22 foi aberta para o mundo"); o Config permite ver uma linha do tempo de alterações de hardware e regras;

### AWS CloudWatch
- o [CloudWatch](https://aws.amazon.com/pt/cloudwatch) é um serviço de monitoramento de recursos integrado da AWS que permite coleta, monitoração, análise e ação sobre os comportamentos dos recursos da AWS; ele coleta dados de monitoramento e operações na forma de logs, métricas e eventos, visando a "saúde" e a performance das aplicações hospedadas;

### AWS X-Ray
- o X-Ray é um serviço que facilita a análise de *comportamento* e *rastreamento* completo de Aplicações Distribuídas \(em microsserviços);

- seu uso consiste em Depurar \(Debug) ou Rastrear \(Trace) gargalos de performance em arquiteturas de Microsserviços ou aplicações distribuídas;

- *instrumentação* em Aplicativos usados no EC2, ECS, Lambda e Beanstalk.

### AWS CloudFormation
- o [CloudFormation](https://aws.amazon.com/pt/cloudformation) é um serviço que permite descrever e modelar toda a infraestrutura na AWS utilizando um arquivo de texto ou linguagem de programação;

- serviço 100% gratuito; você não paga nada para criar ou gerenciar suas Stacks; você paga única e exclusivamente pelos recursos de infraestrutura \(EC2, RDS, volumes EBS) que o template criar;

- **Características**:
	- infraestrutura como código \(IaC - Infrastructure as Code)(versionamento);
	- fonte única e confiável para concentrar todos os recursos;
	- permite automação;
	- suporta formato JSON ou YAML;
	- o arquivo de texto \(JSON/YAML) é o Template \(gabarito), e quando a AWS lê esse template e provisiona os recursos reais na nuvem, o conjunto desses recursos gerados é chamado de Stack \(Pilha);


## App Integration

### Amazon Simple Notification Service - SNS
- o [SNS](https://aws.amazon.com/pt/sns) é um serviço de notificação totalmente gerenciado, altamente disponível, seguro e durável, que permite o desacoplamento de microsserviços, sistemas distribuídos e aplicativos sem servidor;

- Funcionamento no Modelo Push/Pub-Sub: funciona no estilo Publish/Subscribe \(Publicador/Assinante); um serviço publica uma mensagem em um Tópico e o SNS empurra \(push) essa mesma mensagem instantaneamente para múltiplos assinantes de uma vez \(como funções Lambda, filas SQS, URLs HTTP ou e-mails); é uma comunicação de um para muitos.

- use SNS se precisar enviar notificações operacionais automatizadas rápidas ou alertas de infraestrutura \(ex: acoplado a um alarme do CloudWatch);

- **características**:
	- criptografia de mensagens;
	- filtro de mensagens;
	- notificações mobile;
	- configuração de privacidade de mensagens;

### Amazon Simple Queue Service - SQS
- o [SQS](https://aws.amazon.com/pt/sqs) é um serviço de filas de mensagens \(mensageria) gerenciado que permite o desacoplamento e a
escalabilidade de microsserviços, sistemas distribuídos e aplicações sem servidor;

- Funcionamento no Modelo Pull/Fila: funciona no estilo baseado em Fila \(Queue); um serviço envia a mensagem para a fila e ela fica lá guardada; o componente receptor precisa ir até a fila e puxar \(pull/polling) a mensagem para processá-la; é uma comunicação de um para um \(uma mensagem na fila geralmente é processada por apenas um consumidor por vez);

- **características**:
	- filas e mensagens ilimitadas;
	- retenha as mensagens nas filas por até 14 dias;
	- envie e releia as mensagens simultaneamente;
	- bloqueio de mensagens;
	- compartilhamento de filas;
	- criptografia no lado do servidor;

### Amazon Simple E-mail Service - SES
- o [SES](https://aws.amazon.com/pt/ses/) é o serviço que provê envio e recebimento de e-mails em alta escala com custo efetivo;

- **usecases**:
	- *e-mail marketing*: envio de e-mail para grande base de clientes para promoção de produtos, propaganda, ofertas especiais etc.;

	- *e-mail transacional*: envio de e-mail automatizado como confirmação de pedidos, entrega, status de pedido, mudança de políticas, reset de senhas etc.;

	- *notificações*: erros em sistemas ou produtos, monitoramento, mudança de status de processos etc.;

	- *recebimento*: receber e-mails em massa e tomada de decisão \(automação);

- use SES se precisar de uma plataforma de e-mail profissional de alta escala voltada para o negócio \(ex: e-mail marketing, newsletters corporativas ou automação de marketing transacional);

### Amazon API Gateway
- **O que é:** Um serviço totalmente gerenciado que facilita para os desenvolvedores a criação, publicação, manutenção, monitoramento e proteção de APIs em qualquer escala.
- **Como funciona:** Atua como a "porta de entrada" \(Front Door) pública para que aplicações externas acessem dados, lógicas de negócios ou funcionalidades de seus serviços de backend hospedados na AWS.
- **Usecases:**
  - **Arquitetura Serverless Principal:** Ideal quando associado ao **AWS Lambda** para expor microsserviços na internet sem a necessidade de provisionar ou gerenciar servidores web tradicionais \(como Nginx ou Apache).
  - **Segurança e Controle de Tráfego \(Throttling):** Protege o backend contra picos de acessos e ataques limitando a taxa de requisições por segundo por usuário \(*Rate Limiting*). Integra-se nativamente com o *Amazon Cognito* para autenticação de usuários.
  - **Gerenciamento de Versões:** Permite rodar e gerenciar simultaneamente múltiplas versões da mesma API \(ex: Produção, Homologação, Desenvolvimento).
- **Escala:** Totalmente Serverless. Escala de forma automática de centenas a milhões de chamadas de API simultâneas com baixa latência.


## Network Services

### Amazon CloudFront
- o [CloudFront](https://aws.amazon.com/pt/cloudfront) é um serviço de rede de entrega de conteúdo (CDN) criado para alta performance, segurança e conveniência do desenvolvedor; funciona através da rede global de centenas de datacenters menores, as **Edge Locations**;
- oferece proteção nativa contra ataques DDoS em conjunto com o AWS Shield;

### Amazon Route53
- o [Route53](https://aws.amazon.com/pt/route53) é um serviço DNS altamente disponível e escalável;

- **características**:
	- oferece serviços de registro de nome de domínio;
	- é possível obter DNS recursivo para o Amazon VPC e as redes on-premises;
	- regras de firewall que filtram o tráfego de DNS de saída em relação a essas regras;
	- gerenciamento de tráfego global;

- **principais políticas de roteamento**:
	- **Simple Routing**: direciona o tráfego para um único recurso padrão \(ex: um IP de um servidor);
	- **Latency Routing:** encaminha o usuário para a Região AWS que entregar a menor latência de rede para ele;
	- **Failover Routing:** roteia o tráfego para um site de backup em caso de falha do ambiente principal \(Disaster Recovery);
	- **Geolocation Routing:** exibe conteúdo ou direciona para servidores específicos com base na localização geográfica do IP do cliente \(país ou continente);


## Development Tools

### AWS Cloud9 \(Descontinuado)

### AWS CodeStar \(Descontinuado)

### AWS CodeCommit \(Descontinuado)

### AWS CodeBuild
- o [CodeBuild](https://aws.amazon.com/pt/codebuild/) é um serviço de Integração Contínua \(CI) totalmente gerenciado e extensível, permitindo o uso de ferramentas externas à AWS; pay-as-you-go; permite monitoramento pelo AWS CloudWatch; compila o código-fonte, roda testes automatizados e gera pacotes prontos para implantação \(artefatos);

### AWS CodeDeploy
- o [CodeDeploy](https://aws.amazon.com/pt/codedeploy/) é um serviço de implementação automática de aplicações, integrado com as demais ferramentas da AWS; instala o pacote gerado automaticamente nas instâncias EC2, containers \(ECS) ou AWS Lambda; evita o trabalho manual de atualizar servidor por servidor;

### AWS CodePipeline
- o [CodePipeline](https://aws.amazon.com/pt/codepipeline/) é um serviço de Entrega Contínua \(CD), feito uma esteira ou workflow para inserção de tarefas do ciclo de desenvolvimento, integrado com as demais ferramentas da AWS e com diversos plugins para as principais soluções do mercado; não compila e não instala nada sozinho, mas gerencia o fluxo visual e liga o CodeBuild ao CodeDeploy automaticamente sempre que há uma mudança no código;


## Security Services

### AWS Identity and Access Management - IAM
- o [IAM](https://aws.amazon.com/pt/iam) é um serviço que controla o acesso aos recursos na AWS; ele permite criar e controlar usuário, autenticação ou limitar acesso de usuário a recursos; 

- o IAM controlar **quem \(Autenticação)** pode fazer **o que \(Autorização: permissões)** na sua conta AWS;

- **users**:
	- pessoa ou serviço que interage com a AWS Cloud;
	- nome único;
	- pode ter um conjunto de cerdenciais:
		- senha do Console da AWS;
		- Access Key \(Acesso via CLI ou SDK);
		- MFA - Multi Factor Authentication \(Software, Hardware, SMS);
	- tem que estar associado a apenas uma conta da AWS;
	- permite acesso de forma humana ou programada \(via API ou CLI(;

- **groups**:
	- agrupamento de usuários por departamentos, funções ou afinidades etc.;
	- usuários compartilham as mesmas permissões \(policies);
	- facilitam o gerenciamento de usuários;

- **policies**:
	- definem **quem** tem acesso **ao que**, **o que** e **quando** pode fazer;
	- são descritas em formato JSON;
	- por padrão não dão acesso a coisa alguma;
	- podem ser assinaladas para Users, Groups e Roles;
	- definem em detalhes as ações que podem ser executadas;
	- podem ser **managed policies** \(criadas e mantidas pela AWS) ou **inline policies** \(criadas pelos clientes);

- **roles**:
	- função/papel que interage com recursos da AWS sem a necessidade de criar um user;
	- usa Policies;
	- não possui credenciais;
	- chaves de acesso são criadas dinamicamente;
	- usuários, aplicações e serviços podem assumir IAM Roles;

### Amazon Inspector
- o [Inspector](https://aws.amazon.com/pt/inspector) é um serviço de avaliação de segurança automático que ajuda a melhorar a segurança e a conformidade dos aplicativos implementados na AWS com máquinas EC2; o Amazon Inspector avalia automaticamente aplicativos em busca de exposições, vulnerabilidades ou discrepâncias em relação às melhores práticas; analisa conforme padrões de complience e segurança;

- administrado através de:
	- console;
	- CLI;
	- SDK;
	- API;

### AWS Shield
- o [Shield](https://aws.amazon.com/pt/shield) é um serviço gerenciado de proteção contra DDoS que protege os aplicativos executados na AWS;

- **AWS Shield Standrd**:
	- disponível para todos os clientes da AWS sem custos adicionais;
	- protege contra ataques mais comuns;
	- protege as camadas de transporte e rede;
	- pode ser usado com o Amazon Route53 e o Amazon CloudFront, para aumentar o nível de segurança;

- **AWS Shield Advanced**:
	- com custo adicional, oferece alto nível de proteção contr ataques web no CloudFront, Route53, EC2, Elastic Load Balancing, Elastic IP;
	- protege contra ataques massivos de alta escala e grande volume de eventos;
	- configura Network ACLs durante ataque para evitar parada do serviço e utilização em excesso de recursos como capacidade da rede;
	- permite proteção customizada;
	- protege contra custos de DDoS, ou seja, quando o custo dos recursos atingidos aumentar, como caso o ELB aumentar, a AWS devolve como créditos ao cliente;
	- permite contactar o **DDoS Response Team \(DRT)**, que trabalha em plantão 24x7, para obter assistência e ajuda na mitigação dos problemas;
	- provê acesso em tempo real a relatórios e métricas, com total visibilidade do impacto do ataque em seus recursos AWS;
	- protege contra ataques de diversos outros tipos, como SYN Flood, UDP Reflection Attack, DNS Query Flood, Cache-Busting Attack etc.;

### AWS Web Application Firewall - WAF
- o [WAF](https://aws.amazon.com/pt/waf) é um firewall de aplicações web que ajuda a proteger suas aplicações web ou APIs contra bots e exploits comuns na web que podem afetar a disponibilidade, comprometer a segurança ou consumir recursos em excesso;

- usado para identificar como as distribuições CloudFront e ALB respondem às requisições web;

- é composto por:
	- *conditions* que definem quais elementos das requisições de entrada HTTP e HTTPS o WAF vai monitorar, sob critérios de seleção de scripts, localidades de origem de requisição, endereço IP, strings e RegEx ou size constraints, além de SQL injection;
	- *rules* que são constituídas por conjuntos de *conditions*, as quais devem ser totalmente satisfeitas, por estarem paralelizadas com o operador *and*;
	- *web ACL* que é constituída por um conjunto de *rules*;

### AWS GuardDuty
- o [GuardDuty](https://aws.amazon.com/pt/guardduty) é um serviço de detecção de ameaças que monitora continuamente suas contas e cargas de trabalho da AWS para atividade maliciosa e fornece resultados de segurança detalhados para visibilidade e remediação;

### Amazon Macie
- o [Macie](https://aws.amazon.com/pt/macie) é um serviço de segurança de dados que descobre dados sigilosos usando machine learning e correspondência de padrões, fornece visibilidade dos riscos de segurança de dados e permite proteção automatizada contra esses riscos;

### Amazon Cognito
- o [Cognito](https://aws.amazon.com/pt/cognito) é um serviço que permite adicionar cadastramento, login e controle de acesso de usuários a aplicações web e móveis com rapidez e facilidade;


## Artificial Intelligence

### AWS Rekognition
- o [Rekognition](https://aws.amazon.com/pt/rekognition/) é um serviço de API que faz análise de imagens e vídeos utilizando Machine Learning e retornando informações categorizadas e classificadas;

### Amazon Comprehend
- **O que é:** Um serviço de processamento de linguagem natural (NLP) baseado em **Inteligência Artificial e Machine Learning**.
- **Como funciona:** Ele analisa textos brutos e desestruturados (como e-mails, artigos, chats ou posts de redes sociais) e extrai insights, conexões e padrões ocultos.
- **Usecases**:
  - **Análise de Sentimento:** Resposta correta para cenários onde a empresa precisa classificar automaticamente se o texto de um cliente é **Positivo, Negativo, Neutro ou Misto** (ex: analisar o feedback de clientes no suporte).
  - **Reconhecimento de Entidades:** Identifica automaticamente elementos-chave no texto, como nomes de lugares, pessoas, datas, marcas ou produtos.
  - **Detecção de PII:** Identifica e sinaliza dados de identificação pessoal para ajudar na conformidade com leis de privacidade.
- É um serviço pré-treinado pela AWS; desenvolvedores podem integrá-lo via API sem precisar de qualquer conhecimento em ciência de dados ou Machine Learning.


## Billing and Pricing

### AWS Support
- o AWS Support é dividido em planos ou níveis; são eles:

- **Basic \(Básico):**
  - *Custo:* Gratuito \(incluso em todas as contas).
  - *O que cobre:* Acesso a fóruns, documentação e suporte para faturamento \(*billing*) e limites da conta. **Zero suporte técnico para problemas em servidores ou códigos.**
  - *Trusted Advisor:* Acesso apenas às verificações básicas de segurança e limites.

- **Developer \(Desenvolvedor):**
  - *Custo:* Pago. Recomendado para ambientes de testes e desenvolvimento.
  - *O que cobre:* Suporte técnico de arquitetura básica via **E-mail** em horário comercial \(um usuário primário).
  - *SLA de Prova:* Resposta em menos de 24h para falhas gerais e **menos de 12h** para sistemas instáveis.

- **Business \(Negócios):**
  - *Custo:* Pago. Recomendado para cargas de trabalho ativas em **Produção**.
  - *O que cobre:* Suporte técnico **24x7 via Chat e Telefone** com engenheiros da AWS \(usuários ilimitados). Acesso total \(100%) às recomendações do AWS Trusted Advisor.
  - *SLA de Prova:* Resposta em **menos de 1 hora** para sistemas de produção fora do ar.

- **Enterprise On-Ramp \(Corporativo Intermediário):**
  - *Custo:* Pago. Recomendado para aplicações de negócios robustas.
  - *O que cobre:* Suporte técnico 24x7 por chat/telefone. Acesso a um pool compartilhado de Gerentes Técnicos de Conta \(TAM).
  - *SLA de Prova:* Resposta em **menos de 30 minutos** para sistemas de negócios críticos fora do ar.

- **Enterprise \(Empresarial):**
  - *Custo:* Pago (foco corporativo de grande porte). Recomendado para sistemas de **Missão Crítica**.
  - *O que cobre:* Suporte técnico 24x7. Dá direito exclusivo a um **TAM \(Technical Account Manager)** — um engenheiro dedicado à sua conta — e suporte à gestão de eventos \(ex: monitoramento na Black Friday).
  - *SLA de Prova:* Resposta recorde em **menos de 15 minutos** para sistemas de missão crítica fora do ar.

### Ferramentas para precificação
- **AWS Pricing Calculator:** calculadora web utilizada para estimar e desenhar o custo financeiro de uma arquitetura **antes** de contratá-la ou migrá-la para a nuvem;
- **AWS Budgets \(Orçamentos):** permite configurar limites de gastos mensais ou diários; ele envia **alertas automatizados** \(e-mail ou SNS) quando seus custos reais *ou previstos* ultrapassam a meta desenhada;
- **AWS Cost Explorer:** ferramenta de análise pós-gasto; fornece gráficos detalhados e relatórios visuais para compreender, detalhar e rastrear os custos históricos obtidos nos meses anteriores na nuvem;

### AWS Organizations
- o [Organizations](https://aws.amazon.com/pt/organizations) é um serviço que ajuda você a gerenciar e controlar seu ambiente de maneira centralizada à medida que os negócios e seus recursos da AWS expandem;

- **características**:
	- gerencia todas as suas contas;
	- permite a consolidação de faturamento \(consolidated bills);
	- com muitas contas e grandes volumes de utilização pode-se obter descontos na AWS;
	- políticas de segurança podem ser controladas de forma “organizacional”;

### AWS Compute Optimizer
- **O que é:** Um serviço gerenciado que utiliza **Machine Learning** para analisar o histórico de uso dos seus recursos e recomendar melhorias para reduzir custos e aumentar a performance.
- **Como funciona:** Ele avalia os dados de telemetria do *Amazon CloudWatch* \(CPU, memória, armazenamento e rede) e identifica se seus recursos estão operando de forma ideal, superdimensionados \(gastando dinheiro à toa) ou subdimensionados \(risco de lentidão).
- Ele gera recomendações específicas e acionáveis para **quatro componentes de computação**:
  1. Instâncias **Amazon EC2** \(sugere a família e tamanho ideal de máquina).
  2. Volumes **Amazon EBS** \(sugere o tipo de IOPS e tamanho do disco).
  3. Funções **AWS Lambda** \(sugere a quantidade ideal de memória RAM alocada).
  4. Serviços **Amazon ECS** no AWS Fargate \(sugere o tamanho de CPU e memória para containers).
- **Custo:** O serviço em si é **gratuito** para analisar métricas padrão de instâncias EC2.

### AWS Marketplace
- o Marketplace é um catálogo digital com milhares de listagens de software de fornecedores independentes \(terceiros) que funcionam perfeitamente na AWS;
- **Usecases**: cenários em que uma empresa precisa "encontrar, testar, comprar e implantar rapidamente softwares de terceiros pré-configurados" \(como uma imagem pronta de um firewall da Cisco ou Fortinet, ou um sistema operacional customizado);
- **Vantagem Financeira**: integra-se ao faturamento consolidado da AWS, facilitando o gerenciamento de custos de licenciamento;

### AWS Data Exchange
- o Data Exchange é um serviço gerenciado que facilita a **descoberta, assinatura e utilização de dados de terceiros** com total segurança na nuvem AWS;
- funciona como um "mercado de dados brutos": em vez de comprar softwares \(como no Marketplace), você assina conjuntos de dados \(*data sets*) fornecidos por empresas globais \(dados financeiros, climáticos, de saúde, demográficos, de geolocalização, etc.);
- ideal para cenários em que uma empresa precisa **consumir dados externos prontos** de fornecedores terceiros para alimentar as suas ferramentas de Big Data, Business Intelligence \(Redshift) ou Machine Learning, sem precisar criar integrações ou APIs manuais;
- **Integração**: os dados assinados são integrados e atualizados automaticamente em buckets do Amazon S3 ou tabelas do Redshift da sua conta;


---------------------------------------------------------------------

# Créditos

- fichamento adaptado do curso [AWS Certified Cloud Practitioner - Preparatório AWS CCP](https://www.udemy.com/course/aws-certified-cloud-practitioner-aws-ccp) e do repositório [AWS Certified Cloud Practitioner](https://github.com/gustavofreze/aws-certified-cloud-practitioner)







