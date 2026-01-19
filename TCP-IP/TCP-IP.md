# INDEX

- [INTRODUCTION](#INTRODUCTION)





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

### Camada de Transporte
- **Protocolo TCP - Transmission Control Protocol**: *orientado à conexão*, com handshake e pacote numerados para ordenamento - *confiável*, com mecanismo de confirmação de entrega dos dados - maior *overhead*, complexidade e atraso;

- **Protocolo UDP - User Datagram Protocol**: mais simples e ágil;

- **PDU - Protocol Data Unit**: fracionamento da *MENSAGEM* e encapsulamento em:
	- **segmento TCP**;
	- **datagrama UDP**;

- identificação da *porta* de origem e destino;

- camada controlada pelo *Sistema Operacional*;

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
- camada de *Controle de Acesso ao Meio*;

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































	