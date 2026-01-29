# INDEX


- [INTRODUCTION](#INTRODUCTION)
	- [NETWORK TYPES](#NETWORK-TYPES)
	- [INTERNET](#INTERNET)
	- [CENTRALIZED AND DISTRIBUTED COMPUTING](#CENTRALIZED-AND-DISTRIBUTED-COMPUTING)
	- [PROXY](#PROXY)
	- [VPN](#VPN)
- [DIGITAL SYSTEM](#DIGITAL-SYSTEM)
	- [NUMERIC BASES](#NUMERIC-BASES)
	- [CONVERSIONS](#CONVERSIONS)
	- [BIT ORDERING](#BIT-ORDERING)
	- [BINARY WORDS](#BINARY-WORDS)
	- [UNITS OF MEASURE](#UNITS-OF-MEASURE)
- [DATA TRANSMISSION](#DATA-TRANSMISSION)
	- [TYPES](#TYPES)
	- [TRANSMISSION MEDIA](#TRANSMISSION-MEDIA)
	- [TRANSMISSION METHODS](#TRANSMISSION-METHODS)
- [PROTOCOLS](#PROTOCOLS)
	- [OSI MODEL](#OSI-MODEL)
	- [TCP/IP STACK](#TCP/IP-STACK)
- [TOPOLOGY](#TOPOLOGY)
- [CABLING](#CABLING)
- [NETWORK EQUIPMENT](#NETWORK-EQUIPMENT)
- [WIRELESS NETWORKS](#WIRELESS-NETWORKS)
	- [WIRELESS TYPES](#WIRELESS-TYPES)
	- [WI-FI NETWORKS](#WI-FI-NETWORKS)
	- [ELECTROMAGNETIC SPECTRUM](#ELECTROMAGNETIC-SPECTRUM)
	- [IEEE 802 STANDARDS](#IEEE-802-STANDARDS)
	- [WI-FI SECURITY](#WI-FI-SECURITY)
- [NETWORK VIRTUALIZATION](#NETWORK-VIRTUALIZATION)
- [SECURITY](#SECURITY)
	- [CIA](#CIA)
	- [CREDENTIALS](#CREDENTIALS)


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
- o mesmo que a rede mundial de computadores, *i. e.*, a própria [INTERNET](#INTERNET);

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

## CENTRALIZED AND DISTRIBUTED COMPUTING

### Computação Centralizada
- terminais conectados a um mainframe;
- telnet e ssh;

### Computação Distribuída
- poder de processamento nos próprios dispositivos, que se comportam como dispositivos autônomos;
	- **CLIENTE-SERVIDOR**: 
		- servidor web, 
		- servidor de arquivos, 
		- servidor de impressão,
		- **servidor de autenticação** e **serviço de diretório** em redes locais:
			- inclui-se gerenciamento de permissões,
			- acesso à internet,
			- acesso a impressoras etc..
	- **PEER-TO-PEER P2P**:
		- redes ponto-a-ponto em ambientes SOHO \(Small Office/Home Office):
			- sem serviço de autenticação ou serviço de diretório,
			- cada máquina gerencia o compartilhamento de seus diretórios;
		- redes ponto-a-ponto para compartilhamento de arquivos na internet:
			- compartilhamento de blocos segmentados de arquivos por peers na internet;

### Redes Frontend-Backend
- tipo de rede cliente-servidor utilizado por aplicações web;

------------------------------------------------------------

## PROXY

### Proxy Direto
- uso I: **servidor de cache** compartilhado:
	- está em desuso, pois não é possível fazer cache de dados criptografados, caso da maioria dos dados que trafegam pela internet atualmente;
- uso II: **mascaramento de cliente**:
	- mais frequentemente substituído por uma VPN, por segurança;
- uso III: **controle de acesso à internet**, *i. e.*, tráfego para a internet:
	- uso mais comum atualmente, como um firewall;

### Proxy Reverso
- uso I: **controle de acesso** da internet para a rede local, como um firewall;
- uso II: **CDN: Content Delivery Network**:
	- rede de servidores espalhados pelo mundo que armazenam caches para aumento de eficiência de acesso a serviços na internet;
	- pode ter função de firewall, filtrando acessos;
- uso III: **Balanceador de Carga**:
	- rodízio de tráfego de acesso a servidores;

------------------------------------------------------------

## VPN

### Meaning
- Virtual Private Network;
- a VPN estabelece um 'túnel' criptografados para o tráfego de dados;

### site-to-site
- VPN para acesso a rede privada, servindo de caminho para uma 'Extranet', por exemplo;

### host-to-host
- VPN que entrega um serviço semelhante a um proxy para mascaramento de cliente, com a diferença que a VPN é obrigatoriamente criptografada;
- este tipo de serviço também provê uma camada anonimidade;

### software
- **VPN SSL** plugin para navegador web, com protocolo **TLS**, na camada 6 do modelo OSI \(apresentação);
- **VPN IPsec** software adicional para site-to-site ou servidor VPN host-to-host, com protocolo **IPsec**, na camada 3 do modelo OSI \(rede);

------------------------------------------------------------


# DIGITAL SYSTEM 


## NUMERIC BASES

### Decimal Base 
- através da notação de base 10, pode-se considerar a potência como a quantidade de casas decimais:
	- a × 10⁰ = 'a' sem zeros = unidade;
	- a × 10¹ = 'a' com 1 zero = dezena;
	- a × 10² = 'a' com 2 zeros = dezena; etc..

- representação: \(10)₁₀ ou 10d ou 10

- considerar o número **1234**:

| casa decimal 	| operação	| equivalência 	|
|:--------------|:---------:|--------------:|
| I.	4		| 4 × 10⁰	| 4				|
| II.	3		| 3 × 10¹	| 30			|
| III.	2		| 2 × 10²	| 200			|
| IV.	1		| 1 × 10³	| 1000			|
| 				| **TOTAL**	| 1234			|

### Binary Base 
- conversão de notação de base 2:
	- a × 2⁰;
	- a × 2¹;
	- a × 2²;
	- a × 2³; etc..

- representação: \(10)₂ ou 10b ou $10 \(que equivale a 2)

- considerar o número **1100**:

| posição 	| operação			| equivalência 	|
|:----------|:-----------------:|--------------:|
| I.	0	| 0 × 2⁰ = 0 × 1	| 0				|
| II.	0	| 0 × 2¹ = 0 × 2	| 0				|
| III.	1	| 1 × 2² = 1 × 4	| 4				|
| IV.	1	| 1 × 2³ = 1 × 8	| 8				|
| 			| **TOTAL DECIMAL**	| 12			|

### Hexadecimal Base
- representação de 0 a 16;
- cada número equivale a 4 bits;
- a partir de 9 os algorismos são representados pelas letras de A a F;

- representação: \(10)₁₆ ou 10h ou 0x10 \(que equivale a 16)

| decimal 	| binário			| hexadecimal 	|
|:---------:|:-----------------:|:-------------:|
| 0			| 0000				| 0				|
| 1			| 0001				| 1				|
| 2			| 0010				| 2				|
| 3			| 0011				| 3				|
| 4			| 0100				| 4				|
| 5			| 0101				| 5				|
| 6			| 0110				| 6				|
| 7			| 0111				| 7				|
| 8			| 1000				| 8				|
| 9			| 1001				| 9				|
| 10		| 1010				| A				|
| 11		| 1011				| B				|
| 12		| 1100				| C				|
| 13		| 1101				| D				|
| 14		| 1110				| E				|
| 15		| 1111				| F				|

- **padding** é o uso e zeros à esquerda para representar a largura de estrutura de dados;

### Overflow
- é o evento em que um dado extrapola o tamanho das unidades menores da estrutura de dados a ser transportada ou armazenada;
- **desdobramentos:**
	- *fragmentação de dados* é a divisão de um dado longo a ser transportado em pacotes que formam unidades menores, como estruturas de 4 bits;
	- *erro de overflow*;
	- *desconsiderar bits excedentes*;
	- *somar os bits excedentes aos demais*, técnica usada em checksum;

------------------------------------------------------------

## CONVERSIONS

### Binário para Decimal
- considerar cada casa da direita para a esquerda como uma potência de 2 e multiplicar pelo 1 ou 0 que a ocupa, somando os resultados;
- conversão em tabela do dígito 8 bits **10101100**:

| posição 	| potência de 2 	| total		 	|
|:----------|:-----------------:|--------------:|
| I.	0	| 0 × 2⁰ = 0 × 1	| 0				|
| II.	0	| 0 × 2¹ = 0 × 2	| 0				|
| III.	1	| 1 × 2² = 1 × 4	| 4				|
| IV.	1	| 1 × 2³ = 1 × 8	| 8				|
| V.	0	| 0 × 2⁴ = 0 × 16	| 0				|
| VI.	1	| 1 × 2⁵ = 1 × 32	| 32			|
| VII.	0	| 0 × 2⁶ = 0 × 64	| 0				|
| VIII.	1	| 1 × 2⁷ = 1 × 128	| 128			|
| 			| **TOTAL DECIMAL**	| \(172)₁₀		|

- considerar o  dígito de 12 bits **110000010111**:
- ``` 2048	 1024	 512	 256	 128	 64		 32		 16		 8		 4		 2		 1 ```
- ``` 1		 1		 0		 0		 0		 0		 0		 1		 0		 1		 1		 1 ```
- somar apenas bits em 1 e ignorar os 0 \(nulos): ``` 2048 + 1024 + 16 + 4 + 2 + 1 = (3095)₁₀ ```

### Decimal para Binário
- potências de 2 são binários inteiros, em que a casa do binário equevalente a ele é 1 e as outras são 0;
- para os outros valores:
	- passo I: listar as potências de 2 até aquela imediatamente menor ao número decimal e ocupar o bit equivalente com 1; exemplo **79**:
		- ``` 64		 32		 16		 8		 4		 2		 1 ```
		- ``` 1		 	 ?		 ?		 ?		 ?		 ?		 ? ```
	- passo II: 79 - 64 = 15; ainda restam 15, portanto, ocupar com o dígito 1 o bit equivalente à potência de 2 imediatamente menor que **15**, *i. e.*, **8**:
		- ``` 64		 32		 16		 8		 4		 2		 1 ```
		- ``` 1		 	 0		 0		 1		 ?		 ?		 ? ```
	- passo III: 15 - 8 = 7; ainda restam 7:
		- ``` 64		 32		 16		 8		 4		 2		 1 ```
		- ``` 1		 	 0		 0		 1		 1		 ?		 ? ```
	- passo IV: 7 - 4 = 3 = 2 + 1:
		- ``` 64		 32		 16		 8		 4		 2		 1 ```
		- ``` 1		 	 0		 0		 1		 1		 1		 1 ```

### Binário para Hexadecimal
- separar o binário em estruturas de bloco de 4 bits;
- considerar as potências de 2 para cada casa do bloco: ``` 8, 4, 2, 1 ```:

		- ``` 8		 4		 2		 1 	```
		- ``` 1		 1		 1		 0	```

		- o binário do bloco acima equivale a \(12)₁₀, *i. e.*, \(C)₁₆;

- multiplicar pelo 1 ou 0 que as ocupa, somando os resultados de cada bloco;
- considerar para cada bloco: 10 = A, 11 = B, 12 = C, 13 = D, 14 = E, 15 = F;

### Hexadecimal para Binário
- inverter a estrutura de blocos 4 bits; 
- conversão do dígito 12 bits **4A3**:
	- listar as potências de 2 de cada bloco e seguir os passos da conversão decimal para cada um deles:
		- ``` 8		 4		 2		 1 		| 8		 4		 2		 1 		| 8		 4		 2		 1 ```
		- ``` 0		 1		 0		 0		| 1		 0		 1		 0		| 0		 0		 1		 1 ```

### Hexadecimal para Decimal
- seguir os passos da conversão de binários, utilizando porém a base 16;

### Decimal para Hexadecimal
- dividir sucecivamente o decimal por 16 até que a parte inteira se torne zero;
- multiplicar os valores decimais após a vírgula dos resultados parciais por 16;
- a quantidade de operações para tanto é a quantidade de dígitos do hexadecimal final;
- os resultados já convertidos em hexadecimal compõem o algarismo final, sendo o primeiro resultado o primeiro da direita para a esquerda;

- exemplo **9437**:
	- 9437 / 16 = 589,8125	| 0,8125 × 16 = 13 = D
	- 589 / 16 = 35,8125	| 0,8125 × 16 = 13 = D
	- 36 / 16 = 2,25		| 0,25 × 16 = 4
	- 2 / 16 = 0,125		| 0,215 × 16 = 2
	- resultado: **24DD**;

- outra forma, utilizando processos mais simples, pode-se converter decimal para binário e binário para hex;

------------------------------------------------------------

## BIT ORDERING

### Ordenação de bits
- **Most Significant Bit - msb**: o bit mais significativo é aquele que se posiciona na maior potência de 2 do binário, *i. e.*, à esquerda do bináro;
- **Least Significant Bit - lsb**: o bit menos significativo é o que se posiciona na potência 2⁰, à direita do binário;

### Sistemas de Ordenação
- **lsb0**: sistema que identifica os bits como: b0, b1, b2, b3 etc. no mesmo sentido das potências de 2, da direita para a esquerda; 
	- os números das posições, nesse caso, coincidem com as potências, pois parte do bit menos significativo;
	- o sistema *lsb0* é o mais utilizado em *eletrônica digital*;
- **msb0**: sistema que idenficia os bits da forma inversa, a partir do bit mais significativo;
	- o sistema *msb0* é o mais utilizado em *pilha de protocolo TCP/IP*;

------------------------------------------------------------

## BINARY WORDS

### Nibble
- palavra binária com 4 bits;
	- variações possíveis: 2⁴ = 16, de 0 a 15;

### Byte
- palavra binária com 8 bits, também chamado de **octeto**;
	- variações possíveis: 2⁸ = 256, de 0 a 255;

### Word
- palavra binária com 16 bits;
	- variações possíveis: 2¹⁶ = 65.536, de 0 a 65.535;

### Double Word - DWord
- palavra binária com 32 bits;
	- variações possíveis: 2³² = 4.294.967.296;

### Quad Word - QWord
- palavra binária com 64 bits;
	- números possíveis: 2⁶⁴ = 18.446.744.073.709.551.616;

### Sistemas de Ordenação de Bytes
- **Little Endian**: sistema que identifica os bytes como: B0, B1, B2, B3 etc., da direita para a esquerda; 
	- o sistema *Little Endian* é o mais utilizado em relação a *processadores x86*;
- **Big Endian**: sistema que idenficia os bytes da esquerda para a direita;
	- o sistema *Big Endian* é o mais utilizado em *redes*;

------------------------------------------------------------

## UNITS OF MEASURE

### Unidades de Grandeza Decimais
- **kilo** K 10³;
- **mega** M 10⁶;
- **giga** G 10⁹;
- **tera** T 10¹²;
- **peta** P 10¹⁵;
- **exa** E 10¹⁸;
- **zeta** Z 10²¹;
- **yotta** Y 10²⁴;

### Unidades de Grandeza Binárias
- **kibi** Ki 2¹⁰ = 1024¹ = 1.024;
- **mebi** Mi 2²⁰ = 1024² = 1.048.576;
- **gibi** Gi 2³⁰ = 1024³ = 1.073.741.824;
- **tebi** Ti 2⁴⁰ = 1024⁴ = 1.099.511.627.776;
- **pebi** Pi 2⁵⁰ = 1024⁵ = 1.125.899.906.842.624;
- **exbi** Ei 2⁶⁰ = 1024⁶ = 1.152.921.504.606.846.976;
- **zebi** Zi 2⁷⁰ = 1024⁷ = 1.180.591.620.717.411.303.424;
- **yobi** Yi 2⁸⁰ = 1024⁸ = 1.208.925.819.614.629.174.706.176;

¹²³⁴⁵⁶⁷⁸⁹⁰₀₁₂₃₄₅₆₇₈₉
------------------------------------------------------------


# DATA TRANSMISSION


## TYPES

### Simplex - SX
- transmissão em uma única direção, de um **transmissor - Tx** para um **receptor Rx**;

### Half-duplex - HDX
- transmissão bidirecional de dados do transmissor ao receptor em alternância, não simultânea;
- **exemplos**: walkie-talkie, radio, rede com cabo coaxial, redes de par trançado Fast Ethernet, redes Wi-Fi, sistemas antigos de fibra óptica;

### Full-duplex - FDX
- transmissão bidirecional simultânea;
- implementações: 
	- com **dois canais** SX \(simplex):
		- para duas conexões de fibra óptica;
		- em redes de par trançado com um par para transmissão e outro para transmissão;
	- com **um canal**:
		- implementado com **multiplexação** por divisão de comprimento de onda em um canal de fibra óptica;
		- implementado de forma **híbrida** com par trançado de Gbit/s Ethernet e superiores, com transformador híbrido de casamento de impedância, reduzindo um sistema de 4 fios para um sistema de 2 fios;

------------------------------------------------------------

## TRANSMISSION MEDIA

### Meios e Canais de Transmissão de dados
- os *meios* de transmissão de dados, como *ondas eletromagnéticas*, cabos metálicos com *impulsos elétricos* ou fibra óptica com *pulsos luminosos*, podem ser fracionados em várias *frequências*, e cada frequência utilizada é um **canal** de transmissão de dados;

- um meio fracionado em vários canais é um meio **multicanal** ou **banda larga**;
- um meio que usa apenas um canal, é um meio **unicanal** ou **banda base**;

### Conexão Ponto-a-ponto
- uma conexão dedicada, conectando diretamente dois dispositivos, permitindo o maior desempenho possível;
- um **switch**, dispositivo comutador, realiza chaveamentos que permitem conexões diretas entre dispositivos em uma rede local, em topologia estrela;

### Barramento
- um canal compartilhado para conexões, usando dispositivos de **controle de acesso ao meio**;
- em conexão por barramento há redução de desempenho em relação à conexão *ponto-a-ponto*;
- numa conexão por barramento, todos os dados são enviados a todos os dispositivos, contudo só a máquina identificada no campo de enderaçamento do dado vai capturar o dado;
- apenas um domínio de broadcast e um domínio de colisão;

### Controle de Acesso ao Meio
- mecanismos de controle do uso do meio pelos dispositivos conectados:

- **CONTENÇÃO**:
	- algoritmo probabilístico CSMA/CD \(Carrier-Sense Multiple Access with Collision Detection):
		- Detecção de Colisão:
			- um dispositivo detecta a colisão de uso do meio por outro dispositivo e aguarda um período de tempo aleatório para tentar novamente;
		- *usado em redes Ethernet* de topologia linear, em barramento;
	- algoritmo probabilístico CSMA/CA \(Carrier-Sense Multiple Access with Collision Avoidance):
		- Evasão de Colisão;
			- um dispositivo aguarda o canal de transmissão estar livre para iniciar uma transmissão, evitando a colisão;
		- *usado em redes Wi-Fi*;

- **TOKEN PASSING \(passagem de ficha)**:
	- algoritmo determinístico, sendo possível prever quando terá acesso ao meio;
	- uma *ficha* vazia habilita a transmissão de dados de um dispositivo que a aguarda, o qual a "preenche" com os dados a serem transmitidos;
	- uma *ficha* ocupada está transmitindo dados de outros dispositivos conectados à rede;

- **POLLING \(varredura)**:
	- algoritmo determinístico, sendo possível prever quando terá acesso ao meio;
	- método que utiliza um elemento centralizador, **arbitrador**, que faz uma varredura na rede ordenando os dispositivos que solicitam transmissão de dados;
	- um elemento arbitrador é utilizado em redes Wi-Fi quando o QoS está ativado;
	- quando não há um elemento arbitrador, os pŕoprios dispositivos definem a lista de acesso ao meio;

------------------------------------------------------------

## TRANSMISSION METHODS

### Transmissão em Série
- transmissão padrão em um único canal, com dados sendo transmitidos um por vez;

### Transmissão em Paralelo
- transmissão que utiliza meios multicanal, com mais de um dado sendo transmitido ao mesmo tempo, utilizando mais cabos ou mais canais de radiofrequência;

### Multiplexação

- **\(SDM) Space-Division Multiplexing - Space-Division Multiple Access**:
	- *Multiplexação por Divisão Espacial*, em que é usada uma conexão em paralelo através de canais separados; 
	- é utilizada com **switch** em conexões cabeadas de topologia estrela;
	- redes sem fio com **MIMO - Multiple Input, Multiple Output**, com antenas diversas para prover mais de um fluxo espacial;

- **\(TDM) Time-Division Multiplexing - Time-Division Multiple Access**:
	- *Multiplexação por Divisão de Tempo*, utilizando uma alternância acelerada na transmissão de dados, causando a sensação de simultaneidade;
	- é a técnica mais popular de transmissão de dados; 

- **\(FDM) Frequency-Division Multiplexing - Frequency-Division Multiple Access**:
	- *Multiplexação por Divisão de Frequência*, usada em TV e Rádio analógicos;
	- *Orthogonal Frequency-Division Multiplexing \(OFDM)* é uma técnica que permide subtividir os canais em subcanais em uma FDM, para transmitir dados em paralelo através de um canal, usada em TV Digital e Wi-Fi;

- **\(CDM) Code-Division Multiplexing - Code-Division Multiple Access**:
	- *Multiplexação por Divisão de Código* utiliza uma *faixa de frequência alongada \(spread spectrum)*, criando fluxos de dados "embaralhados", mas codificados, de modo a identificar o emissor e o destinatário que compartilham as chaves de um mesmo código;
	- provê uma camada de seguraça extra através da codificação dos dados;

- **\(WDM) Wavelength-Division Multiplexing - Wavelength-Division Multiple Access**:
	- *Multiplexação por Divisão de Comprimento de Onda* é utilizada por um tipo de fibra óptica específica *NZ-DSF*;
	- permite a utilização de conexão bidirecional com fibra óptica;

### Sincronia
- em uma transmissão em série, torna-se necessário identificar o tempo de duração do sinal de cada bit;
- a *sincronia* é a técnica usada para que a ponta receptora consiga identificar e separar os bits recebidos;
- técnicas de sincronia de dados:
	- **transmissão em série síncrona** ou sincronia fora de banda:
		- um canal paralelo, *canal de controle*, transmite o sinal de sincronismo chamado *clock*;
		- circuito mais complexo e mais caro;
		- maior eficiência na transmissão de dados, *i. e.*, mais dados podem ser transmitidos em um intervalo de tempo;
	- **transmissão em série assíncrona** ou sincronia em banda:
		- no mesmo canal de dados, o emissor inicia a transmissão de dado com uma **palavra de sincronismo**: 
			- **preâmbulo**, em rede Ethernet; 
			- **start bit**, em porta serial RS-232; 
			- **Sync**, em conexões USB;
		- circuito mais simples e mais barato;
		- menor eficiência na transmissão de dados, *i. e.*, menos dados podem ser transmitidos em um intervalo de tempo, pois parte da banda é usada para os sinais de controle;

- **Quadro Ethernet**

| Sincronismo 		| Cabeçalho 						| Dados	| Rodapé 	|
|:-----------------:|:---------------------------------:|:-----:|:---------:|
| Preâmbulo - SDF 	| Destino - Origem - Comprimento 	| Dados | FCS 		|

- no quadro Ethernet acima, o Preâmbulo é uma sequência de 7 bytes, alternando 0 e 1 para indicar o clock, e o SDF \(Start Frame Delimiter) indica o final do sincronismo com 1 byte, cuja estrutura é ``` 10101011 ```;

### Codificação
- codificar os dados permite criar *sistema de sincronia* entre transmissor e receptor e evitar **baseline wandering** \(desvio da linha de base), impedindo sequências longas de 0 e 1;
- tipos de codificação:
	- **NRZ \(Non Return to Zero)**: codificação padrão, baseada em alternância de tensão \(0v/5v ou -3v/+3v) ou alternância de sinal luminoso;
		- não evita *baseline wandering*;
	- **NRZI \(Non Return to Zero Iverted)**: o sinal 1 inverte o código enquanto o sinal 0 mantém;
		- não evita *baseline wandering*;
	- **Manchester**: inverte o sinal a cada bit, evitando *baseline wandering*, mas dobrando o *baud rate* \(grandeza de número de elementos sinalizadores por segundo), reduzindo pela metade a taxa de bit, perdendo a eficiência em 50%;
	- **4B/5B ou 8B/10B**: mais usada atualmente, convertendo pacotes de 4 bits em pacotes de 5 bits ou 8 bits em 10 bits; os bits a mais podem servir de sinal de sincronia;

### Modulação
- é a conversão do código no sinal analógico compatível com o meio a ser utilizado;
- tipos de modulação:
	- **PAM2 \(Pulse Amplitude Modulation 2)**: para NRZ, considera-se a variação de amplitude da onda quadrática de variação de tensão, como por exemplo: -5v = 0 | +5v = 1;
		- taxa de transferência 100Mbd \(megabauds em Baud Rate, grandeza de número de elementos sinalizadores por segundo) para 100Mbit/s;
	- **PAM4 \(Pulse Amplitude Modulation 4)**: PAM2 convertido em 4 níveis de tensão para combinações de dois bits, como por exemplo: -5v = 00 | -2,5v = 01 | +2,5v = 10 | +5v = 11;
		- taxa de transferência 100Mbd \(megabauds em Baud Rate, grandeza de número de elementos sinalizadores por segundo) para 200Mbit/s, sendo mais eficiente;

### Estrutura do Pacote de Dados
- basicamente: 

| *cabeçalho* | *área de dados* | *rodapé* |

	- cabeçalho: contém o endereçamento de origem e destino do pacote; bits de controle;
	- área de dados: o dado propriamente;
	- rodapé: estrutura opcional; bits de controle;

- *overhead* \(desperdício): a maior parte dos dados é dado de usuário, mas além deles há os dados de controle;

### Tipos de Pacote
- **quadro**: pacote de dados no meio físico;
- **célula**: pacote de dados no meio físico com tamanho fixo;
- **datagrama**: pacote de dados sem confirmação de recebimento;
- **segmento**;

### Tipos de Mensagem
- **Unicast**: mensagem para um único destinatário, mais comum;
- **Broadcast**: mensagem destinada a todos os dispositivos na rede;
- **Multicast**: mensagem para um grupo determinado de dispositivos na rede;
- **Anycast**: mensagem destinada a um dispositivo mais próximo de determinado tipo para atender determinada demanda;

### Confirmação de Entrega de Dado
- um pacote é enviado ao destino buscando o retorno de um **ACK \(Acknowledge)** que confirma a entrega;

- o pacote enviado inicialmente considera um temporizador para mensurar o tempo de resposta com o retorno do *ACK*, verificando se há erro de *timeout*;

- os protocolos que utilizam a confirmação de recebimento de dados são chamados de **protocolos confiáveis**, com maior **overhead**, feito o protocolo *TCP*, em oposição aos protocolos não confiáveis com menor complexidade \(menor overhead), feito o *UDP*;

- **NACK \(Negative Acknowledge)** é o mecanismo de envio de pacote de notificação de não recebimento de um pacote esperado;

### Handshake \(Conexão)
- pacote de controle que solicita o estabalecimento de conexão;

- protocolos que utilizam esse mecanismo são **Protocolos Orientados a Conexão**, com pacotes sempre enviados em ordem, feito o protocolo *TCP*, em oposição a protocolos sem conexão **Conectionless**, com pacotes enviados fora de ordem, feito o *UDP*;

### Detecção de Erros
- **Paridade**: um bit de paridade é adicionado a fim de que o total de bits de um pacote seja par; 1 para um pacote com número ímpar de bits 1 e 0 para um pacote que já tenha um número par de bits 1;
- **Repetição**: o mesmo pacote é enviado mais de uma vez, normalmente 3 vezes, para serem conferidos pelo receptor que, pela comparação dos pacotes, pode ou não solicitar uma retransmissão;
- **Checksum \(Soma de Verificação)**: um algoritmo de soma de todos os dados é utilizado para anexar um código ao rodapé do pacote que serve de verificação pelo receptor, que usa o mesmo algoritmo para checar o pacote recebido;
- **CRC \(Ciclical Redundancy Check)**: um processo similar ao Checksum é feito, mas utilizando a divisão por um polinômio, resultando um *FCS \(Frame Check Sequence) formando uma sequência de bits com o total de bits do polinômio menos um bit; o FCS é acrescido ao dado; é o mecanismo mais utilizado;

### Correção de Erros
- algoritmo que é capaz de detectar e corrigir o erro pode ser cjamado de:
	- **ECC \(Error Correction Code)**: para memórias e sistemas de armazenamento;
	- **FEC \(Forward Error Correction)**: para sitemas de transmissão de dados e telecomunicações;
- ao ECC e ao FEC são adicionados bits de redundância que permitem a recuperação do dado original em caso de corrupção;
- quanto maior a redundância, maior o potencial de correção de erros;

### Comutação de Pacotes
- tipo mais comum de rede que opera no esquema de melhor esforço;
- principais características:
	- pode haver mais de um caminho entre a origem e o destino; não sabemos de antemão qual
caminho será usado; o caminho pode variar a cada pacote de dados;
	- pacotes podem ser recebidos fora de ordem;
	- não há garantia de velocidade;
	- não há garantia de latência; não sabemos quando o pacote de dados chegará ao destino; pode haver atraso na entrega de pacotes de dados;
	- recursos não são previamente alocados, *i. e.*, são alocados dinamicamente;
 	- pode haver perda de pacotes de dados;
	- normalmente não há garantia de entrega dos pacotes de dados;
- sistemas de confirmação de entrega e qualidade de serviço \(QoS) podem mitigar alguns destes pontos;

### Comutação de Circuito
- tipo oriundo do sistema telefônico tradicional, é utilizado por redes de longo alcance \(WAN) oferecidas por operadoras de telefonia, usando tecnologias como *Frame Relay* e *ATM*;
- principais características:
	- monta-se um circuito entre a origem e o destino que é sempre o mesmo, sendo sempre usado o mesmo caminho entre a origem e o destino;
	- pacotes são sempre recebidos em ordem; 
	- há garantia de velocidade;
	- há garantia de latência, permitindo saber quando o pacote de dados chegará ao destino;
	- funcionamento determinístico;
	- recursos são previamente alocados;
	- não há perda de pacotes de dados;
	- há garantia de entrega dos pacotes de dados;

- atualmente, operadoras de telefonia criam redes por comutação de circuito em cima de uma rede por comutação de pacotes, usando uma técnica chamada circuito virtual \(**VC, Virtual Circuit**):
	- *PVC \(Permanent Virtual Circuit)*: circuito permanente, permanece montado mesmo quando dados não estão sendo transmitidos;
	- *SVC \(Switched Virtual Circuit)*: circuito temporário, montado somente quando há dados a serem transmitidos; serviço mais barato;

### Taxa de Transferência
- é a velocidade com que os dados trafegam por um canal;
- a taxa é dada na base 10 para bit/s ou frequentemente na base 10 para B/s, podendo eventualmente ser na base 2 para esse último caso;

### Largura de Banda
- **Banda Base** é o sistema de uso da frequência máxima de operação de um meio pelo canal, sendo mais frequentemente usado;
- **Banda Larga** ou *multicanal* é o sistema em que os canais fracionam a banda máxima do meio;

### Latência
- tempo médio, medido em milisegundos, que um pacote leva para ser transmitido na rede;
- **RTT \(Round-Trip Time)** é o tempo de ida e volta de um pacote numa rede, utilizado no **ping**;

### Melhor Esforço
- técnica empregada em **redes por comutação de pacotes**, em que não há 
	- garantia de entrega de um dado;
	- garantia de desempenho;
	- garantia de latência;
	- garantia de ordem de entrega;
- pode-se habilitar o **ACK \(Acknowledge)**;
- pode-se implementar **QoS \(Quality of Service)**;

### QoS - Quality of Service
- a *qualidade do serviço* indica os parâmetros de funcionamento de uma rede para prioridade de determinados pacotes;
- parâmetros de QoS em contrato *SLA - Service Level Agreement*:
	- Desempenho: largura de banda disponível e porcentagem de tempo dessa disponibilidade;
	- Classes de Tráfego: marcação de pacotes de acordo com a classe de prioridade, ex.: vídeo-conferência, comunicação em tempo real, dados etc.;
	- Confiabilidade: percentual de erros possíveis;
	- Disponibilidade: tempo de disponibilidade da rede;
	- Segurança;


------------------------------------------------------------


# PROTOCOLS


## OSI MODEL

### Estrutura do Modelo
- modelo de 7 camadas \(Layers) por que um dado passa após sair do **aplicativo** e antes de chegar ao **meio** em que será transmitido;
- cada camada gera uma **Protocol Data Unit \(PDU)** que é repassado para a camada imediatamente inferior;
- na camada inferior, a *PDU* é inserido na *área de dados* do pacote recebido da camada superior, resultando em um cabeçalho específico;
- **Service Access Point \(SAP)** é o sistema de endereçamento no cabeçalho de cada *PDU* que direciona o pacote ao protocolo correto numa camada superior;

- **CAMADAS**:

	- 7. **Aplicação**:
		- camada que identifica os **Protocolos de Aplicação**;
		- gera uma **Mensagem** com os dados e os comandos sobre o que fazer com os dados;

	- 6. **Apresentação**:
		- camada que identifica ou modifica **Formato dos Dados**, resolvendo problemas de representação de informação existente entre *sistemas heterogêneos interconectados;
		- camada relacionada à *sintaxe* e à *semântica*;
		- responsável por comprimir ou descomprimir os dados;
		- responsável por criptografar dados, com o protocolo **TLS - Transport Layer Security** \(ou *SSL - Secure Socket Layer*, versão obsoleta antecessora ao *TSL*);
		- aqui, a *mensagem* ainda não está fracionada em pacotes menores;

	- 5. **Sessão**:
		- camada que cria uma *sessão* de conexão que, em caso de interrupção, a transferência é retomada a partir desse *sessão*;
		- *mensagem* ainda íntegra;

	- 4. **Transporte**:
		- camada intermediária entre as camadas de alto nível \(5-7) e as camadas de baixo nível \(1-3);
		- camada em que se identificam origem e destino de dados;
		- nesta camada, inicia-se o **fracionamento em pacotes menores**;
		- definem-se *segmentos TCP* ou *datagramas UDP*;
		- camada responsável também pelo ordenamento e pela integridade dos dados, com mecanismos como a numeração e a *soma de verificação*;

	- 3. **Rede \(*Internet*)**:
		- camada de roteamento de dados;
		- camada responsável pelo endereçamento lógico dos pacotes;
		- camada de operação de **roteadores** e **switches** direcionando os dados, normalmente com os protocolos IPv4, IPv6, IPsec ou ICMP;
		- camada responsável por gerar PDUs chamadas *datagramas IP*;

	- 2. **Link de Dados \(Enlace de Dados)**:
		- camada de operação de **switches**. que é responsável por inserir os *datagramas IP* em PDUs chamadas *quadros* ou *células*;
 		- camada responsável por gerar PDUs chamadas *quadros*;
		- camada responsável por identificar os *endereços físicos*, **MAC - Medium Access Control** de origem e destino dos pacotes;

	- 1. **Física**:
		- camada de operação dos **hubs**;
		- camada que opera com protocolos de transmissão de dados em nível de bits;
		- camada responsável pela modulação e demodulação dos dados conforme o meio a ser usado;

------------------------------------------------------------

## TCP/IP STACK

### Estrutura em 4 camadas
- na pilha TCP/IP, as camadas 5, 6 e 7 do modelo OSI foram fundidas um uma única camada *Aplicação*;
- as camadas 1 e 2 são abordadas tradicionalmente como uma camada chamada **Interface com a rede**;
- a *Interface com a rede* é definida pela arquitetura de redes, e não pela pilha TCP/IP; 

### Dinâmica de encapsulamento de dado
- **Camada Aplicação**: gera uma PDU com um comando e os dados a serem transmitidos chamada **Mensagem**, acrescidos de 
	- **Número de Porta** de origem e destino, indicando o **Protocolo de Aplicação**:
		- protocolo de transporte a usar: **TCP** ou **UDP**;

- **Camada Transporte**:
- a *mensagem* é encaminhada para a *Camada Transporte* como um fluxo de dados, sendo fracionada byte a byte, para caber no espaço da PDU de transporte;
	- se **TCP**, a camada Transporte gera uma PDU chamada **Segmento**, contendo a *mensagem*;
		- no destinatário, o *TCP* é identificado e é gerado um pacote *ACK \(Acknowledge)* para o remetente;
		- o protocolo *TCP* é *orientado à conexão* e *confiável*, pois confirma o recebimento dos dados;
		- os segmentos são numerados, para serem organizados pelo receptor, caso necesário;
		- há controle de fluxo pelo receptor, com base nessa numeração, para não sobrecarregar o processamento dos dados recebidos;
	- se **UDP**, a camada Transporte gera uma PDU chamada **Datagrama**, contendo a *mensagem*;

- **Camada Rede**: recebe o *segmento TCP* ou o *datagrama UDP* e o encapsula na área de dados de uma UDP chamada **Datagrama IP**, sendo também fracionado, caso necessário;
	- no cabeçalho do *datagrama IP* estarão o IP de origem e o IP de destino;
	- também é acrescido o campo **EtherType**, que servirá para indicar à Camada de Enlace do destinatário qual o protocolo de rede \(IPv4, IPv6 ou ICMP);
	- **Datagramas**, como os *datagramas IP*, ao contrário de segmentos, não possuem idenficação para orientação à conexão e não retornam confirmação de recebimento \(não são confiáveis);

- **Camada de Enlace \(link de dados)**: gera uma UDP chamada **Quadro**, com o *datagrama IP* em sua área de dados;
	- a camada de enlace é definida pela arquitetura de rede utilizada;
	- no cabeçalho do *quadro* são inseridos os endereços físicos, **MAC - Medium Access Control**, de origem e destino;
	- a área de dados do *quadro* é a **MTU - Maximum Transmission Unit**;

- **camada física**: recebe os *quadros* para *modular* e *codificar* conforme conveniente ao *meio* utilizado na transmissão;

- o processo inverso de desencapsulamento é feito pelo destinatário;


------------------------------------------------------------


# TOPOLOGY


### TOPOLOGIA TOTALMENTE CONECTADA
- topologia pela qual todos os nós numa rede estão diretamente conectados entre si; 
- fórmula para cálculo dos cabos necessários: ``` n(n-1)/2 ```;
- modelo teórico que não é implementado;
- *vantagens*:
	- não há atraso entre conexões, porque não há intermediários;
	- não há perda de conectividade, pois há redundância completa de conecções, com caminhos alternativos para as conexões;
- *desvantagens*:
	- inviabilidade por excesso de conexões;

### TOPOLOGIA EM MALHA OU MESH
- topologia com redundância de conectividade para nós críticos de rede;

### TOPOLOGIA EM ANEL
- topologia em que os nós de uma rede são conectados em anel, com duas conexões, para entrada e saída, de cada um;
- utiliza-se um sistema de **token**, em que o dispositivo insere os dados e a identificação de endereçamento a serem transmitidos para outro dispositivo ao longo do caminho circular;

### TOPOLOGIA EM BARRAMENTO, LINEAR OU BUS
- topologia mais básica entre os modelos que usam o padrão *Ethernet*;
- utiliza apenas um cabo de conexão e apenas um dispositivo pode se comunicar por vez;
- os *quadros* são enviados a todos os dispositivos, mas são recebidos apenas por aquele ao qual eles são endereçados, sendo ignorados pelos outros dispositivos;
- quando dois dispositivos tentam se comunicar ao mesmo tempo, ocorre a *colisão*, conforme visto acima em *controle de acesso ao meio*;
- por haver apenas um cabo, há apenas um único domínio de colisão e de broadcast; ocorre contenção;

### TOPOLOGIA EM ESTRELA
- topologia mais utilizada, centrada em um **dispositivo concentrador**, do qual parte apenas um cabo para cada dispositivo final;
- com **hub**:
	- opera na camada 1 do modelo OSI, o que leva a rede a se comportar como uma rede de topologia em barrmento: todos os *quadros* são enviados para todas as portas do *hub*, caracterizando apenas um único domínio de colisão e broadcast; ocorre contenção;
	- tem-se aqui uma *topologia física em estrela*, mas uma *topologia lógica em barramento*;
	- hubs operam apenas no modo *half-duplex*;
- com **switch**:
	- opera na camada 3 do modelo OSI, pois o switch lê os *quadros* e verifica seus endereçamentos, enviando-os apenas para o dispositivo de destino, criando domínios de colisão e broadcast separados;
	- switches operam no modo *full-duplex*;

### TOPOLOGIA EM ÁRVORE OU HIERÁRQUICA
- topologia que conecta mais de uma rede de *topologia em estrela*, conectando *dispositivos concentradores* entre si;


------------------------------------------------------------


# CABLING


### Cabo Coaxial
- tipo de cabeamento coaxial com impedância 50ohms;
	- cabo fino: thinnet 10base2 conector BNC;
	- cabo grosso: thicknet 10base5 conector transceptor;
- *10base* sinaliza a lrgura de banda de 10Mbits/s e tipo de transmissão banda base;
- 2 ou 5 equivale ao comprimento máximo do cabo preto, com 185 metros, ou cabo amarelo, 500 metros;

### Par Trançado
- cabeamento mais usual para redes Ethernet atualmente;
- usado em topologia estrela e árvore;
- utiliza **transmissão diferencial**: um fio do par com sinal *D+* e outro *D-*, com o sinal inverso como espelhamento do sinal, para realizar proteção contra ruído;
- par trançado para Ethernet com 4 pares:
	- **UTP - Unshielded Twisted Pair**: par trançado sem blindagem, suscetível a *cross-talk - diafonia*;
	- **STP - Shielded Twisted Pair**: par trançado com blindagem;
	- **conector 8P8C**: "RH-45";
	- subdivide-se em categorias, sendo o mais comum a **categoria 5e**, que suporta conexões de até 2,5 Gbit/s;
	- *10base-T* para *Twisted pair*;

### Fibra Óptica
- tipo de cabeamento cuja transmissão de dados opera através de um *laser - light amplification by stimulated emission of radiation* em comprimento de onda infravermelho;

- **SMF - Single-Mode Fiber** fibra monomodo:
	- a luz segue em linha reta, num percurso único;
	- mais fina \(9/125);
	- processo de fusão de emendas mais difícil, devido ao menor núcleo;
	- mais cara;
	- maior alcance \(mais longa);
	- maior largura de banda;
	- onda mais longa 1300nm;
	- mais usada em redes MANs e WANs;
		- 10 Gbit/s até 80km;
		- distâncias maiores com amplificadores ópticos;

- **MMF - Multi-Mode Fiber** fibra multimodo:
	- a luz reflete pela borda interna da fibra, por **índice degrau** ou **índice gradual**;
	- ocorre **dispersão modal** que deve ser corrigida pelo receptor;
	- a *dispersão modal* é menor com *índice gradual*;
	- mais grossa \(50/125 ou 62,5/125);
	- melhor processo de fusão de emendas, devido ao maior núcleo;
	- mais barata;
	- menor alcance \(mais curta);
	- menor largura de banda;
	- onda mais curta 850nm;
	- mais usada em redes LANs e CANs;
		- 100 Mbit/s até 2km;
		- 1 Gbit/s até 1km;
		- 10 Gbit/s até 500m;

- **SMF NZ-DSF - Single-Mode Fiber Non-Zero, Dispersion-Shifted Fiber** fibra monomodo adaptada para multiplexação por comprimento de onda **WDM - Wavelength Division Multiplexing**, com mais de um laser, implementando múltiplos comprimentos de onda para transmitir mais de um fluxo de dados separados;
	- com esse recurso, pode-se obter transmissão bidirecional;

- **conectores**:
	- **individuais**: SC - subscriber channel, ST straight tip, LC;
	- **multimodo**: MT-RJ;


- **classificação Ethernet com fibra óptica**:
	- *1000base-LX*, em que X pode ser F ou S \(short) para multimodo ou L \(long) para monomodo;

### Cabeamento Estruturado
- subsistemas:
	- 1. *ponto de entrada \(entrance facilities)*: chegada do sinal externo, entrada do prédio;
	- 2. *sala de equipamento \(equipament room)*: sala de servidores, com racks ou armários;
	- 3. *backbone cabling*: cabeamento de backbone \(espinha dorsal);
	- 4. *telecommunications rooms and enclosure*: salas ou armários de telecomunicação, normalmente com *patch panels*;
	- 5. *horizontal cabling*: cabeamento que conecta as salas de comunicação às tomadas de rede;
	- 6. *work area*: áreas de trabalho;


------------------------------------------------------------


# NETWORK EQUIPMENT


### NIC - Network Interface Card or Controller
- interface de rede do dispositivo, normalmente conhecido como *placa de rede*;
- normalmente, possuem um endereço físico **MAC - Medium Access Control**;

### Modem
- *modulador/demodulador* de sinal que conecta dispositivos ou, mais comumente, redes;
- muito frequentemente incorporado ao *roteador de banda-larga*;

### Hub
- *equipamento concentrador* para redes em topologia estrela;
- opera na **camada 1 - Física** do modelo OSI, não possuindo qualquer tipo de processamento, sendo apenas um *repetidor*, sem controle de quadro ou tráfego;
- limitado em desempenho e segurança;
- opera em mecanismo de contenção;
- pode ser ativo, realizando amplificação e restauração do sinal, ou passivo;
- **repetidor** equipamento obsoleto equivalente rudimentar do Hub para estender redes de cabo coaxial, amplificando e restaurando o sinal;

### Switch
- *equipamento concentrador* para redes em topologia estrela em nível físico e lógico;
- opera na **camada 2 - Enlace** do modelo OSI, podendo analisar os quadros que trafegam pela rede, eliminando a colisão, atuando como comutador do tráfego de rede;
- maior segurança, pois os quadros são direcionados considerando origem e destino;
- possui *buffer* para armazenamento temporário de quadros, até que sejam efetivamente transmitidos;
- o reconhecimento dos nós da rede ocorre através de um processo chamado **flooding \(inundação)**, para realizar o checagem dos endereços físicos dos nós da rede;
- *inundação* - difusão - transmissão em *broadcast* para identificar um destinatário;
- os equipamentos mais sofisticados, permitem a configuração de redes virtuais **VLANs**, separando domínios de *broadcast*, isolando-as;
- **bridge \(ponte)** um equipamento obsoleto para interligar segmentos de rede de cabo coaxial, operando na **camada 2 - Enlace** filtrando quadros e isolando os segmentos de rede, reduzindo a frequência de colisões;
- **plano de controle** para configurações do equipamento;
- **plano de dados** para processar e controlar quadros, examinando endereço físico MAC;

### Roteador
- equipamento utilizado para conectar duas redes distintas;
- opera na **camada 3 - Rede \(Internet)** do modelo OSI, analisando o endereçamento lógico dos *datagramas IP*, processando o encaminhamento de pacotes para a *rede local* e para a *rede externa*;
- possui apenas duas portas: uma LAN \(interna) e uma WAN \(externa);
- **plano de controle** para configurações do equipamento;
- **plano de dados** para processar e controlar datagramas;

### Switch Camada 3 \(Layer 3)
- switch habilitado a analisar endereçamento lógico de *datagramas IP*, conectando apenas *redes locais*;
- possui apenas portas LAN;
- utilizados para suportar comunicação entre redes virtuais VLANs, de forma análoga a um roteador;

### Firewall
- equipamento com um sistema de filtragem e controle de acesso baseado em regras;
- pode atuar impedindo acessos determinados à rede externa;

### Ponto de Acesso
- equipamento que gerencia redes do tipo Wi-Fi;
- cria uma interface entre uma rede cabeada e uma rede wireless;
- *modos de operação*:
	- *modo ESS* para expandir o alcance de uma rede Wi-Fi;
	- *modo MBSS \(mesh)* para expandir o alcance através de conexões sem uso de cabos para outros pontos de acesso;
	- *modo repetidor* para retransmitir quadros, com menor eficiência;
	- *modo ponte* para permitir uma conexão dedicada entre dois pontos de acesso sem fio, sendo útil para conectar duas redes sem cabeamento, através de um *enlace de micro-ondas \(conexão ponto-a-ponto)*;
- *características técnicas*:
	- padrões de compatibilidade *IEEE 802.11*;
	- bandas de operação *2,4GHz*, *5GHz* e *6GHz*;
		- pode ser banda dupla ou banda tripla;
	- potência de transmissão, dada em *mW* ou *dBm*;
	- potência de transmissão acrescida do ganho de amplificação proporcionado pela antena, chamada *EIRP - Equivalent Isotropic Radiated Power*;
	- capacidade *MIMO - Multiple Input, Multiple Output*, que permite transmissão e recepção simultâneas: 2x2, 3x3, 4x4 \(qantidade de antenas para transmissão de dados X qantidade de antenas para recepção de dados);

### Roteador de Banda Larga
- equipamento que acumula diversas funções normalmente atribuídas a outros equipamentos; *all-in-one*:
	- roteador;
	- servidor DHCP;
	- ponto de aceso;
	- switch;
	- firewall;
	- modem, eventualmente;

### Repetidor Sem Fio
- equipamento para expandir o alcance para redes sem fio;
- apresenta operacionalidade limitada, pois na prática cria um novo *SSID - Service Set ID* de rede com final *_EXT*;

### Balanceador de Carga
- equipamento dedicado a distribuir o tráfego de rede para mais de um servidor;

### Armazenamento
- **DAS Directly-Attached Storage** Armazenamento Conectado Diretamente:
	- classifica dispositivos conectados diretamente em uma máquina, feito HD, SSD, Flashdrive etc.;
- **NAS Network-Attached Storage** Armazenamento Conectado em Rede:
	- servidor de armazenamento autônomo;
- **SAN Storage Area Network** Rede de Área de Armazenamento:
	- conexão dedicada para unir várias unidades de armazenamento;
	- acessível como se fosse uma unidade *DAS*;
	- *padrões*:
		- InfiniBand;
		- iSCSI;
		- Fibre Channel;
	- conexão física a uma placa de expansão especial acrescida ao servidor;

### RAID - Redundant Array of Independent Disks
- **RAID 0** - Divisão de Dados - Aumento de Desempenho;
	- dados são dividos entre as unidades de armazenamento disponibilizadas e gravados de forma fracionada;
	- a consulta simultânea a diferentes frações do mesmo arquivo divididas entre os dispositivos, aumenta o desempenho de leitura;
	- há soma da capacidade de armazenamento, conforme as unidades de armazenamento disponíveis;
	- mínimo de dois discos;

- **RAID 1** - Espelhamento - Redundância - Aumento da Confiabilidade - Backup em tempo real;
	- dados são replicados e gravados simultaneamente em cada uma das unidades de armazenamento disponibilizadas;
	- através de conexão **hot swap**, a substituição de um dispositivo defeituoso, com o sistema em operação, não afeta o armazenamento e uso de dados;
	- não há soma de capacidade de armazenamento disponível;
	- mínimo de dois discos;

- **RAID 2** - Divisão de Dados - Aumento de Desempenho - semelhante ao *RAID 0*, mas com *ECC*;
	- possui um algoritmo específico para detecção de erros **ECC**:
		- *Error Correcting Code*;
	- mínimo de dois discos;
	- método obsoleto;

- **RAID 3**:
	- **paridade**: informação de redundância com detecção de erros na transmissão de dados; anexo de um bit de paridade extra para cada byte transmitido; um erro é detectado se a paridade do byte não coincidir com o bit de paridade;
	- acrescenta *um disco de paridade* exclusivo para os bits de paridade;
	- mínimo de três discos;
	- método obsoleto;

- **RAID 4**:
	- equivalente ao *RAID 3* com dados de paridade em blocos maiores no disco exclusivo;
	- mínimo de três discos;
	- método obsoleto;

- **RAID 5**: 
	- equivalente ao *RAID 3* com dados de paridade em setores de todos os discos, sem um disco exclusivo para paridade;
	- paridade distribuída: se um disco apresentar falhas, não há comprometimento da integridade dos dados;
	- mínimo de três discos;

- **RAID 6**:
	- equivalente ao *RAID 5* com maior tolerância a falhas, em que até dois discos podem apresentar falhas sem comprometimento da integridade dos dados;
	- mínimo de quatro discos \(capacidade de dois discos dedicada à paridade);


------------------------------------------------------------


# WIRELESS NETWORKS


## WIRELESS TYPES

### PAN - Personal Area Network
- bluetooth;
- infravermelho - IrDA, *IEEE 802.11-1997*;

### LAN and CAN
- Wi-Fi *IEEE 802.11*;

### MAN and WAN
- WiMAX - *IEEE 802.16* - banda larga sem fio para regiões metropolitanas;
- Redes 4G e 5G;
- Microwave Link - Enlace de Micro-ondas: linha reta com 80km de alcance;
- Satélite;

------------------------------------------------------------

## WI-FI NETWORKS

### Modos de Operação

- **IBSS - Independent Basic Service Set** Conjunto de Serviços Básico Independente **Ad-hoc**:
	- *sem ponto de acesso*;
	- cada estação controla a conexão de forma independente, como em uma conexão ponto a ponto;

- **BSS - Basic Service Set** Conjunto de Serviços Básico:
	- *com ponto de acesso*;
	- o ponto de acesso serve como concentrador, feito uma topologia estrela;
	- **Infrastructure BSS - Infrastructure Basic Service Set** Conjunto de Serviços Básicos de Infraestrutura: com ponto de acesso oferecendo conexão com a internet, como ocorre com um roteador de banda larga, mais comum em redes residenciais;
	- *SSID - Service Set ID* é o *nome* da rede, pelo qual ela é identificada publicamente;

- **ESS - Extended Service Set** Conjunto de Serviços *Extendido*:
	- utiliza *pontos de acesso* para expansão da rede com o mesmo SSID;
	- nas áreas de *sobreposição de sinal*, devem-se usar *canais* diferentes;

- **MBSS - Mesh Basic Service Set** Conjunto de Serviços Básico em Malha:
	- modo *mesh* aplicado ao wi-fi, mas sem uso de qualquer cabo conectando os pontos de acesso;
	- o modo *bridge* implementa a conexão entre os pontos de acesso, através do sistema *WDS - Wireless Distribution System*;
	- devem-se usar *canais* diferentes;
	- o ponto de acesso principal é chamado *portal*, normalmente um roteador de banda larga, e os outros são chamados *nós*;

### Serviços de Estação
- Serviços disponíveis para as estações \(clientes):
	- *Autenticação*:
		- habilita a conexão da estação;
		- solicita chave criptográfica, caso a criptografia esteja ativada;
	- *Desautenticação*;
	- *Privacidade*:
		- criptografa os dados sendo transmitidos, caso ativada;
	- *Entrega de Dados*;

- *Serviços de Distribuição*, disponíveis para os pontos de acesso:
	- *Associação*:
		- associa uma estação a um ponto de acesso, para que ela não esteja conectada a mais de um ponto de acesso da mesma rede;
	- *Desassociação*;
	- *Reassociação*:
		- movimenta uma estação para outro ponto de acesso na mesma rede;
	- *Distribuição*:
		- comunicação com demais pontos de acesso;
	- *Integração*:
		- interfaceamento da rede Wi-Fi com redes de outras arquiteturas, com tradução de quadros;

### Acesso ao Meio

- **contenção**:
	- algoritmo probabilístico CSMA/CA \(Carrier-Sense Multiple Access with Collision Avoidance) *usado em redes Wi-Fi*:
		- Evasão de Colisão;
			- um dispositivo aguarda o canal de transmissão estar livre para iniciar uma transmissão, evitando a colisão;
		- verifica se o meio está livre antes do envio do quadro, através da escuta do canal pelo sistema de rádio, rastreando inatividade;
	- diferente do 	algoritmo probabilístico CSMA/CD \(Carrier-Sense Multiple Access with Collision Detection) *usado em redes Ethernet*, por detecção de Colisão;

- **multiplexação por divisão de tempo** para a transmissão de quadros para cada nó;

- **multiplexação por divisão de frequência** para separar canais de dados;

------------------------------------------------------------

## ELECTROMAGNETIC SPECTRUM

### Uso do Espectro Eletromagnético
- **band ISM - Industrial, Scientific and Medical**:
	- faixas de frequência livres para uso; ICM no BR:
		- 900 MHz: 902 a 907,5 MHz; 915 a 928 MHz;
		- **2,4 GHz: 2.400 a 2.483,5 MHz**;
		- **5,8 GHz: 5.725 a 5.875 MHz**;
		- 24 GHz: 24,00 a 24,25 GHz;
- regulamentadas pela FCC nos EUA e ANATEL no BR;

### Faixa 2,4 GHz
- BR, Europa: 
	- de 2.415 MHz até 2.472 MHz; 
- dividida em 13 canais, com intervalos de 5 MHz;
- 4 canais de 20 MHz sem sobreposição;
- faixa de canais saturados, utilizada por diversos equipamentos;

### Faixa 5 GHz
- ANATEL Ato 14.448/2017 com padrão FCC/EUA:
	- U-NII-1: de 5.150 a 5.250 MHz, canais 32 a 48:
		- ambientes internos; 
		- DFS opcional;
	- U-NII-2A: de 5.250 a 5.350 MHz, canais 52 a 68:
		- ambientes internos; 
		- DFS obrigatório;
	- U-NII-2B: de 5.350 a 5.470 MHz: 
		- não usado;
	- U-NII-2C: de 5.470 a 5.725 MHz, canais 96 a 144:
		- ambientes internos ou externos;
		- DFS obrigatório;
	- U-NII-2C: de 5.725 a 5.850 MHz, canais 149 a 165:
		- ambientes internos ou externos;
	- *DFS - Dynamic Frequency Selection*: detecta se há radar utilizando a frequência;
- possui 28 canais de 20 MHz sem sobreposição;
- possui 12 canais de 40 MHz sem sobreposição;
- possui 6 canais de 80 MHz sem sobreposição;
- possui 2 canais de 160 MHz sem sobreposição;

### Faixa 6 GHz
- BR e EUA:
	- de 5.925 MHz a 7.125 MHz;
	- até 59 canais de 20 MHz sem sobreposição;
- faixa suportada a partir do padrão Wi-Fi 6E - IEEE 802.11ax, com extensão de 6GHz;
- canais de até 320 MHz, a partir do padrão Wi-Fi 7 - IEEE 802.11be;
- suporta 3 tipos de equipamento 6 GHz:
	- *Standard Power*:
		- opera em ambientes externos;
	- *Low Power Indoor*:
		- tipo mais comum, opera em ambientes internos;
		- diferente de outros casos, ao dobrar a largura do canal pode-se dobrar a potência de transmissão é dobrada, compensando a dobra do nível de ruído;
	- *Very Low Power*:
		- pode ser usado em ambientes externos, sem interferência sistemas de comunicação que operam nessa faixa;

------------------------------------------------------------

## IEEE 802 STANDARDS

### IEEE 802.11-1997 - Wi-Fi 0
- opera na faixa 2,4 GHz;
- canais de 22 MHz;
- método de transmissão: 
	- infravermelho; 
	- FHSS - Frequency Hopping Spread Spectrum; 
	- DSSS - Direct Sequence Spread Spectrum;
- velocidades: 2 Mbit/s ou 1 Mbit/s;

### IEEE 802.11b - Wi-Fi 1
- ano 1999;
- opera na faixa 2,4 GHz;
- canais de 22 MHz;
- método de transmissão: DSSS - Direct Sequence Spread Spectrum;
- velocidades: 11, 5,5, 2 ou 1 Mbit/s;

### IEEE 802.11a - Wi-Fi 2
- ano 1999;
- opera na faixa 5 GHz;
- canais de 20 MHz;
- método de transmissão: OFDM;
- velocidades: 54, 48, 36, 24, 18, 12, 9 ou 6 Mbit/s;

### IEEE 802.11g - Wi-Fi 3
- ano 2003;
- opera na faixa 2,4 GHz;
- canais de 20 MHz;
- método de transmissão: OFDM;
- velocidades: 54, 48, 36, 24, 18, 12, 9 ou 6 Mbit/s;
- conversão do padrão IEEE 802.11a para 2,4 GHz;

### IEEE 802.11n - Wi-Fi 4
- ano 2009;
- opera nas faixas 2,4 GHz ou 5 GHz;
- canais de 20 MHz ou 40 MHz;
- método de transmissão: MIMO-OFDM, com até 4 fluxos espaciais \(multiplexação espacial);
- velocidades: até 32 larguras de banda com o método MIMO de até 4 fluxos;

### IEEE 802.11ac - Wi-Fi 5
- ano 2013 \(wave 1) e 2016 \(wave 2);
- opera na faixa 5 GHz;
- canais de 20 MHz, 40 MHz e 80 MHz na *wave 1*; 80+80 MHz e 160 MHz na *wave 2*;
- método de transmissão: 
	- MIMO-OFDM com até 3 fluxos espaciais na *wave 1*;
	- MIMO-OFDM com até 4 na *wave 2*; 
	- Beamforming, permitindo seccionamento e direcionamento de fluxos espaciais para transmissão simultânea; 
	- MU-MIMO-OFDM para downlink na *wave 2*, permitindo transmissão simultânea de quadros;
- velocidades: até 32 larguras de banda com o método MIMO de até 4 fluxos;

### IEEE 802.11ax - Wi-Fi 6/6E
- ano 2019 \(Wi-Fi 6) e 2021 \(Wi-Fi 6E);
- opera nas faixas de 1 a 6 GHz;
- canais de 20 MHz, 40 MHz, 80, 80+80 e 160 MHz;
- método de transmissão: MU-MIMO-OFDMA com até 8 fluxos espaciais;

### IEEE 802.11be - Wi-Fi 7
- ano 2024;
- opera nas faixas de 1 a 7 GHz \(multi-link operation);
- canais de até 320 MHz;
- método de transmissão: MU-MIMO-OFDMA com até 16 fluxos espaciais;

### IEEE 802.16
- regulamentação para WiMAX, banda larga sem fio para regiões metropolitanas;

------------------------------------------------------------

## WI-FI SECURITY

### Protocolos Padrão IEEE 802.11
- WEP: obsoleto quebrado;
- WPA: obsoleto quebrado;
- WPA2: preferencial;
- WPA3: preferencial;

### WPS
- Wi-Fi Protected Setup;
- autenticação por PIN ou por acionamento de botão WPS;
- PIN costuma ser inseguro, pois é facilmente quebrado com ferramentas adequadas;


------------------------------------------------------------


# NETWORK VIRTUALIZATION


### Virtualização Interna
- simulação de uma rede e do tráfego de dados em uma máquina;
- softwares específicos são desenvolvidos para dar suporte a essa simulação;

### Virtualização SDN/VLAN
- **Software Defined Network**:
	- componentes de rede podem ser modificados através de software: um switch que, suportando a tecnolgia, pode ser virtualmente dividio em dois switches lógicos gerenciando duas redes independentes;
	- *Plano de Controle* do equipamento passa a ser controlado por software;

### Virtualização NFV
- **Network Function Virtualization**:
	- utilização de pequenas máquinas como equipamentos de rede através de softwares apropriados;
	- máquinas podem exercer função de firewall, balanceador de carga etc.;
	- *Plano de Controle* e *Plano de Dados* são controlados por software;

### Virtualização de Desktop
- um Desktop virtual acessado por uma estação fica armazenado em um servidor, sendo acesível em qualquer estação conectada à rede;

### Virtualização de Armazenamento
- centralização do armazenamento, feito armazenamento em nuvem;


------------------------------------------------------------


# SECURITY


## CIA

### Confidentiality
- queremos que apenas pessoas autorizadas tenham acesso à informação;
- comprometimentos:
	- roubo ou furto de equipamentos como celular ou notebook;
	- e-mail enviado a endereço errado;
	- leitura de documento por pessoa não autorizada
	- captura de pacotes de dados;
- mitigação:
	- criptografia;
	- autenticação em dois fatores \(2FA);
	- biometria;
	- uso de computador sem qualquer tipo de conexão \(air-gapped) em conjunto com medidas de proteção física para uso e acesso, autenticação etc.;

### Integrity
- queremos que a informação não seja adulterada;
- comprometimentos:
	- adulteração de documento;
	- adulteração de pacotes de dados;
- mitigação:
	- cópia autenticada;
	- soma de verificação \(checksum) e CRC;

### Availability \(Disponibilidade)
- queremos que a infraestrutura esteja disponível sempre em que haja demanda;
- comprometimentos:
	- ataque do tipo DDoS \(Distributed Denial of Service, negação de serviço distribuída);
	- falha de hardware;
- mitigação:
	- firewall;
	- sistema de detecção de intrusos \(IDS);
	- manutenção preventiva da infraestrutura \(hardware e software);

### Autenticação e Autorização
- *Autenticação* ou Identificação é um desdobramento do princípio da Confidencialidade;
	- verificação de credenciais de usuário;
- *Autorização* é a verificação dos privilégios de um usuário em um sistema;
- comprometimentos:
	- roubo de credenciais \(login e senha);
- mitigação:
	- autenticação em dois fatores \(2FA);
	- biometria;

### Autenticidade
- queremos que a informação não seja adulterada;
- comprometimentos:
	- falsidade ideológica;
	- golpes \(scam) em que o remetente diz ser de uma determinada empresa;
- mitigação:
	- reconhecimento de firma;
	- certificado digital;

### Conformidade
- estar de acordo com as políticas e normas de segurança da organização e de acordo com a lei;

### Irretratabilidade
- característica dos atos jurídicos que, por imposição legal ou acordo entre as partes, não podem ser desmentidos, revogados ou desfeitos;

### Privacidade
- queremos que informações sejam usadas apenas pelo seu destinatário original e apenas para os fins propostos;
- comprometimentos:
	- venda ou disponibilização de dados pessoais a terceiros;
	- envio de e-mails não solicitados \(spam);
- mitigação:
	- legislação que descreva e proíba o uso não autorizado da informação;

------------------------------------------------------------

## CREDENTIALS

### Senhas
- não armazenar senhas em texto puro \(plain text) nos bancos de dados, mas através de Funções Hash \(resistência à primeira inversão ou propriedade unidirecional) e Checksums: 
	- algoritmos frágeis: MD5 e SHA1;

### Criptografia
- *criptografia simétrica*: a mesma chave criptografa e descriptografa;

- *criptografia assimétrica*: um par de chave é usado, com um chave pública, usada para criptografar os dados, e uma chave privada, para descriptografar os dados;

### IDS - IPS
- *IDS - Intrusion Detection System* Sistema de Detecção de Intrusos: apenas emite alerta;
- *IPS - Intrusion Prevention System* Sistema de Prevenção de Intrusos: impede o acesso;
- *IDPS* combina as funções; 
- NIDS, NIPS e NIDPS atuam na rede \(network);
- HIDS, HIPS e HIDPS atuam na máquina \(host);

### DoS
- *Denial of Service* é um ataque de negação de serviço, normalmente provocado por sobrecarga de acessos a um serviço;
- *Distributed DoS - DDoS* é um ataque DoS a partir de diversos clientes;


























