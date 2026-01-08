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
- considerar as potências de 2 para cada casa do bloco: ``` 8, 4, 2, 1 ```;
		- ``` 8		 4		 2		 1 	```
		- ``` 1		 1		 1		 0	```
		- o binário do bloco acima equivale a \(12)₁₀, *i. e.*, \(C)₁₆;
- multiplicar pelo 1 ou 0 que as ocupa, somando os resultados de cada bloco;
- considerar para cada bloco: 10 = A, 11 = B, 12 = C, 13 = D, 14 = E, 15 = F;
¹²³⁴⁵⁶⁷⁸⁹⁰₀₁₂₃₄₅₆₇₈₉

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

### Sistema de Ordenação
- **lsb0**: sistema que identifica os bits como: b0, b1, b2, b3 etc. no mesmo sentido das potências de 2, da direita para a esquerda; 
	- os números das posições, nesse caso, coincidem com as potências, pois parte do bit menos significativo;
	- o sistema *lsb0* é o mais utilizado em *eletrônica digital*;
- **msb0**: sistema que idenficia os bits da forma inversa, a partir do bit mais significativo;
	- o sistema *msb0* é o mais utilizado em *pilha de protocolo TCP/IP*;

------------------------------------------------------------

## BINARY WORDS
