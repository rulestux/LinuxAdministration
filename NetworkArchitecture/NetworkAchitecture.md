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
	- [TOPOLOGY TYPES](#TOPOLOGY-TYPES)
- [CABLING](#CABLING)
	- [CABLING TYPES](#CABLING-TYPES)
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

### Controle de Acesso ao Meio
- mecanismos de controle do uso do meio pelos dispositivos conectados:

- **CONTENÇÃO**:
	- algoritmo probabilístico CSMA/CD \(Carrier-Sense Multiple Access with Collision Detection):
		- Detecção de Colisão:
			- um dispositivo detecta a colisão de uso do meio por outro dispositivo e aguarda um período de tempo aleatório para tentar novamente;
		- usado em redes Ethernet de topologia linear, em barramento;
	- algoritmo probabilístico CSMA/CA \(Carrier-Sense Multiple Access with Collision Avoidance):
		- Evasão de Colisão;
			- um dispositivo aguarda o canal de transmissão estar livre para iniciar uma transmissão, evitando a colisão;
		- usado em redes Wi-Fi;

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
- modelo de 7 camadas por que um dado passa após sair do **aplicativo** e antes de chegar ao **meio** em que será transmitido;
- cada camada gera uma **Protocol Data Unit \(PDU)** que é repassado para a camada imediatamente inferior;
- na camada inferior, a *PDU* é inserido na *área de dados* do pacote recebido da camada superior, resultando em um cabeçalho específico;
- **Service Access Point \(SAP)** é o sistema de endereçamento no cabeçalho de cada *PDU* que direciona o pacote ao protocolo correto numa camada superior;

- **CAMADAS**:

	- 7 **Aplicação**:
		- camada que identifica os **Protocolos de Aplicação**;
		- gera uma **Mensagem** com os dados e os comandos sobre o que fazer com os dados;

	- 6 **Apresentação**:
		- camada que identifica ou modifica **Formato dos Dados**, resolvendo problemas de representação de informação existente entre *sistemas heterogêneos interconectados;
		- camada relacionada à *sintaxe* e à *semântica*;
		- responsável por comprimir ou descomprimir os dados;
		- responsável por criptografar dados, com o protocolo **TLS - Transport Layer Security** \(ou *SSL - Secure Socket Layer*, versão obsoleta antecessora ao *TSL*);
		- aqui, a *mensagem* ainda não está fracionada em pacotes menores;

	- 5 **Sessão**:
		- camada que cria uma *sessão* de conexão que, em caso de interrupção, a transferência é retomada a partir desse *sessão*;
		- *mensagem* ainda íntegra;

	- 4 **Transporte**:
		- camada intermediária entre as camadas de alto nível \(5-7) e as camadas de baixo nível \(1-3);
		- camada em que se identificam origem e destino de dados;
		- nesta camada, inicia-se o **fracionamento em pacotes menores**;
		- definem-se *segmentos TCP* ou *datagramas UDP*;
		- camada responsável também pelo ordenamento e pela integridade dos dados, com mecanismos como a numeração e a *soma de verificação*;

	- 3 **Rede \(*Internet*)**:
		- camada de roteamento de dados;
		- camada responsável pelo endereçamento lógico dos pacotes;
		- camada de operação de **roteadores** e **switches** direcionando os dados, normalmente com os protocolos IPv4, IPv6, IPsec ou ICMP;
		- camada responsável por gerar PDUs chamadas *datagramas IP*;

	- 2 **Link de Dados \(Enlace de Dados)**:
		- camada de operação de **switches**. que é responsável por inserir os *datagramas IP* em PDUs chamadas *quadros* ou *células*;
 		- camada responsável por gerar PDUs chamadas *quadros*;
		- camada responsável por identificar os *endereços físicos*, **MAC - Medium Access Control** de origem e destino dos pacotes;

	- 1 **Física**:
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

- **camada física**: recebe os *quadros* para *modular* e *codificar* conforme conveniente ao *meio* utilizado na transmissão;

- o processo inverso de desencapsulamento é feito pelo destinatário;


------------------------------------------------------------


# TOPOLOGY


## TOPOLOGY TYPES

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

## CABLING TYPES




















