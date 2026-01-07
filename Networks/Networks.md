- [INTRODUCTION](#INTRODUCTION)
	- [NETWORK TYPES](#NETWORK-TYPES)
	- [INTERNET](#INTERNET)
	- [PROXY](#PROXY)

------------------------------------------------------------

# INTRODUCTION 


## NETWORK TYPES

### Nano-Network
- nanoredes que conectam equipamentos microscópicos;

### NFC: Near Field Communication
- redes para comunicação pŕoxima sem fio, com RFID: Radio-Frenquency Identification;

### BAN: Body Area Network
- redes que conectam equipamentos implantados ou afixados ao corpo humano;

### PAN and WPAN: \(Wireless) Personal Area Network
- redes de pequeno alcance, feito redes que conectam dispositivos bluetooth;

### NAN: Near-me Area Network
- modelo teórico de redes entre dispositivos próximos que não estejam necessariamente conectados a uma mesma rede, feito redes para anúncios de um mercado em smartphones de clientes presentes em dado momento;

### LAN: Local Area Network
- rede local mais comum;
- **WLAN** é a modalidade Wireless;
- **HAN** Home Area Network;
- **SAN** Storage Area Network:
	- rede local que funciona feito um barramento que conecta diversos dispositivos, como dispositivos de armazenamento, a um servidor;

### CAN: *campus* Area Network
- rede que conecta as diversas edificações, feito as edificações de um *campus* universitário;

### MAN: Metropolitan Area Network
- rede que conecta mais de uma rede em uma mesma cidade, feito a conexão de redes de filiais de uma mesma corporação;

### WAN: Wide Area Network
- versão de longo alcance de uma MAN, estendendo-se por mais de uma cidade;

### GAN: Global Area Network
- o mesmo que a rede mundial de computadores, *i. e.*, a própria **internet**;

### IAN: Internet Area Network
- caracteriza uma rede que possui elementos armazenados em cloud;

------------------------------------------------------------

## INTERNET

### Notion
- Rede Mundial de Computadores, sendo uma rede pública;

### AS: Autonomous System
- Sistema Autônomo é cada uma das redes que compõe a infraestrutura da internet;

### Internet Services
- correio eletrônico, email;
- VoIP \(Skype, WhatsApp etc.);
- videoconferência;
- jogo online;

### World-Wide Web: a Internet Service
- teia de conexão entre páginas hipertexto;
- **Spiders and Crawlers** são sistemas indexadores das páginas, feito portais de busca;
	- **Deep Web** é o conjunto de páginas não indexadas por mecanismos de busca;
	- **Dark Web** é uma camada de páginas com conteúdo ilegal na internet;

### Intranet
- rede privada que oferece serviços equivalentes à internet de forma limitada;

### Extranet
- acesso remoto a uma rede privada;
- um sistema pode ser acessado com login e senha a partir de páginas públicas;
- através de uma VPN, tal acesso se torna mais seguro;

------------------------------------------------------------

## PROXY

### Proxy Direto
- uso I: **servidor de cache** compartilhado:
	- está em desuso, pois não é possível fazer cache de dados criptografados, caso da maioria dos dados que trafegam pela internet atualmente;
- uso II: **mascaramento de cliente**:
	- mais frequentemente substituído por uma VPN, por segurança;
- uso III: **controle de acesso à internet**, *i. e.*, tráfego para fora:
	- uso mais comum atualmente, como um firewall;

### Proxy Reverso
- uso I: **controle de acesso** da internet para a rede local, como um firewall;
- uso II: **CDN: Content Delivery Network**:
	- rede de servidores espalhados pelo mundo que armazenam caches para aumento de eficiência de acesso a serviços na internet;
	- pode ter função de firewall;
- uso III: **Balanceador de Carga**: