# INDEX

- [INTRODUCTION](#INTRODUCTION)
- [IPv4 ADDRESSING](#IPv4-ADDRESSING)
	- [NETWORK ADDRESS TRANSLATION](#NETWORK-ADDRESS-TRANSLATION)
	- [DHCPv4](#DHCPv4)
- [IPv6 ADDRESSING](#IPv6-ADDRESSING)
- [IPv4-IPv6 TRANSITIONING](#IPv4-IPv6-TRANSITIONING)
- [PORTS](#PORTS)
- [USER DATAGRAM PROTOCOL](#USER-DATAGRAM-PROTOCOL)
- [TRANSMISSION CONTROL PROTOCOL](#TRANSMISSION-CONTROL-PROTOCOL)
	- [TCP SEGMENT STRUCTURE](#TCP-SEGMENT-STRUCTURE)
- [APPLICATION LAYER PROTOCOLS](#APPLICATION-LAYER-PROTOCOLS)
	- [DNS](#DNS)
	- [HTTP](#HTTP)
	- [FTP](#FTP)
	- [EMAIL PROTOCOLS](#EMAIL-PROTOCOLS)
- [TRANSPORT LAYER SECURITY](#TRANSPORT-LAYER-SECURITY)
- [IPv4 PROTOCOL](#IPv4-PROTOCOL)
- [IPv6 PROTOCOL](#IPv6-PROTOCOL)
- [IPsec](#IPsec)
- [ICMP](#ICMP)
- [ROUTING](#ROUTING)
	- [RIP](#RIP)
	- [EIGRP](#EIGRP)
	- [OSPF](#OSPF)
	- [BGP](#BGP)



------------------------------------------------------------


# INTRODUCTION


### TCP/IP vs. OSI
- *OSI* em 7 camadas:
	- 7. *Aplicação*
	- 6. *Apresentação*
	- 5. *Sessão*
	- 4. *Transporte*
	- 3. *Rede \(Internet)*
	- 2. *Enlace*
	- 1. *Física*

- *TCP/IP* reduz a 5 camadas:
	- *Aplicação*: camadas 7, 6, 5
	- *Transporte*: camada 4
	- *Internet \(Internet)*: camada 3
	- *Enlace*: camada 2
	- *Física*: camada 1

- há um protocolo de criptografia chamado *Transport Layer Security* que, quando é usado, faz o papel da camada de *Apresentação* de forma destacada na pilha TCP/IP;

- Responsáveis pelas camadas:
	- *Aplicação*: Software
	- *Transporte*: Sistema Operacional
	- *Internet \(Internet)*: Sistema Operacional
	- *Enlace*: Hardware
	- *Física*: Hardware

- na pilha de protocolos TCP/IP, as camadas de *Enlace* e *Física* podem ser tratadas como uma única camada de *Acesso à Rede*;

### Camada de Aplicação
- **Protocolos de Aplicação**: linguagens de comunicação utilizadas pelo software da máquina: 
	- FTP, HTTP, DNS, SMTP, IMAP, POP3, Telnet, SSH etc.;

- **PDU - Protocol Data Unit**: estrutura de dados da camada de aplicação é a **MENSAGEM**;

- camada controlada pelo *Software*;

- **endereços específicos**;

### Camada de Transporte
- camada em que se identificam origem e destino de dados;

- **Protocolo TCP - Transmission Control Protocol**: *orientado à conexão*, com handshake e pacote numerados para ordenamento - *confiável*, com mecanismo de confirmação de entrega dos dados - maior *overhead*, complexidade e atraso;

- **Protocolo UDP - User Datagram Protocol**: mais simples e ágil;

- **PDU - Protocol Data Unit**: fracionamento da *MENSAGEM* e encapsulamento em:
	- **segmento TCP**;
	- **datagrama UDP**;

- identificação da *porta* de origem e destino;

- camada controlada pelo *Sistema Operacional*;

- **Endereçamento de portas**;

### Camada de Rede \(Internet)
- - camada de roteamento de dados com endereçamento lógico; camada *entre-redes*;

- **Protocolo IP**: protocolo de comunicação entre redes;
- **Protocolo IPsec**: criptografia para VPN;
- **ICMP - Internet Control Message Protocol**;
- **IGMP - Internet Group Message Protocol**;

- camada de atuação dos **roteadores**;

- **PDU - Protocol Data Unit**:
	- **datagrama IP**:
		- sem conexão;
		- não confiável;

- camada controlada pelo *Sistema Operacional*;

- **Endereçamento Lógico**: *endereços IP* - endereços roteáveis;

### Camada de Enlace \(Link de Dados)
- camada de *Controle de Acesso ao Meio*; camada de dados ou de interface com a rede que usa como referência os *endereços físicos*;

- **PDU - Protocol Data Unit**: 
	- **Quadro**: tamanho variável;
	- **Célula**: tamanho fixo;

- camada controlada pelo *Hardware*;

- **Endereçamento Físico**: *endereços MAC* - não roteáveis, circulando apenas dentro de uma mesma rede;

### Camada Física
- camada de codificação e modulação de bits;
- camada controlada pelo *Hardware*;

### Desencapsulamento
- *Camada Física*: a interface de rede da máquina observa o *meio*, aguardando a recepção de um sinal, que será demodulado e decodificado em bits, sendo enviados para a camada acima;

- *Camada de Enlace - Link de Dados*: a interface de rede da máquina monta os *quadros*, com o cabeçalho que contém o campo do *endereço físico*, para conferi-lo; se o valor do endereço físico não corresponder ao da máquina em questão, o quadro é ignorado; caso o endereço físico corresponda, verifica-se o campo que contém o protocolo para o qual aquele quadro se destina: *IPv4* ou *IPv6*;

- *Camada de Rede - Internet*: verifica-se no cabeçalho do *datagrama IP* qual é o *endereço IP* a que ele se destina; correspondendo o endereço IP, verifica-se o protocolo de destino, que pode ser da camada de transporte \(TCP ou UDP), ou mesmo da própria camada de rede, \(ICMP ou IGMP);

- *Camada de Transporte*: 
	- *segmento TCP*: 
		- orientado à conexão: segmentos são colocados em ordem;
		- confiável: um segmento é gerado e enviado de volta para confirmar o recebimento;
		- a *porta de destino* no cabeçalho é lida e a *mensagem* é encaminhada para a aplicação que está ouvindo a porta designada;

	- *datagrama UDP*: 
		- a *porta de destino* no cabeçalho é lida e a *mensagem* é encaminhada para a aplicação que está ouvindo a porta designada;

### IETF e RFC
- **IETF - Internet Engineering Task Force** estabelece os padrões da pilha de protocolos TCP/IP através dos documentos **RFC - Request for Comments**;


------------------------------------------------------------


# IPv4 ADDRESSING


### Protocolos ARP e RARP
- **ARP - Address Resolution Protocol**: protocolo de quadros enviados em broadcast buscando um retorno de *endereço físico* correspondente a um *endereço IP* conhecido;

- **RARP - Reverse Address Resolution Protocol**: protocolo de quadros enviados em broadcast buscando um retorno de *endereço IP* correspondente a um *endereço físico* conhecido;
	- essa funcionalidade foi absorvida pelo **protocolo DHCP**;

### Tipos de Endereçamento IPv4
- **Unicast**
	- identifica um único nó;

- **Broadcast**
	- identifica todos os nós de uma rede;

- **Multicast**
	- identifica um grupo de nós dentro de uma rede;
	- utiliza o protocolo *IGMP - Internet Group Message Protocol*;

- **Anycast**
	- identifica mais de um nó com o mesmo endereço IP dentro de uma rede;
	- acessa o nó fisicamente mais próximo com o IP compartilhado, com o menor número de saltos;
	- utilizado em sistemas *CDN - Content Delivery Network*;
	- não é nativo no IPv4, sendo implementado via BGP;

### Estrutura do Endereçamento IPv4
- endereço de *32 bits*;
- **CIDR - Clasless Inter-Domain Routing**: roteamento entre domínios sem uso de classes: 
	- ``` 192.168.0.0/24 ```;

- Máscara de Subrede \(ou Máscara de Rede):
	- ``` 255.255.255.0 ```;

- Endereço de Rede \(primeiro endereço da rede):
	- ``` 192.168.0.0 ```;

- Endereço de  Broadcast da Rede \(último endereço da rede):
	- ``` 192.168.0.255 ```;

- o número de endereços disponíveis em uma rede sempre é: ``` 2ⁿ - 2 ```, em que *n* é o número de bits reservados para a identificação de nós, à direita;

### VLSM \(Segmentação)
- **Variable-Length Subnet Masking**: Mascaramento de Subrede de Comprimento Variável;
- permite dobrar o número de redes disponíveis acrescentando mais um bit ao CIDR, por outro lado, dividindo por 2 o número de nós possíveis;

### Agregação de Rotas
- consiste na união de redes próximas em entradas de *tabelas de roteamento* em roteadores;
- possível apenas quando várias redes são acessadas por um mesmo caminho, *i. e.*, por um mesmo roteador;

### Máscara Coringa
- consiste na utilização de máscara com bits 0 marcando valores fixos e bits 1 marcando valores variáveis de uma faixa de endereço IP;

### Classes
- 0.0.0.0 a 127.255.255.255 - CIDR /8 - CLASSE A
	- bit inicial: 0

- 128.0.0.0 a 191.255.255.255 - CIDR /16 - CLASSE B
	- bits iniciais: 10

- 192.0.0.0 a 223.255.255.255 - CIDR /24 - CLASSE C
	- bits iniciais: 110

- 224.0.0.0 a 239.255.255.255 - CLASSE D - MULTICAST
	- bits iniciais: 1110

- 240.0.0.0 a 255.255.255.255 - CLASSE E - RESERVADA
	- bits iniciais: 1111

### Faixas Especiais
- ``` 0.0.0.0/8 ```
	- indica a rede local ou qualquer rede;

- ``` 10.0.0.0/8 | 172.16.0.0/12 | 192.168.0.0/16 ```
	- endereçamento privado;

- ``` 127.0.0.0/8 ```
	- loopback \(realimentação) - o próprio host;

- ``` 192.0.2.0/24 | 198.51.100.0/24 | 203.0.113.0/24 ```
	- documentação e exemplos;

- ``` 169.254.0.0/16 ```
	- Zeroconf/APIPA, endereçamento automático normalmente usado por sistemas Windows quando um servidor DHCP não retorna um endereço IP;

- ``` 198.18.0.0/15 ```
	- equipamentos para teste de rede;

- ``` 192.88.99.0/24 ```
	- conversão de endereços IPv6 em IPv4;

- ``` 192.0.0.0/24 | 224.0.0.0/4 | 240.0.0.0/4 ```
	- reservada, derivadas das antigas classes D e E;

### Endereçamento IPv4 Públicos
- os blocos de endereçamento são distribuídos pela **IANA - Internet Assigned Numbers Authority**;
- a *LACNIC* é a entidade que distribui as faixas na América do Sul;

### Endereçamento IPv4 Privados

| Faixa				| Endereço Inicial	| Endereço Final 	|
|------------------*|-------------------|-------------------|
| 10.0.0.0/8 		| 10.0.0.0			| 10.255.255.255	|
| 172.16.0.0/12		| 172.16.0.0		| 172.31.255.255	|
| 192.168.0.0/16	| 192.168.0.0		| 192.168.255.255	|

------------------------------------------------------------

## NETWORK ADDRESS TRANSLATION

### NAT
- mecanismo pelo qual o roteador que habilita o acesso à WAN substitui o IP privado pelo IP público;

### NAT Dinâmico
- é realizada uma associação dinâmica de IPs privados em um índice com IPs públicos disponíveis para o roteador;
- o número de conexões é limitado pelo número de IPs públicos disponíveis para o roteador;
- **NAT Estático**
	- força a conversão de um IP privado sempre no mesmo IP público dentro do sistema NAT dinâmico;

### NAT Overload
- ou **PAT - Port Address Translation** é o método mais utilizado;
- o roteador passa a manipular também os campos *porta* nos 4 primeiros bytes do *datagrama IP*;
- pelo método *PAT*, o número da porta é também substituído, de modo a identificar no roteador o IP de origem e a porta de origem, gerando um índice de conversão;

### CGNAT
- **Carrier-Grade Network Address Translation** é o mecanismo pelo qual um provedor configura sua rede em uma faixa de endereçamento privado para prover serviços de IP público dinamicamente, para solucionar a exaustão de endereços IPv4;

------------------------------------------------------------

## DHCPv4

### Dynamic Host Configuration Protocol v4
- protocolo de aplicação responsável por realizar a configuração dos endereços em uma rede;

### Modos de Configuração
- **Manual**;

- **Dinâmico**: o servidor DHCP entrega um endereço IP dentro da faixa de rede configurada, sem garantia de que sempre será a mesma;

- **Automático**: o servidor DHCP tenta entregar um mesmo endereço IP a um nó apenas quando possível;

- **Estático**: o servidor DHCP sempre entrega o mesmo endereço IP a um nó;

### Protocolo de Comunicação
- o protocolo DHCP utiliza como método de transporte o protocolo **UDP**:
	- *servidor: porta 67*;
	- *cliente: porta 68*;

- **etapas de comunicação**
	- 1. um nó cliente solicita a entrada na rede através de uma mensagem **DHCPDISCOVER** em *broadcast*;
	- 2. o servidor DHCP responde com uma mensagem **DHCPOFFER**; pode haver mais de um servidor DHCP na rede, e todos respondem;
	- 3. o cliente direciona uma mensagem **DHCPREQUEST** em *broadcast*, mas direcionada a um servidor DHCP escolhido;
	- 4. o servidor retorna uma mensagem DHCP Acknowledge **DHCPACK**;

- **outras mensagens**:
	- *DHCPRELEASE*: mensagem do cliente liberando seu IP e solicitando a renovação;
	- *DHCPINFORM*: mensagem de solicitação de informações ao servidor DHCP;


------------------------------------------------------------


# IPv6 ADDRESSING

### Simplificação do Endereçamento IPv6
- zeros à esquerda podem ser removidos;
- um bloco com apenas zeros deve ser sinalizado com pelo menos um zero;
- vários blocos em sequência com zeros podem ser sinalizados com apenas um par de dois pontos ``` :: ```; apenas uma sequência em um endereço IPv6 pode ser abreviada dessa forma;

### Outras Características
- possui configuração automática **SLAAC - StateLess Address AutoConfiguration**, tornando o protocolo DHCP opcional;
- não há ARP/RARP;
- não há sistema de broadcast, que é substituído pelo sistema multicast:

### Tipos de Endereçamento IPv6
- **Unicast**
	- identifica um único nó;

- **Multicast**
	- substitui o *broadcast* em IPv6;
	- endereço padrão multicast:
		- multicast padrão para máquinas: *ff02::1*;
		- multicast padrão para roteadores: *ff02::2*;
	- identifica um grupo de nós dentro de uma rede;
	- utiliza o protocolo *IGMP - Internet Group Message Protocol*;

- **Anycast**
	- identifica mais de um nó com o mesmo endereço IP dentro de uma rede;
	- acessa o nó fisicamente mais próximo com o IP compartilhado, com o menor número de saltos;
	- utilizado em sistemas *CDN - Content Delivery Network*;
	- suporte nativo com IPv6;
	- o primeiro endereço IPv6 sempre identifica o gateway padrão de uma rede;

### Escopos IPv6

| Valor hex	| Escopo			| Equivalência IPv4	| Uso					|
|-----------|-------------------|-------------------|-----------------------|
| 0 		| reservado			|					|						|
| 1 		| interface-local 	| loopback 			| uso em loopback;		|
| 2			| link-local		| privado			| endereçamento privado |
| 3			| realm-local		| 					| definido auto			|
| 4			| admin-local		| 					| definido pelo admin	|
| 5			| site-local		|					| definido pelo admin	|
| 8			| organization-local|					| definido pelo admin	|
| e			| global			| público			| endereçamento público |
| f 		| reservado			|					|						|


### Endereçamento IPv6 Unicast e Anycast Globais
- 128 bits em 8 blocos de 16 bits;
- Prefixo | Sub-rede | IID 64 bits:
	- Prefixo + Sub-rede = Identificação da Rede em 64 bits;
	- IID = Identificação do Nó;
- faixa de endereços públicos: 
	- ``` 2000:: até 3 ```;

### Endereçamento IPv6 Local
- **Local-Link**:
	- Prefixo 
		- ``` fe80::/64 ```;
	- não permite configuração de sub-redes - sem segmentação;
	- usado em redes menores;

- **ULA - Unique Local Address**:
	- permite segmentação em sub-redes;
	- usado em redes de médio porte;
	- estrutura: 
		- ``` fd | 40 bits aleatórios de prefixo | 16 bits sub-rede | IID 64 bits ```

### IID Interface Identifier
- o campo de identificação da interface é constituído pelo endereço físico da interface quando o prefixo *não* se inicia por 0 ou 1;
	- utiliza-se o formato *EUI-64* de 64 bits, convertido a partir do endereço físico que comumente se apresenta com 48 bits:
		- o endereço MAC é separado em dois grupos de 3 bytes \(24 bits);
		- entre eles são acrescentados os 2 bytes FF FE;
		- inverte-se o valor do terceiro bit \(U/L), o que implica normalmente em tornar o primeiro byte 00 um byte 02;
		- separar em 4 grupos de 4 algarismos para obter o IID;

### Índices e Colchetes
- *Windows*:
	- fe80::1234%1 - 1ª interface
	- fe80::1234%2 - 2ª interface

- *Unix*:
	- fe80::1234%eth0 - 1ª interface
	- fe80::1234%eth1 - 2ª interface

- Colchetes:
	- são usados para marcar endereçamento IPv6 em URL;
	- isso evita ambiguidade com números de porta, separados por dois pontos;

### NDP - Neighbor Discovery Protocol
- o *Protocolo de Descoberta de Vizinhos* equivale ao Protocolo ARP do IPv4, que permite descobrir o endereço físico de um nó a partir do endereço IP;

- o *NDP* faz parte do sistema de auto-configuração **SLAAC - StateLess Address AutoConfiguration** do IPv6, provendo informações que equivalem ao Protocolo DHCP do IPv4, funcionando apenas quando o sistema SLAAC estiver ativado;

- o *NDP* fornece ainda o prefixo da rede, o endereço IPv6 do gateway padrão e o endereço IPv6 do servidor DNS;

- o *NDP* utiliza o protocolo **ICMPv6** para o envio das mensagens:

	- 1. **solicitação de roteador** *ICMPv6 tipo 133*:
		- mensagem enviada por um nó a todos os roteadores de uma rede para obter informações sobre os parâmetros da rede;
		- mensagem enviada para o multicast padrão de roteador: ``` ff02::2 ```;

	- 2. **anúncio de roteador** *ICMPv6 tipo 134*:
		- enviada por todos os roteadores de uma rede em resposta à *solicitação de roteador*;

	- 3. **solicitação de vizinho** *ICMPv6 tipo 135*:
		- mensagem equivalente ao ARP do IPv4;
		- solicita o endereço físico da máquina de destino;

	- 4. **anúncio de vizinho** *ICMPv6 tipo 136*:
		- mensagem equivalente a uma operação de resposta ARP do IPv4;
		- contém o endereço físico da máquina-alvo;

	- 5. **redirecionamento** *ICMPv6 tipo 137*:
		- enviada à orgigem de um roteador para informá-la que existe outro roteador com menor número de saltos até um determinado alvo;
		- equivale à mensagem ICMPv4 de redirecionamento - tipo 5;

### DHCPv6
- utiliza também o protocolo *UDP* na *camada de transporte*, mas em portas diferentes:
	- *cliente: porta 546*;
	- *servidor: porta 547*;

- utiliza endereços de multicast:
	- *ff02::1:2* usado por todos os servidores e relays DHCP da rede;
	- *ff05::1:3* usado por todos os servidores DHCP da rede para acesso por relays;

- os parâmetros principais para acesso à internet, endereço IP e dervidor DNS, são obtidos de forma automática pelo sistema *SLAAC - StateLess Address AutoConfiguration*, através do  protocolo *NDP*; o procotolo *DHCPv6* faz-se opcional, sendo usado apenas quando se deseja incluir outros parâmetros de configuração, feito seleção de servidor DNS alternativo;

- mensagens com SLAAC ativo:
	- *information_request* com a especificação do dado que o cliente busca do servidor DHCPv6, para o endereço multicast *ff02::1:2*;
	- *reply* com a resposta solicitada;

- mensagens com SLAAC desativado com apenas um servidor DHCPv6:
	- *solicit* com a opção de configuração expressa, *rapid commit*, para que todos os dados necessários retornem em mensagem única;
	- *reply* com a resposta solicitada;

- mensagens com SLAAC desativado em operação completa, com mais de um servidor DHCPv6:
	- *solicit*;
	- *advertise* anúncio enviado por todos os servidores DHCPv6 da rede;
	- *request* para o servidor escolhido;
	- *reply* com a resposta solicitada;


------------------------------------------------------------


# IPv4-IPv6 TRANSITIONING

### Pilha Dupla: IPv4 mapeado em IPv6
- usado para acessar máquinas IPv4 em redes IPv6, sendo o mais utilizado;
- endereço IPv4 é convertido em um endereço IPv6 prefixo *::ffff:0:0/96*:

	- IPv4 192.0.2.33 - IPv6 ::ffff:192.0.2.33 ou ::ffff:c000:221;

### Tradução: SIIT - Stateless IP/ICMP Translation
- usado para acessar máquinas IPv4 em redes IPv6;
- sistema de tradução de cabeçalho, usando o prefixo *::ffff:0:0:0/96*:

	- IPv4 192.0.2.33 - IPv6 ::ffff:0:192.0.2.33 ou ::ffff:0:c000:221;

### Tradução: NAT64
- usado para conectar uma rede IPv4 a uma rede IPv6;
- sistema de tradução de endereços em um roteador, adicionando ou removendo dos IPv4s o prefixo bem conhecido *64:ff9b::/96*:

	- IPv4 192.0.2.33 - IPv6 64:ff9b::192.0.2.33 ou 64:ff9b::c000:221;

### Tradução: DNS64
- usado para converter endereços IPv4 em IPv6 em requisições DNS;
- sistema de tradução de endereços em um servidor DNS, adicionando ou removendo dos IPv4s o prefixo *64:ff9b::/96*, como no NAT64;

### Tunelamento: Túnel 6to4
- usado quando uma conexão entre redes IPv6 passa por uma rede IPv4 no caminho;
- os roteadores envolvidos no tunelamento precisam ser compatíveis com a tecnologia 6to4;
- prefixo *2002::/16*;
- apresenta problemas anycast;
- necessita de endereços IPv4 públicos;

### Tunelamento: Túnel 6rd
- *rapid deployment* - implementação rápida;
- usado quando uma conexão entre redes IPv6 passa por uma rede IPv4 no caminho;
- prefixo IPv6 público do provedor de acesso;
- baseado no 6to4 sem problemas anycast;
- necessita de endereços IPv4 públicos;

### Tunelamento: Túnel Teredo
- soluciona a necessidade de endereços IPv4 públicos pela compatibilidade com a tradução NAT de endereços IPv4 privados;
- utiliza um servidor *Teredo*, que pode estar na internet, para criar endereços IPv6 públicos;
- estrutura:

	- 2001:0000:aabb:ccdd:xxxx:pppp:aabb:ccdd
	- prefixo:0000:IPv4Te:redo:flags:portaUDPofuscado:IPv4doNATofuscado


------------------------------------------------------------


# PORTS


### Organização das Portas
- o campo *porta*, em segmentos TCP ou datagramas UDP, possui 16 bits: 2¹⁶ = 65.536 \(0 a 65.535);

- **portas bem conhecidas ou privilegiadas**: 
	- portas 0 a 1.023;
	- só podem ser usadas no lado do servidor;
	- não podems ser usadas no lado do cliente;
	- padronizadas pela IANA para protocolos com RFC regulamentadora;

- **portas registradas**: 
	- portas 1.024 a 49.151;
	- padronizadas pela IANA para protocolos sem RFC regulamentadora;
	- podem ser usadas no lado do servidor, como porta bem conhecida, e no lado do cliente, como porta dinâmica;

- **portas dinâmicas, privadas ou efêmeras**: 
	- portas 49.152 a 65.535;
	- podem ser usadas livremente por aplicações;
	- usadas, por exemplo, em diferentes abas de um navegador, como cliente HTTP;


------------------------------------------------------------


# USER DATAGRAM PROTOCOL


### UDP
- características básicas:
	- protocolo simples;
	- sem conexão;
	- não confiável: não confirma recebimento de dados;

- *estrutura de dado*: **DATAGRAMA**;

- *vantagens*: mais simples, mais ágil, mais rápido, demanda menor processamento;
- *desvantagens*: não confirma recebimento; dados fora de ordem para a aplicação;

- uso mais frequente por:
	- *Aplicações de Controle, Estado e Configuração de Rede*:
		- DNS;
		- DHCP;
		- RIP - Routing Information Protocol;

	- *Aplicações de Tempo Real*:
		- Streaming de Vídeo;
		- Vídeoconferência;
		- Jogos Online;

### Estrutura do Datagrama UDP
- cabeçalho:
	- porta de origem - 2 bytes;
	- porta de destino - 2 bytes;
	- tamanho do datagrama - 2 bytes;
	- checksum - 2 bytes;

- área de dados com tamanho variável entre 0 e 65.527 bytes \(= 65.535 bytes - 8 bytes de cabeçalho);


------------------------------------------------------------


# TRANSMISSION CONTROL PROTOCOL


### TCP
- características básicas:
	- protocolo mais complexo;
	- orientado à conexão: segmentos são numerados para fins de reordenamento;
	- confiável: possui mecanismo de confirmação de recebimento de dados com segmento Acknowledge;

- *estrutura de dado*: **SEGMENTO**;

- usado para transportar dados de usuário:
	- comunicação Web: HTTP ou HTTPS;
	- email: POP3, IMAP, SMTP;
	- transferência de arquivo: FTP;
	- serviços de terminal: SSH e Telnet;

### Abertura de Conexão
- *handshake de três vias*:
	- transmissor envia um segmento TCP contendo o *número de sequência*, aleatório, inicial e um bit de sincronia *SYN*;
	- o receptor retorna um segmento TCP com o mesmo número de sequência + *SYN* + *ACK* \(aknowledge);
	- o transmissor retorna um segmento TCP com um *ACK* confirmando a conexão;

- *SYN* e *ACK* são bits de controle;

### Fechamento de Conexão
- *handshake de quatro vias*:
	- a máquina que toma iniciativa do encerramento da conexão envia um segmento TPC contendo um bit *FIN* ativado;
	- o receptor retorna um segmento TCP com *ACK*;
	- o receptor envia outro segmento TCP com *FIN*;
	- o transmissor confirma com segmento TCP com *ACK*;

- *FIN* e *ACK* são bits de controle;

### Confirmação de Recebimento
- segmentos TCP são numerados aleatoriamente no início e depois com números ordenados;

- a confirmação é realizada através de um segmento TCP de confirmação com o bit *ACK* \(aknowledge) ativado;

- acrescenta-se um valor no campo *número de confirmação* que serve também para ordenar os segmentos TCP;

- a ordem é definida e reprendentada pela adição ao número aleatório inicial do valor que representa o tamanho da área de dados em bytes;

- o segmento TCP com *ACK* ativado retorna com o campo de número de confirmação contendo a numeração do próximo segmento TCP esperado do emissor \(número do pacote anterior + tamanho da área de dados);

- **RTT - Return Trip Time** é o tempo entre o envio de um segmento e o retorno de sua confirmação;

### Full Duplex
- uma vez estabelecida a conexão, a máquina A pode enviar segmentos TCP para a máquina B e vice-versa simultaneamente, em uma mesma conexão;

- **Piggybacking**
	- como a comunicação é em *full-duplex*, pacote transmitindo dados também podem transmitir confirmação de recebimento de outros pacotes;

### Janela TCP
- **janela** é o mecanismo pelo qual um grupo de pacotes é definido para intervalo de retorno *ACK*, para fins de otimização de tempo de transmissão;

- como a numeração dos segmentos TCP é feita com base no tamanho do campo de dados, a janela pode ser medida pela quantidade de dados transmitidos em um intervalo de pacotes;

- **SACK - Selective Acknowledge** é um mecanismo opcional pelo qual se evita a retransmissão de pacotes recebidos de um intervalo, em caso de perda de dados;

- **Campo Tamanho da Janela**:
	- 2 bytes = 16 bits = 2¹⁶ = 65.536 = a janela pode ser configurada pelo receptor entre 0 e 65,535 bytes;
	- o tamanho da janela é configurado através de um mecanismo de *controle de fluxo*;
	- *SWS - Silly Window Syndrome* síndrome da janela pequena: 
		- o *controle de fluxo* é feito com base na capacidade do receptor dos pacotes processar o recebimento sem congestionamento;
		- a área de dados pode ser continuamente tão reduzida que ocorre *overhead* \(desperdício), em que o tamanho da área de dados não é compensador se comparado ao cabeçalho do pacote;
		- o valor *0* colocado no campo *tamanho da janela* pausa a transmissão de dados e aciona um temporizador até um novo envio de pacote;

------------------------------------------------------------

## TCP SEGMENT STRUCTURE

### Estrutura do Segmento TCP

- **cabeçalho**:
	- porta de origem - 2 bytes;
	- porta de destino - 2 bytes;
	- número de sequência - 4 bytes:
		- número de identificação de cada segmento TCP;
	- número de confirmação - 4 bytes:
		- número inserido pelo receptor do próximo segmento TCP esperado;
	- deslocamento - 4 bits:
		- *HLEN - header length*: tamanho do cabeçalho em número de linhas:
			- pode conter um número 5 ou 6 ou mais, que são as linhas, sendo 6 ou mais quando o campo *opções* estiver presente, considerando sua quantidade de linhas;
	- reservado - 3 bits;
	- controle - 9 bits:
		- *control flags*;
	- tamanho da janela - 2 bytes;
	- checksum - 2 bytes;
	- ponteiro de urgência - 2 bytes:
		- usado apenas quando o bit de controle *URG* está ativado;
	- opções + preenchimento - tamanho variável;

- **área de dados** com tamanho variável até 65.535 bytes \(*MMS - Maximum Segment Size*);
	- idealmente de acordo com o *Datagrama IP*:
		- IPv4: 576 bytes - 20 bytes de cabeçalho = 556 bytes de dados no *Datagrama IP*:
			- Segmento TCP: 556 - 20 bytes de cabeçalho sem opções = 536 bytes no *Segmento TCP*;

		- IPv6: 1.280 bytes - 40 bytes de cabeçalho = 1.240 bytes de dados no *Datagrama IP*:
			- Segmento TCP: 1.240 - 20 bytes de cabeçalho sem opções = 1.220 bytes no *Segmento TCP*;

- **bits de controle**:
	- NS:
		- *ECN-Nonce*: bit experimental para evitar a manipulação de bits *ECE* e *CWR*;
		- os três primeiros bits de controle são usados pelo sisstema *ECN - Explicit Congestion Notification*, que interage com o *Protocolo IP* na *camada de rede*;
	- CWR:
		- *Congestion Window Reduced*;
		- bit ativado em resposta ao bit *EXE*;
	- ECE:
		- *ECN-Echo*: terceiro *ECN*, ativado durante a abertura de conexão, com o *SYN*, indicando que a máquina é compatível com o sistema *ECN*;
		- caso o *ECE* esteja ativado sem a ativação do *SYN*, fica indicado ao protocolo IP que há problema de congestionamento na rede;

	- URG:
		- *Urgent*, para indicar a ativação do *campo ponteiro de urgência*;
	- PSH:
		- *Push*;
		- força o envio de um segmento, mesmo que sua área de dados não esteja completamente preenchida;
		- usado em terminais \(Telnet ou SSH), por exemplo, para enviar sinais de dispositivos de entrada;
	- RST:
		- *Reset*;
		- reinicia a conexão;
	- SYN:
		- usado na abertura de conexão;
	- FIN:
		- usado para encarrar conexão;

- **campo opções**:
	- campo opcional para instruções;
	- pode ter mais de uma linha;
	- subcampos:
		- Tipo - 1 byte:
			- 2: para tamanho da área de dados;
			- 3: para *escala da janela*, em que o valor é a potência cuja base é 2, pelo que se multiplica o *tamanho da janela*;
			- 4: confirmação seletiva SACK permitida;
			- 5: confirmação seletiva com o campo opções transportando o número de sequência do segmento a confirmar;
			- 8: timestamp;
			- 14: algoritmo para método alternativo de checksum;
			- 15: transporte do valor checksum, caso maior que 16 bits, não cabendo no campo checksum padrão;
		- Comprimento - 1 byte:
			- indica o tamnho total do campo opções em bytes;
		- Opções e Preenchimento:
			- o preenchimento são os bytes acrescendados, quando necessário, para que o total de bytes sempre seja igual a um múltiplo de 4 bytes \(largura de 32 bits);
			- quando houver mais de uma opção, apenas a última terá o campo preenchimento ocupado por zeros; nos outros casos, com uns;


------------------------------------------------------------


# APPLICATION LAYER PROTOCOLS


## DNS

### DOMAIN NAME SYSTEM
- resolve nomes de domínio em IP;

### URL - Uniform Resource Locator
- endereço web, *link*;

- estrutura:

	- protocolo: http://, https://, ftp://;

	- **FQDN - Fully-Qualified Domain Name** \(Nome de Domínio Totalmente Qualificado):
		- **TLD - Top-Level Domain**: 
			- *country top-level*: .com.br, .co.uk etc.; 
			- *generic top-level*: .edu, .net etc;
		- **Domínio**: nome do site;
		- **host, máquina ou subdomínio**: www.;

	- **User**: nome de usuário em endereço de email, antes do *arroba*, i. e., *at*:
		- user@site.com: user at site = user at FQDN;

- não há distinção entre maúsculas e minúsculas;

### Servidores DNS
- servidores DNS para URLs acessados pelos clientes são **resolvedores** ou **servidores recursivos** \(Recursive Resolver);

- armazenam nomes e IPs por meio de *cache*, em registros com **TTL - Time To Live**: tempo de vida do cache do registro, após o qual ele é atualizado;

- podem ser *privados* ou *públicos*, como:
	- Google: ``` 8.8.8.8 ```;
	- CloudFlare: ``` 1.1.1.1 ```;

- solicitações DNS são enviadas para a **porta 53** do servidor DNS, através de:
	- *datagrama UDP*, quando mensagens até 512 bytes;
	- *segmento TCP*, quando mensagens com mais de 512 bytes;

- **forwarding** é a consulta de um nome a servidores raiz que não estão no cache dos servidores recursivos;

- servidores consultados pelos *resolvedores* para atualização de cache são:
	- **servidores root - servidores raiz**: retorna o IP de um determinado *servidor TLD*; há apenas 13 endereços IP anycast de servidores root;
	- **servidor TLD**: retorna o IP de um *servidor autoritativo*;
	- **servidor autoritativo**: servidor de registro de IPs de FQDNs;

### Consulta DNS
- *nslookup* e *dig*: comandos para consultar uma URL por linha de comando;

- serviços DNS estáticos locais ficam armazenados em:
	- Windows: ``` C:\windows\system32\drivers\etc\hosts ```;
	- Linux: ``` /etc/resolv.conf ```;

- **consultas recursivas**: 
	- consulta a servidores *resolvedores*, sendo realizada recursivamente até que todo o FQDN esteja completo;

- **consultas iterativas \(não recursivas)**: consulta que o servidor responde apenas quando é o responsável pela resolução do nome consultado; 
	- consulta a servidores *root*, servidores *TLD* e servidores *autoritativo*;

- **registros RR - Resource Records**:
	- A: mapeia nome em endereço *IPv4*;
	- AAAA: mapeia nome em endereço *IPv6*;
	- MX: *Mail eXchange*;
	- CNAME: mapeia um nome alternativo para um registro; alias;
	- PTR: converte IP para domínio; inverso de A;
	- NS: equivale ao registro A exclusivo para nome do *Name Server*;
	- SOA: *Start Of Authority*: declara que será um Servidor Autoritativo;

- **consulta reversa**: retorna o FQDN para um IP fornecido;

### DNSsec
- *cache poisoning* é um tipo de ataque a *servidores recursivos* com a finalidade de alterar o cache;
- o *protocolo DNSsec* é um protocolo de autenticação que atesta a veracidade de registros DNS;

### bind
- aplicação Open Source que implementa servidor DNS no Linux;
- o nome do daemon é *named*;
- arquivo de configuração: /etc/named.conf;

------------------------------------------------------------

## HTTP

### HyperText Transfer Protocol
- protocolo para navegação pela internet através de textos com links entre si, formando a World-Wide Web;

### Funcionamento
- inserido o nome do endereço no browser, um *servidor DNS* resolve o nome em um *endereço IP*;
- o browser estabelece uma *conexão TCP* com o servidor Web, através da porta:
	- **80** sem criptografia;
	- **443** com criptografia - HTTPS;

- *principais métodos de requisição HTTP*:
	- GET: solicita arquivos do servidor Web, como uma página inicial */*:
		- o servidor retorna o HTML da página com códigos de resposta:
			- 200: Ok;
			- 301: Moved Permanently;
			- 304: Not Modified;
			- 403: Forbidden;
			- 404: Not Found;
			- 500: Internal Server Error;
	- POST: envia dados do cliente para o servidor Web, como formulários;

------------------------------------------------------------

## FTP

### File Transfer Protocol
- protocolo de transferência de arquivo;
- autenticação obrigatória, com possibilidade de autenticação anônima;

- aplicações para transferência de arquivos:
	- ftp: linha de comando;
	- Filezila: gráfico;

### Funcionamento
- FTP utiliza duas conexões TCP:
	- *conexão controle*:
		- mantida aberta durante toda a conexão;
	- *conexão dados*
		- é aberta e fechada para cada arquivo transferido;

- **abertura de conexão**:
	- solicitação abertura de *conexão TCP controle* com a *porta 21* do servidor;
	- servidor retorna uma mensagem de boas vindas *220 - client connection accepted*;
	- cliente solicita conexão segura através do comando *AUTH TLS*, com protocolo de criptografia TLS;
	- servidor retorna a mensagem *530 - Please login with USER and PASS*;
	- cliente envia comandos USER e PASS;
	- servidor retorna a mensagem *230 - Login successful*;

- **modo ativo**:
	- solicitação abertura pelo cliente de *conexão TCP dados*, através da *porta 20* do servidor, com o comando *PORT* + IP do cliente + porta enviado à porta 21 do servidor;
	- o servidor abre a conexão, no *modo ativo*, com three-way handshake; pode haver problemas com firewall do lado do cliente;
	- cliente solicita arquivo com comando *RETR* através da conexão de controle;
	- o arquivo é enviado pela conexão de dados;
	- servidor envia pela conexão de controle a mensagem *226 - Transfer complete* quando a transferência é concluída;

- **modo passivo**:
	- solicitação abertura pelo cliente de *conexão TCP dados*, com o comando *PASV*;
	- servidor retorna a mensagem *227 Entering passive mode* com seu IP e porta aleatória para a conexão de dados;
	- cliente abre a conexão, no *modo passivo*, com three-way handshake;
	- o modo passivo é o mais utilizado devido ao frequente uso de firewall do lado do cliente;

------------------------------------------------------------

## EMAIL PROTOCOLS

### SMTP
- *Simple Mail Transfer Protocol* é um protocolo usado entre servidores de email e entre um cliente e um servidor de email para envio de emails;

- **porta 25** ou **porta 587 - submission TLS**;

### POP3
- *Post Office Protocol v. 3* é um protocolo usado para acesso a caixas postais localizadas no servidor de email;

- servidor ouve na **porta 110** ou **porta 995**, com criptografia POP3S;

- características principais:
	- remove os emails do servidor assim que são baixados pelo cliente;
	- não permite mais de um cliente acessando uma mesma caixa postal simultaneamente;
	- concentrado no lado do cliente;

### IMAP4
- *Internet Message Access Protocol v. 4* é um protocolo usado para acesso a caixas postais localizadas no servidor de email;

- servidor ouve na **porta 143** ou **porta 993**, com criptografia IMAPS;

- características principais:
	- mantém emails no servidor, mesmo depois de baixados pelo cliente;
	- há sincronia entre cliente e servidor;
	- permite criar novas pastas e regras no cliente e no servidor;
	- concentrado no lado do servidor;


------------------------------------------------------------


# TRANSPORT LAYER SECURITY


### TLS
- é um protocolo de segurança que sucede o *SSL - Secure Socket Layer*, para segmentos TCP;

- atua protegendo apenas dados de usuário; cabeçalhos TCP e UDP não são protegidos;

- objetivos básicos de segurança:
	- **autenticidade**: confirmar a origem de um dado;
	- **integridade**: confirmar que os dados não foram adulterados;
	- **confidencialidade**: confirmar que os dados não sejam capturados sem autorização;

- o *TLS* opera na camada de *Apresentação*, ou entre *Aplicação* e *Transporte* na pilha TCP/IP;
- portanto, atua apenas em *mensagens*, protegendo apenas *dados de usuário*;
- ativado pela própria aplicação, sem requerer intervenção do usuário;
- ultiliza a porta 443 *HTTPS* do lado do servidor;

### Handshake
- subprotocolo *TLS* responsável pela autenticação;
	- obrigatória para o servidor;
	- opcional para o cliente;

- realiza troca de chaves e parâmetros de configuração;

- cliente e servidor negociam um conjunto de códigos \(CipherSuite), por meio das primeiras mensagens da comunicação, definindo os algoritmos criptográficos que serão usados;

- a autenticação se baseia no uso de certificado digital do lado do servidor obrigatoriamente e opcional para o cliente;

- são usadas chaves criptográficas públicas para o handshake;

### Registro \(Record)
- subprotocolo *TLS* responsável pela integridade e pela confidencialidade;

- fraciona a *mensagem* em registros, criptografando cada um individualmente;

- são usadas chaves criptográficas simétricas \(chaves compartilhadas) para o registro;


------------------------------------------------------------


# IPv4 PROTOCOL


### Estrutura do Datagrama IPv4
- **cabeçalho**:
	- versão \(4 bits7ª - linha 1 de 32 bits):
		- valor 4;
	- tamanho do cabeçalho *IHL - Internet Header Length* \(4 bits - linha 1 de 32 bits):
		- número de linhas do cabeçalho, com valor de no mínimo 5 ou até 15, caso o campo opções seja usado, entre 0 a 10 linhas além das 5 linhas mínimas do cabeçalho;
	- serviço diferenciado *DS* \(6 bits - linha 1 de 32 bits):
		- tipo de serviço ou *qualidade do serviço*;
		- dos 64 códigos disponíveis, 32 são utilizados para classificar a prioridade do datagrama;
	- *ECN - Explicit Congestion Notification* \(2 bits - linha 1 de 32 bits):
		- sistema para sinalizar congestionamento nos roteadores pelo caminho, com a ativação dos dois bits pelo roteador congestionado;
		- o segmento TCP de confirmação retorna com o bit ACK e ECE ativados, para sinalizar a necessidade de redução da taxa de envio de dados pelo transmissor;
	- tamanho total \(2 bytes - linha 1 de 32 bits):
		- até 65.535 bytes;
	- identificação \(2 bytes - linha 2 de 32 bits):
		- número sequencial que identifica o fragmento;
	- flags \(3 bits - linha 2 de 32 bits)
		- bit DF: 'don't fragment', quando valor 1, não pode fragmentar o datagrama;
			- se um datagrama precisar ser fragmentado com a flag DF ativada, um roteador no caminho retorna uma mensagem de erro ICMP;
		- bit MF: 'more fragments', quando valor 0, é o último fragmento de uma seqência; 
	- deslocamento do fragmento \(13 bits - linha 2 de 32 bits);
		- número de ordem do fragmento;
	- tempo de vida \(1 byte - linha 3 de 32 bits):
		- carrega um valor com o número de saltos em roteadores que um datagrama pode passar pelo caminho, sendo decrementado a cada salto; se chegar a zero, o datagrama é descartado;
	- protocolo \(1 byte - linha 3 de 32 bits):
		- indica qual protocolo acima do protocolo IPv4 foi responsável pelo datagrama IPv4;
		- códigos mais comuns:
			- 1: ICMPv4
			- 2: IGMP
			- 3: GGP
			- 4: IPv4
			- 6: TCP
			- 8: EGP
			- 9: IGP
			- 17: UDP
			- 41: IPv6
			- 50: ESP \(IPsec)
			- 51: AH \(IPsec)
			- 89: OSPF
	- checksum do cabeçalho \(2 bytes - linha 3 de 32 bits):
		- o checksum sempre é recalculado quando há alteração no cabeçalho;
	- endereço IP da origem, na linha 4 de 32 bits;
	- endereço IP do destino, na linha 5 de 32 bits;
	- opções e preenchimento, a partir da linha 6 de 32 bits;

- **área de dados**:
	- até 65.535 bytes menos no mínimo 20 bytes do cabeçalho: 65.515 bytes;
	- tamanho típico: datagrama mínimo total 576 bytes menos 20 bytes: 556 bytes, para garantir suporte pelos equipamentos no caminho;

### Fragmentação de Datagrama IPv4
- pode ser feita pelo transmissor ou por qualquer roteador no caminho;
	- no caso do IPv6, apenas pelo transmissor;

- a fragmentação é realizada considerando que o datagrama IP, que já possui cabeçalhos e dados de um *segmento TCP*, por exemplo, em sua área de dados, precisa encapsular o segmento e seu próprio cabeçalho de modo a caber na *área de dados* de um *quadro*: **MTU - Maximum Transmission Unit**;


------------------------------------------------------------


# IPv6 PROTOCOL

### Diferenças entre IPv4 e IPv6
- tamanho do endereçamento;
- simplificação do cabeçalho IPv6, aumentando a eficiência dos saltos pelos roteadores, otimizando o tempo de leitura:
	- tamanho fixo do cabeçalho, em 40 bytes, excluindo o campo opções, dispensando a necessidade de cálculo de delimitação; opções são incluídas em cabeçalhos extras na área de dados;
	- não há checksum de cabeçalho, dispensando o tempo de recálculo de soma de verificação em qualquer alteração; IPv6 confia na verificação da camada de transporte nos segmentos TCP e datagramas UDP;
	- remoção do campo de fragmentação, cujas informações são incluídas em cabeçalhos extras;
- datagrama mínimo maior, aumentado de 576 bytes para 1.280 bytes;
- não há fragmentação de datagrama por roteadores no caminho:
	- hosts e roteadores determinam o tamanho do datagrama de forma dinâmica, trocando informações a respeito do menor MTU ao longo do caminho;


### Estrutura do Datagrama IPv6
- **cabeçalho**:
	- versão \(4 bits - linha 1 de 32 bits):
		- valor 6;
	- classe do tráfego \(traffic class)  \(linha 1 de 32 bits):
		- equivalente ao tipo de serviço: 1 byte:
			- *DSCP - serviços diferenciado* - 6 bits s;
			- *ECN - Explicit Congestion Notification*: 2 bits;
	- rótulo do fluxo \(flow label) \(20 bits - linha 1 de 32 bits); 
			- campo para definir qualidade de serviço, mas o campo não é utilizado;
	- tamanho dos dados \(playload length) \(2 bytes - linha 2 de 32 bits):
			- se *0*, é um *jumbograma*;
			- o tamanho da área de dados é fornecido: datagrama IPv6 subtraído o cabeçalho;
	- próximo cabeçalho \(next header) \(1 byte - linha 2 de 32 bits):
			- caso não existam cabeçalhos extras, esse campo que transporta o código do protocolo responsável pelo datagrama IP, sendo equivalente ao campo *protocolo* do cabeçalho IPv4;
				- note-se que o último cabeçalho quase sempre será o cabeçalho de um segmento TCP ou de um datagrama UDP;
			- caso exista cabeçalho extra na área de dados, um código indica o primeiro cabeçalho extra a seguir na área de dados, assim sucesivamente;
			- o código 59 indica que não há mais cabeçalhos nem área de dados a seguir;
	- limite de saltos \(hop limit) \(1 byte - linha 2 de 32 bits):
			- equivale ao TTL;
	- endereço IP de origem, da 3ª linha até a 6ª linha de 32 bits;
	- endereço IP de destino, da 7ª linha até a 10ª linha de 32 bits;

- **área de dados**:
	- até 65.535 bytes;
	- *jumbograma* até 4 GiB;
	- tamanho típico: datagrama mínimo total 1.280 bytes menos 40 bytes: 1.240 bytes;


------------------------------------------------------------


# IPsec


### IPsec
- enquanto TLS, SSL e SSH atuam na camada de aplicação, o IPsec atua na **camada de rede \(internet)**;

- tanto dados de usuário quanto cabeçalhos de segmento TCP e datagrama UDP são protegidos;

- usado em VPNs;

- garantia de:
	- autenticidade que certifica a origem;
	- integridade dos dados;
	- confidencialidade opcional com criptografia;

### Modos de Implementação
- **modo nativo**:
	- IPsec suportado por todos os componentes entre origem e destino;
	- IPsec atua no lugar do protocolo IP na camada de rede;
	- *AH - Authentication Header*: cabeçalho autenticado exceto em campos variáveis;
	- *ESP - Encapsulating Security Payload*: cabeçalho não autenticado;

- **BITS - Bump In The Stack**:
	- o cabeçalho IP é encapsulado na área de dados, e um novo cabeçalho IP é adicionado com o cabeçalho AH ou ESP;

- **BITW - Bump In The Wire**:
	- encapsulamento equivalente ao BITS, mas realizado entre roteadores no caminho;

### Modos de Operação
- **modo transporte**:
	- quando a comunicação é suportada pelos equipamentos nas duas extremidades da comunicação;

- **modo túnel**:
	- quando parte dos equipamentos no caminho não suporta nativamente o IPsec, como no modos de implementação BITS e BITW;

### IKE - Internet Key Exchange
- protocolo de troca de chaves, associação de segurança e definições de parâmetros, como algoritmo de criptografia que será utilizado;

- dividido em duas fases:
	- 1. associação de segurança IKE, mantida a mesma durante toda a conexão;
	- 2. associação de segurança IPsec, para AH ou ESP, refeita em lapsos de tempo durante a conexão;

### AH - Authentication Header
- garantia de proteção contra ataques do tipo *replay*, em que um pacote capturado é interceptado, modificado e retransmitido;
	- o número de sequência é único para cada datagrama até os números serem esgotados e a associação IKE de fase 2 ser refeita;

- integridade e autenticidade garantidas por soma de verificação;

- **estrutura do cabeçalho**:
	- campo próximo cabeçalho \(1 byte - linha 1 de 32 bits):
		- valor 6 para TCP no modo transporte;
		- valor 17 para UDP no modo transporte;
		- valor 4 pra IPv4 no modo túnel;
		- valor 41 para IPv6 no modo túnel;
	- comprimento do cabeçalho \(1 byte - linha 1 de 32 bits);
	- campo reservado  \(2 bytes - linha 1 de 32 bits);
	- índice de parâmetro de segurança \(SPI) \(4 bytes - linha 2 de 32 bits):
		- número da associação de segurança definido no IKE fase 2;
	- número de sequência \(4 bytes - linha 3 de 32 bits);
		- número de sequência é único para cada datagrama;
	- dados de autenticação \(ICV) \(variável - linha 4 de 32 bits);
		- valor de checksum de dados não variáveis;

### ESP - Encapsulating Security Payload
- subprotocolo que adiciona criptografia ao IPsec;

- **estrutura**:
	- índice de parâmetro de segurança \(SPI) \(4 bytes - linha 1 de 32 bits):
		- número da associação de segurança definido no IKE fase 2;
	- número de sequência \(4 bytes - linha 2 de 32 bits);
		- número de sequência é único para cada datagrama;
	- *área de dados*;
	- rodapé ESP \(trailer):
		- preenchimento;
		- comprimento do preenchimento:
			- tamanho variável, conforme algoritmo de criptografia;
		- próximo cabeçalho;
	- dados de autenticação \(ICV);


------------------------------------------------------------


# ICMP


### Internet Control Message Protocol
- protocolo que opera na camada de rede da pilha TCP/IP \(camada 3 do modelo OSI);

- protocolo para mensagens de diagnóstico, controle e erro;

- mensagens ICMP já vistas:
	- retorno de um roteador com bit DF \(Don't Fragment) ativado;
	- datagrama IPv6, que não suporta fragmentação, precisa ser fragmentado;
	- TTL excedido após o limite de saltos;
	- ping e traceroute;

### Mensagem ICMP
- estrutura apenas com cabeçalho IP e a Mensagem na área de dados, uma vez que o datagrama IP é gerado já na camada de rede;

- IPv4 com valor 1 no campo *protocolo* e valor 58 no campo *próximo cabeçalho*;

- a mensagem é estruturada com:
	- tipo da mensagem \(1 byte);
	- código da mensagem \(1 byte);
	- checksum \(2 bytes):
		- checksum IPv6 considera um pseudocabeçalho;
	- área de dados opcional, podendo conter os dados dos 8 primeiros bytes de cabeçalho de datagrama UDP ou segmento TCP que gerou a mensagem de erro;

### ping
- trabalha com mensagem ICMP com código de pedido de eco \(tipo 8, código 0) e recebe mensagem de resposta de eco \(tipo 0, código 0);
- o intervalo até a resposta é o **RTT - Round Trip-Time**;
- pelo valor TTL retornado no ping é possível saber o SO do destino, considerando:
	- Linux/Unix: 64;
	- Windows: 128;
	- AIX/Solaris/Cisco: 254 ou 255;

### traceroute
- trabalha com mensagem ICMP com código de pedido de eco para os roteadores ao longo de um caminho;
- o datagrama IP parte com IP do destino final, mas com TTL 1, e o primeiro roteador retorna uma mensagem ICMP de TTL excedido com seu respectivo IP; um novo datagrama parte com o TTL incrementado para atingir o segundo roteador e assim por diante até o destino;


------------------------------------------------------------


# ROUTING


### Roteamento Estático vs. Roteamento Dinâmico
- *estático* é o modo em que a *tabela de roteamento* é atualizada manualmente, a fim de definir o caminho entre uma origem e um destino;

- *dinâmico* é o modo que utiliza *protocolos de roteamento* para definir a *tabela de roteamento*;

### Vetor de Distância vs. Estado do Link
- *vetor de distância*: para definir o melhor caminho entre uma origem e um destino, são enviadas mensagens de protocolo de roteamento que avaliam o *vetor de distância*, com o critério de *menos saltos* \(custo por vetor), como ocorre com o *protocolo RIP*;

- *estado do enlace*: o melhor caminho é avaliado tendo como critério o *caminho mais rápido* \(que não necessariamente é mais curto), considerando parâmetros como latência, como ocorre com o *protocolo OSPF*;

------------------------------------------------------------

## RIP

### Routing Information Protocol
- protocolo de roteamento *interno* em um *AS - Autonomous System*;

- protocolo baseado em algoritmo de *vetor de distância*;

- versões:
	- RIPv1 - versão obsoleta sem autenticação e sem suporte a máscara de rede \(CIDR); 
	- RIPv2 versão para IPv4; 
	- RIPng versão para IPv6;

- apresenta limitações como *convergência lenta* e *loop de roteamento*;

### Temporizador e Mensagens
- *update timer*: mensagens enviadas para outros roteadores a cada 30 segundos com sua tabela de roteamento atualizada;

- *invalid timer*: 180 segundos sem receber atualizações de um roteador leva uma tabela a considerá-lo inválido, marcando usa distância \(custo) com valor 16 \(inacessível - 15 é o limite de saltos com o RIP);

- *flush timer*: 240 segundos sem receber atualizações de um roteador para que ele seja removido da tabela;

- **estrutura das mensagens**:
	- as mensagens RIPv2 são encapsuladas em datagramas UDP para a porta 520 no endereço multicast 224.0.0.9;

	- as mensagens RIPng são encapsuladas em datagramas UDP para a porta 521 no endereço multicast ff02::9; utiliza IPsec para autenticação;

------------------------------------------------------------

## EIGRP

### Enhanced Interior Gateway Routing Protocol
- protocolo de roteamento *interno* proprietário da Cisco;
- protocolo híbrido, com características de protocolo de vetor de distância e protocolo de estado do link;

------------------------------------------------------------

## OSPF

### Open Shortest Path First
- protocolo baseado no *estado do link*, utilizando ao algoritmo SPF de Dijkstra;

- mensagens encapsuladas diretamente no datagrama IP;

- versões:
	- OSPFv2 versão para IPv4; 
	- OSPFv3 versão para IPv6;

- convergência rápida, com no máximo 45 segundos;

### Topologia Hierárquica
- o protocolo OSPF permite seccionar um *AS - Autonomous System* em áreas, como se fossem subsistemas autônomos separados;
- roteadores internos numa determinada área conhecem apenas a topologia daquela área em seu *LSDB - Link-State DataBase*;
- permite utilizar roteadoress mais simples, de menor custo, dentro deas mesma área;

- a *área 0* é a rede que conecta as outras áreas através de seus *ABR - Area Border Routers* e do Backbone que os conecta;

### Temporizador e Mensagens
- *hello*: mensagem enviada a cada 10 segundos para os roteadores vizinhos;

- *dead interval*: 4 vezes o tempo de hello aguardando a resposta de um outro roteador da rede;

- *update SPF*: 5 segundos de espera sem resposta após o *dead interval*, o roteador é considerado inoperante pelo vizinho;

- *DBD - DataBase Description*: descrição reduzida da tabela de roteamento enviada através de um mensagem chamada *LSA - Link-State Announcement*;

- um roteador é eleito como *DR - Designated Router* para receber e retransmitir as mensagens de DBD em uma determinada área, através de um endereço de multicast;

- para obter mais detalhes sobre os links, cada roteador envia pedidos de informações completas de cada link atravésde uma mensagem *LSR - Link-State Request* e o roteador que tiver a informação completa responde com uma *LSU - Link-State Updatde* com uma *LSA - Link-State Announcement* completa respondida com uma confirmação *LSACK*;

------------------------------------------------------------

## BGP

### Border Gateway Protocol
- BGP-4 protocolo de roteamento *externo* ou *exterior*, estabelecendo a comunicação externa entre *sistemas autônomos*;

- utiliza *protocolo TCP*, na *porta 179*;

- protocolo de *vetor de caminho*:
	- dá preferência ao menor número de *sistemas autônomos* ao longo do caminho, diferente do número de saltos, considerado pelo vetor de distância;

### Boundary Router
- Roteador de Borda;

- o roteador que comunida um Sistema Autônomo com a Rede Mundial de Computadores é chamado *ASBR - Autonomous System Boundary Router*;

- em um sistema *multihoming*, com mais de uma conexão com o mundo externo, são utilizados váruios *ASBR - Autonomous System Boundary Routers*, que comunicam entre si:
	- através do protocolo iBGP \(internal);
	- através do protocolo eBGP \(external) com o mundo externo;

### Temporizador e Mensagens
- *open*: mensagem de abertura de comunicação de vizinhança; mensagem *keepalive* é enviada confirmando, quando não é negada;

- *keepalive*: mensagem enviada a cada 60 segundos aos vizinhos; *hold-down* padrão de 180 segundos para ser considerado inoperante;

- *update*: mensagem para atualização de rotas, acrescentando ou removendo;

- *notification*: mensagem de erro;

- *route refresh*: mensagem enviada em caso de atualização de políticas;































	