## Computação em nuvem

- É a entrega **sob demanda** \(on demand) de recursos de computação, banco de dados, armazenamento, aplicações ou qualquer outro recurso de tecnologia entregue por uma **plataforma** via internet, onde o pagamento e o preço são baseados em **consumo** \(pay as you go).

### Vantagens

	- **Mudança na modalidade gastos**: muda da modalidade de despesas de capital, [CAPEx](https://pt.wikipedia.org/wiki/CAPEX) ou despesa de aquisição de bens, para modelo de despesa variável,  [OPEx](https://pt.wikipedia.org/wiki/OPEX) ou depesa operacional.

	- **Economia de escala**: com a computação em nuvem, você pode chegar a um custo variável menor do que seria possível por conta própria. Como o uso de centenas de milhares de clientes é agregado à nuvem, os provedores como a AWS têm redução de custos, através da alta escala de aquisição de hardware para a infraestrutura, o que se converte em um menor preço pago em função do uso.

	- **Capacidade**: você cresce ou diminui a capacidade necessária para atender às suas demandas, pagando apenas o que consumir.

	- **Agilidade e velocidade**: recursos estão disponíveis imediatamente; alta disponibilidade.

	- **Economia**: você deixa de gastar dinheiro para comprar e manter data centers.

	- **Global em poucos minutos**: permite que você tenha recursos disponíveis globalmente em poucos minutos, com baixa latência e custo, melhorando a experiência do cliente, através de Content Delivery Network \(CDN).

### Tipos de Cloud Computing

	- **IaaS - Infrastructure as a Service**
		- contratante gerencia os servidores físicos ou virtuais;
		- contratante gerencia os sistemas operacionais e softwares adicionais;
		- o datacenter não tem responsabilidade com o que você faz com os recursos;

	- **PaaS - Platform as a Service**
		- datacenter é responsável pelos recursos físicos ou virtuais, SOs, softwares e alguns itens de segurança;
		- contratante é responsável pela aplicação e sua configuração;
		
	- **SaaS - Software as a Service**
		- toda a responsabilidade é do provedor, como no caso do Gmail, Office 365, Salesforce etc..

### Modelos de Implantação de Cloud Computing

	- **Public Cloud**
		- AWS, Azure, Google Cloud;

	- **Private Cloud**
		- datacenter próprio da empresa \(on-premises), como uma infraestrutura de TI antigam, com recursos dedicados privados;

	- **Hybrid Cloud**
		- Combinação entre Public Cloud e Private Cloud \(on-premises);

## Infraestrutura global

- a [infraestrutura global da AWS](https://aws.amazon.com/pt/about-aws/global-infrastructure) é uma plataforma de nuvem e oferece mais de 200 serviços completos de datacenter em todo o mundo.

### Regiões \(Regions)
- são as localidades físicas onde a AWS está disponível ao redor do mundo.

### Zonas de disponibilidades \(Availability Zone - AZ)
- é a quantidade de datacenters que a AWS tem em cada uma das regiões para prover serviços e produtos. No mínimo, são duas zonas de disponibilidade por região, a fim de proporcionar **alta disponibilidade**, **tolerância a falhas**, *desempenho*, *disaster recovery* e **escalabilidade**.

### Pontos de presença \(Edge locations)
- uma *edge location* é basicamente um pequeno servidor de cache. Eles estão localizados na maioria das principais cidades do mundo e são usados especificamente pelo **CloudFront** \(CDN da AWS) para distribuir conteúdo ao usuário final e reduzir a latência do acesso.

