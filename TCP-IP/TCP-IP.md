# INDEX

- [INTRODUCTION](#INTRODUCTION)
- [IPv4 ADDRESSING](#IPv4-ADDRESSING)
	- [NETWORK ADDRESS TRANSLATION](#NETWORK-ADDRESS-TRANSLATION)
	- [DHCPv4](#DHCPv4)
- [IPv6 ADDRESSING](#IPv6-ADDRESSING)
- [IPv4-IPv6 TRANSITIONING](#IPv4-IPv6-TRANSITIONING)
- [PORTS](#PORTS)
- [USER DATAGRAM PROTOCOL](#USER-DATAGRAM-PROTOCOL)


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

### Camada de Aplicação
- **Protocolos de Aplicação**: linguagens de comunicação utilizadas pelo software da máquina: 
	- FTP, HTTP, DNS, SMTP, IMAP, POP3, Telnet, SSH etc.;

- **PDU - Protocol Data Unit**: estrutura de dados da camada de aplicação é a **MENSAGEM**;

- camada controlada pelo *Software*;

- **endereços específicos**;

### Camada de Transporte
- **Protocolo TCP - Transmission Control Protocol**: *orientado à conexão*, com handshake e pacote numerados para ordenamento - *confiável*, com mecanismo de confirmação de entrega dos dados - maior *overhead*, complexidade e atraso;

- **Protocolo UDP - User Datagram Protocol**: mais simples e ágil;

- **PDU - Protocol Data Unit**: fracionamento da *MENSAGEM* e encapsulamento em:
	- **segmento TCP**;
	- **datagrama UDP**;

- identificação da *porta* de origem e destino;

- camada controlada pelo *Sistema Operacional*;

- **Endereçamento de portas**;

### Camada de Rede \(Internet)
- camada *entre-redes*;

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
- camada de *Controle de Acesso ao Meio*; camada de dados ou de interface com a rede;

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
	- 1. um nó cliente solicita a entrada na rede através de uma mensagem **DHCPDISCOVERY** em *broadcast*;
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
- cabeçalho com:
	- campo de porta de origem - 2 bytes;
	- campo de porta de destino - 2 bytes;
	- campo com o tamanho do datagrama - 2 bytes;
	- checksum - 2 bytes;

- área de dados com tamanho variável entre 0 e 65.527 bytes \(= 65.535 bytes - 8 bytes de cabeçalho);








































	