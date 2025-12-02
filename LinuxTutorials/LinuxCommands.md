## GLOSSARIVM

- [GENERAL COMMANDS](#GENERAL-COMMANDS)
	- [GENERAL COMMANDS](#GENERAL-COMMANDS)
	- [TEXT FILTERING](#TEXT-FILTERING)
	- [PRINTING](#PRINTING)
	- [FILE HANDLING](#FILE-HANDLING)
	- [REDIRECTS](#REDIRECTS)
- [SYSTEM ADMINISTRATION](#SYSTEM-ADMINISTRATION)
	- [SYSTEM BASE](#SYSTEM-BASE)
	- [PARTITIONS](#PARTITIONS)
	- [FILE SYSTEMS](#FILE-SYSTEMS)
	- [PROCESS MANAGEMENT](#PROCESS-MANAGEMENT)
	- [LOCAL AND TIME](#LOCAL-AND-TIME)
	- [PACKAGE MANAGEMENT](#PACKAGE-MANAGEMENT)
	- [PARTITIONS](#PARTITIONS)
- [SECURITY](#SECURITY)
	- [PERMISSIONS](#PERMISSIONS)
	- [USER MANAGEMENT](#USER-MANAGEMENT)
	- [NETWORK](#NETWORK)


# GENERAL COMMANDS

### pwd
- exibe o caminho do diretório corrente.

### uname
- exibe a arquitetura do sistema, a versão do kernel a distribuição e a versão
da distribuição.
- **opções:**
    - -a, --all;
	- -s, --kernel-name;
	- -n, --nodename;
	- -r, --kernel-release;
    - -v, --kernel-version;
	- -m, --machine \(machine hardware name);
	- -p, --processor \(processor type);
	- -i, --hardware-platform;
	- -o, --operating-system.

### man 
- acessa arquivos de ajuda da documentação de um comando fornecido a seguir, a partir dos arquivos localizados em '/usr/share/man'; note que o diretório de manuais está divido em sessões;
- 'man' funciona apenas com o nome exato do comando.

### apropos
- explora os nomes e descrições das páginas de manuais (man pages) de um comando fornecido a seguir, permitindo encontrar o objeto de busca de um modo mais gnérico;
- equivale a ```man -k ```.

### info
- exibe uma versão resumida de 'man' para um comando fornecido a seguir.

### whatis
- obtém informações sumárias em poucas linhas de um comando fornecido a seguir, indicando a sessão 'man', de onde o termo foi localizado.

### which
- retorna sempre a localização absoluta de um executável fornecido, buscando pelos caminhos parents especificados na variável $PATH;
- com a opção '-a', todos os nomes de caminho para o executável são exibidos;
- busca apenas em caminhos especificados na variável $PATH.

### type
- retorna igualmente informações sobre um binário fornecido e seu tipo, em relação ao bash, caso seja builtin;
- a opção '-a' é análoga à de which;
- a opção '-t' detalha o tipo.

### whereis
- equivale a which, mas retorna também a localização das páginas de manual ou código fonte do programa;
- a opção '-b' filtra o resultado pelo binário;
- a opção '-m' retorna a localização do manual;
- a opção '-s' retorna a localização do código fonte.

### sleep
- utilizado em scripts de shell para pausar a execução por um determinado período de tempo;
- **sintaxe:**

	- ```$ sleep NT ```

		- em que 'N' é um número de tempo e 
		- 'T' uma unidade de tempo, que pode ser:
			- 's' segundos;
			- 'm' minutos;
			- 'h' horas;
			- 'd' dias.

### history
- exibe os comandos executados anteriormente, acessando-os através do buffer e do conteúdo do arquivo '.bash_history' \(ou '.zsh_history'); 
- 'history N' exibe apenas os últimos 'N' comandos do histórico;
- digitar '!N' no shell, reutiliza o comando número 'N' do histórico; '!!' reutiliza o comando imediatamente anterior;
- os comandos em buffer só são gravados no histórico depois de se encerrar a sessão corrente.
- variáveis para histórico:
    - $HISTFILE guarda o caminho para o arquivo de histórico;
    - $HISTSIZE define a quantidade máxima de comandos no buffer;
    - $HISTFILESIZE define a quantidade máxima de comandos armazenados no arquivo de histórico.

### bash and zsh
- como comando, inicia um shell filho, seja em um pts \(pseudo terminal slave - emulador de terminal) ou em um tty \(teletypewritter); 
- para abrir um console tty, pode-se usar as combinações ctrl+alt+F1-F6; ctrl+alt+F7 retorna ao desktop;
- **opções para o comando bash:**
	- '-l' ou '--login' invocam um shell de login;
	- '-i' invoca um shell interativo;
	- '--noprofile' em shell de login, ignora arquivos feito '/etc/profile' de sistema e '~/.bash_profile', '~/.bash_login' e '~/.profile' de usuário;
	- '--norc' em shell interativo, ignora arquivos feito '/etc/bash.bashrc' de sistema e '~/.bashrc' de usuário;
	- '--rcfile' em shell interativo, considera o arquivo fornecido a seguir como arquivo de inicialização, no lugar de arquivos de sistema e arquivos de usuário.

### exec
- antecedendo um comando, sai da sessão do shell quando a execução desse comando é encerrada; útil para assegurar o encerramento de uma sessão iniciada por um script.

### $0
- variável que contém o tipo de shell, que pode retornar:
	- '-bash' ou '-su' interativo de login;
	- 'bash' ou '/bin/bash' interativo sem login;
	- 'nome_de_script' não interativo.

- **Bash Built-in Variables:**
	- $? referencia o resultado do último comando, sendo '0' sucesso;
	- $$ expande-se para o PID do shell;
	- $! expande-se para o PID do último trabalho em segundo plano;
	- $0 expande-se para o nome do shell ou script; os valores acima de '0' expandem para as posições de parâmetros ou argumentos;
	- $# expande-se para o número de argumentos;
	- $@ ou $* expandem-se para todos os argumentos;
	- $_ expande-se para o último parâmetro ou nome, caso não existam parâmetros.
	- $SHLVL guarda a camada de sessão do shell.
	- $IFS variável 'Input Field Separator', por padrão: espaço, tabulação e nova linha;
		- ```$ IFS=$'\n'``` configura quebra de linha como separador, por exemplo.

### basename
- comando que retorna somente o nome de um arquivo cujo caminho completo seja fornecido a seguir;
- útil em scripts seguido de '"$0"', para obter somente o nome do arquivo do script:

	``` basename "$0" ```

### dirname
- comando que retorna o diretório de um arquivo cujo nome seja fornecido a seguir;
- útil em scripts seguido de '"$0"', para obter o diretório do arquivo do script:

	``` dirname "$0" ```

### alias
- cria aliases temporários na sessão, com a sintaxe
	- ```alias var=COMMAND```

### export
- passa uma variável fornecida a seguir para os subshells (shells filhos);
- 'export -n' retorna uma variável ao status local;
- 'export -p' lista todas as variáveis de ambiente.

### declare
- 'declare -x' equivale a export;
- 'declare -f' lista funções.
- **arrays:**
	- ```$ declare -a ARRAY```
	- ```$ ARRAY=( 1 2 3 4 5 )```
	- ```$ echo ${ARRAY}```
	- ```$ echo ${ARRAY[0]}```
	- ```$ echo ${ARRAY[@]}``` ou ```$ echo ${ARRAY[*]}``` referenciam todas as posições do array;
	- ```$ echo ${#ARRAY[@]}``` ou ```$ echo ${#ARRAY[*]}``` retornam o comprimento de um array;

### let
- comando usado para criar variáveis com expressões: ```$ let "VAR = EXPRESSION" ```

### expr
- 'expr' e ```$(())``` indicam uma expressão aritmética.

### readonly
- cria, transforma ou mostra variáveis imutáveis;
- 'readonly -p' lista as variáveis imutáveis.

### set
- exibe todas as variáveis locais e globais e funções do shell atual.

### unset
- desconfigura valores e atributos de varáveis e funções do shell fornecidas a seguir.

### env
- estende e modifica as variáveis de ambiente (apenas variáveis globais).
- com '-u' desconfigura uma variável de ambiente fornecida a seguir;
- 'env -i bash' inicia uma sessão do shell sem a maioria das variáveis de ambiente;
- 'env' antecedendo a declaração de uma variável, prepara-a para uso exclusivo em um script:
 ```# env DADOS='/var/log/syslog' bash /usr/local/bin/new_data.sh```

### printenv
- assim como 'env', 'printenv' imprime na tela as variáveis de ambiente;
- 'printenv' também pode ser usado para imprimir o conteúdo de uma variável fornecida, mas diferente de 'echo', 'printenv' mostra o conteúdo da variável sem precisar do método de referenciamento com '$'.

### alias
- comando que retorna aliases disponíveis ou permite criar novos;
- para desconfigurar um alias, usa-se **unalias**.

### source
- comando que executa scripts num mecanismo chamado sourcing;
- ```source``` equivale a ``` . ```.

### test
- 'test' e ```[ ]``` retornam booleano true ou false.
- **opções para test**
	- podem-se usar variáveis para estas opções, desde que sejam referenciadas entre aspas duplas;
	- **ARQUIVOS**	
	- '-a' testa se o destino de um caminho fornecido a seguir é um arquivo;
	- '-b' se é um bloco especial;
	- '-c' se é um caractere especial;
	- '-d' se é um diretório;
	- '-e' se existe no sistema de arquivos;
	- '-f' se é um arquivo regular;
	- '-g' se tem permissão SGID;
	- '-G' se pertence ao grupo do usuário corrente;
	- '-h' ou '-L' se é um symlink;
	- '-k' se tem permissão sticky bit;
	- '-n' testa se o conteúdo de uma variável de string não está vazia;
	- '-N' se foi modificado desde o último acesso;
	- '-O' se é de propriedade do usuário corrente;
	- '-p' se é um arquivo pipe;
	- '-r' se é legível pelo usuário corrente;
	- '-s' se não está vazio;
	- '-S' se é arquivo socket;
	- '-t' se está aberto em um terminal;
	- '-u' se tem permissão SUID;
	- '-w' se é gravável pelo usuário corrente;
	- '-x' se é executável pelo usuário corrente;
	- '-z' testa se o conteúdo de uma variável de string está vazia, feito uma string de tamanho 0;
	- '-nt' se o destino de um caminho anteriormente fornecido é mais recente que o caminho seguinte, conforme última modificação;
	- '-ot' se é mais antigo;
	- '-ef' se é link físico um para o outro;
	- **TEXTOS \(STRINGS)**
	- '=' ou '==' compara se duas variáveis têm conteúdos de texto iguais;
	- '!=' se diferentes;
	- '<' e '>' se vêm antes ou depois em ordem alfabética, respectivamente;
	- **OPERADORES DE COMPARAÇÃO COM NÚMEROS**
	- '-lt' menor que;
	- '-gt' maior que;
	- '-le' menor ou igual;
	- '-ge' maior ou igual;
	- '-eq' igual;
	- '-ne' diferente;
	- **MODIFICADORES**
	- '!' testa se uma expressão que se seguir é falsa;
	- '-a' entre expressões, testa se uma anterior e outra seguinte são verdadeiras;
	- '-o' testa se ou a anterior ou a seguinte é verdadeira.

------------------------------------------------------------

## TEXT FILTERING

### cat
- combina e retorna o conteúdo de arquivos de texto simples fornecidos;
- 'cat' retorna o conteúdo de um arquivo, com um output que pode ser direcionado para outro arquivo, usando ```>``` ou ```>>```; 
- com ```<```, seguido do caminho do arquivo, o conteúdo é exibido na tela;
- **opções:**
    - '-n' numera todas as linhas, incluso linhas em branco;
    - '-b' numera apenas linhas escritas;
- **tac** retorna o conteúdo de um arquivo de forma invertida;
- **bzcat**, **xzcat** e **zcat** processam ou lêem arquivos comprimidos usando os métodos bzip2, xz e gzip, respectivamente.

### echo
- exibe as strings e variáveis informadas;
- **opções:** 
	- '-e' seguida de strings em aspas, permite formatação de conteúdo, habilitando a exibição de caracteres especiais com escape '\', como
		- tabulação: '\t';
		- nova linha: '\n';
	- '-n' remove a quebra de linha (Enter) em scripts, sendo normalmente usando antes do comando 'read', para entrada de dados.

### printf
- comando para exibir dados na tela com funcionamento semelhante ao da linguagem 'C':
	- '%s' substitui texto \(strings);
	- '%d' inteiros;
	- '\n' para quebras de linha em final de strings longas.

### less
- pagina o conteúdo de um arquivo fornecido a seguir, possibilitando navegação e pesquisa, sendo uma versão mais moderna do **more**.

### head
- exibe as dez primeiras linhas de um arquivo fornecido a seguir; 
- a opção '-n N' permite personalizá-lo, enumerando a quantidade de linhas desejadas em 'N'.

### tail
- exibe as dez últimas linhas de um arquivo; 
- **opções:**
	- '-n N' permite personalizá-lo, enumerando a quantidade de linhas desejadas em 'N'; 
	- '-f' segue a saída do arquivo de texto conforme novos dados são acrescidos a ele em tempo real.

### read
- comando para entrada \(leitura) de dados;
- **sintaxe:**
	
	- ```$ read OPTIONS VARIABLE(S) ```

- **opções:**
	- '-a' lê um array;
	- '-d' define um delimitador personalizado para a entrada;
	- '-p' permite inserir um 'prompt' entre aspas para se exibir antes da entrada dos dados;
	- '-r' permite interpretar barras invertidas '\\' como escape;
	- '-s' oculta o que é digitado, sendo útil para a inserção de senhas.

### diff
- compara dois arquivos fornecidos a seguir e não retorna coisa alguma se eles forem idênticos;
- retorna a diferença quando são diferentes.

### wc
- word count options file;
- **opções:**
    - '-l' número de linhas;
    - '-w' número de palavras;
    - '-m' número de caracteres.

### sort
- retorna o conteúdo dos arquivos em ordem alfabética;
- **opções:**
    - '-r' reverte (inverte) a ordem.

### uniq
- retorna o conteúdo de um arquivo, sem exibir linhas com conteúdo repetido em sequência;
- para retornar sem qualquer repetição, usar uma sintaxe de redirecionamento do output: ```$ sort file | uniq```.
- **opções:**
    - '-d' exibe somente as linhas que se repetem;
    - '-c' conta e exibe a quantidade de vezes que uma linha se repete.

### nl
- numera as linhas de um arquivo, usando a sintaxe:

	- ```$ cat /caminho/do/arquivo | nl ```
	- ```$ nl /caminho/do/arquivo ```

### tr
- translate:
- **Opções e parâmetros:**

	- mudar minúsculas para maiúsculas:

		- ```$ tr 'a-z' 'A-Z' ```
		- ```bash $ tr '[:lower:]' '[:upper:]' ```

	- substituir espaços por underscores:
		
		- ```$ tr ' ' '_' ```

	- remover os espaços:

		- ```$ tr -d ' ' ```
		- ```$ tr -d [:blank:] ```

### cut
- corta e exibe partes de um arquivo de texto, separando-o em colunas, usando um caractere fornecido como referência ```-d'caractere'``` \(delimitador), seguido da posição \(campos) dos elementos a serem exibidos com 					```-f número,número,número```:

	- ```$ cut -d; -f1,6,7 /caminho/do/arquivo ```

- ou em um intervalo de caracteres com ```c-número-número```:

	- ```$ cut -d; -c2-8 /caminho/do/arquivo ```

### awk
- utilitário para analisar e manipular dados em linha, separando colunas usando espaço como delimitador;
- a opção '-F' pode ser utilizada para escolher outro delimidador fornecido imediatamente a seguir
	- ```-F,```, onde a vírgula se torna delimidador, como em arquivos CSV; 
	- ```-F'</td>'``` com aspas simples, para mais de um elemento, como divisões de tabelas HTML.

### paste
- retorna uma comparação linha a linha de dois arquivos fornecidos em paralelo, juntando conteúdos de arquivos;

	- ```$ paste -d, FILE FILE``` une dois arquivos incluindo ',' como delimitador de campos.

### split
- divide um arquivo fornecido em vários arquivos com padrão de nomes fornecido a seguir;
- **opções:**
    - '-l N' divide o arquivo em arquivos de 'N' linhas;
	- '-b N' divide o arquivo em arquivos de 'N' bytes;
	- '-d PATTERN' numera os arquivos resultantes seguindo um padrão;
- se o parâmetro '-l' não for definido, o split separa por padrão em arquivos com 1000 linhas.

### od
- 'octal dump' retorna o conteúdo do arquivo fornecido em formato octal; 
- **opções:**
	- '-x' retorna em hexadecimal; frequentemente usado com '-tx'.
	- '-c' retorna caracteres que normalmente não são visíveis, feito marcas de quebra de linha '\n';
	- '-An' oculta a primeira coluna de deslocamento de bytes.

### iconv
- comando que permite converter a codificação de caracteres de um arquivo de texto:
 ```$ iconv -f ISO-8859-1 -t UTF-8 original.txt > converted.txt```, em que '-f' = from e -t = to;
- a opção '-l' ou '--list' lista as codificações suportadas;
- a opção '-o' ou '--output' pode ser usada no lugar do redirecionamento.

### grep
- localizador de padrões;
- **opções:**
	- '-i' ignora a propriedade case sensitive;
	- '-v' diferente do 'verbose' da maioria dos casos, com 'grep' essa opção
	retorna quaisquer linhas, exceto as que tiverem o padrão de caracteres que segue 
	a opção;
	- '-c' conta e retorna a quantidade de linhas em que um padrão de caracteres
	ocorre no arquivo fornecido;
	- '--color' destaca as ocorrências que o 'grep' encontra; pode-se usar o alias
	'grep='grep --color';
	- '-E' permite estender metacaracteres em expressões regulares;
	- 'egrep' equivale a 'grep -E';
	- 'fgrep' impede expressões regulares.

- **caracteres especiais para expressões regulares:**
- Atoms
	- **.** \(ponto) representa qualquer caractere, independente de sua natureza, exceto quebra de linha;
	- **^** \(circunflexo) sinaliza o início de uma linha;
	- **$** sinaliza o final de uma linha;
- Brackets
	- expressões em colchetes formam um átomo, normalmente constituídos de uma lista:
	- **\[]** \(colchetes) delimita uma lista de caracteres que podem ocupar uma mesma posição em um padrão:
		- '\[1b]' delimita um espaço que pode ser ocupado seja por '1' ou 'b';
		- '\[0−9]' ou '\[a-z]' com '-' representando um intervalo de zero a nove ou de 'a' a 'z';
		- '\[:alnum:]' corresponde a um caractere alfanumérico;
		- '\[:alpha:]' corresponde a um caractere alfabético;
		- '\[:ascii:]' caractere ASCII;
		- '\[:blank:]' espaço ou tabulação;
		- '\[:lower:]' ou '\[:upper:]' minúsculo ou maiúsculo;
		- '\[:space:]' espaço, alimentação de formulário \(\f), nova linha \(\n), retorno de carro \(\r), tabulação horizontal \(\t) e tabulação vertical \(\v);
		- '\[:xdigit:]' hexadecimal de '0' a 'f'.
	- **\[^]** \(circunflexo em colchetes) representa a negação dos caracteres na lista:
		- '\[^1b]' delimita um espaço que exclui '1' ou 'b'.
	- **\*** \(asterisco) representa a ocorrência de um caracter precedido de 0 a n vezes;
	- **+** sinaliza que uma ocorrência aparece uma ou mais vezes;
	- **?** \(interrogação) sinaliza que o caractere imediatamente anterior é opcional;
	- **{n}** \(chaves) sinaliza o número 'n' de vezes que um átomo precedido pode ocorrer;
		- '{n,}' sinaliza que o átomo precedido deve ocorrer ao menos 'n' vezes;
		- '{n1,n2}' sinaliza que deve ocorrer entre 'n1' e 'n2' vezes.
	- **|** pipes, em expressões regulares, têm o valor de um operador lógico de alternância;

- **exemplos de uso:**
	- ``` $ grep -E '(root){3}' /tmp/passwd_copy ``` retorna as linhas em que a sequência de caracteres 'root' ocorre exatamente três vezes aglutinadas;
	- ``` '(root){3,}' ``` retorna ocorrências aglutinadas três ou mais vezes;
	- ``` 'o{2}t' ``` retorna ocorrências aglutinadas duas vezes de 'o' seguidas de 't' \(oot).

### sed
- editor de fluxo de texto simples.
- **opções e parâmetros:**
	- retornar uma linha com um padrão:

		- ```$ sed -n /PATTERN/p FILENAME ```

	- localizar e substituir primeira ocorrência na linha:

		- ```$ sed s/conteúdo/novo_conteúdo/ /caminho/do/arquivo ```
		- ```$ sed s|conteúdo|novo_conteúdo| /caminho/do/arquivo```

	- incluir número da posição para trocar outra ocorrência:

		- ```$ sed s|conteúdo|novo_conteúdo|2 /caminho/do/arquivo ```

	- incluir 'g' para substituir tudo:

		- ```$ sed s/conteúdo/novo_conteúdo/g /caminho/do/arquivo ```

	- substituir dados para um novo arquivo:

		- ```$ sed -i.backup s/conteúdo/novo_conteúdo/ /caminho/do/arquivo ```

	- deletar da linha 1 até a linha 25 linha:

		- ```$ sed -i 1,25 /caminho/do/arquivo ```

- **exemplos de uso:**

	- com o comando 's' \(buscar e substituir), localizar ocorrências de 'nologin' no final de cada linha, representado por '$', e substituir por 'REGEX FOUND', no arquivo '/tmp/passwd_copy':

		- ``` # sed 's/nologin$/REGEX FOUND/' /tmp/passwd_copy ```

	- permitir um agrupamento de caracteres na posição da referência de busca 'false|nologin' \(em que o pipe '|' representa o operador 'or'), para substituir qualquer ocorrência de 'false' ou 
	'nologin' no final de cada linha por 'INVALID SHELL':

		- ``` # sed -E 's/(false|nologin)$/INVALID SHELL/' /tmp/passwd_copy ```

	- substituir o '$' cifrão pelo '^' circunflexo no início do agrupamento de caracteres para sinalizar que qualquer ocorrência de 'root' ou 'daemon' ou 'www-data' no início de uma linha deverá ser substituída por 'REGEX'; a saída da expressão terá linhas numeradas pelo comando 'nl':

		- ``` # sed -E 's/^(root|daemon|www-data)/REGEX/' /tmp/passwd_copy | nl```

	- buscar sequências de caracteres que se iniciem por qualquer letra entre 'a' e 'f' minúsculos no começo de cada linha, seguidas de mais dois caracteres quaisquer:

		- ``` 's/^[a-f]../REGEX/g' ```

	- substitir as sequências de até 3 caracteres no início de cada linha que NÃO se iniciem por qualquer letra minúscula entre 'a' e 'f':

		- ``` 's/^[^a-f]../REGEX/g' ``` 

------------------------------------------------------------

## PRINTING

### lpadmin
- comando legado para gerenciamento de impressão e adição de impressora;
- **opções:**
	- '-p' destino do trabalho de impressão \(nome da impressora);
	- '-L' define a localização física da impressora entre aspas;
	- '-v' define a URI do dispositivo;
	- '-E' habilita o dispositivo;
	- '-d' para fornecer o nome de uma impressora padrão;
	- '-D' para inserir uma descrição;
	- '-P' para inserir o caminho para o driver;
	- '-m' define o modelo da impressora, para o CUPS determinar o arquivo PPD para usar;
	- '-p PRINTER -o printer-is-shared=true' permite compartilhar uma impressora na rede;
	- '-p PRINTER -u allow:USER1,USER2,USER3' especifica usuários que podem executar trabalhos de impressão;
	- '-p PRINTER -u deny:USER' especifica usuário que não pode executar trabalhos de impressão; grupos podem ser inseridos com o uso de '@';
	- '-p FRONT-DESK -o printer-error-policy=retry-job' permite definir uma política de erro, como tentar novamente uma impressão; outras opções são:
		- 'abort-job'
		- 'stop-printer'
		- 'retry-current-job'
	'-x' seguido do nome da impressora remove uma impressora, semelhante ao '**cupsreject -r**'.

### lpinfo
- comando que lista os arquivos PPD instalados;
- a opção '-v' mostra mais detalhes;
- a opção '-m' exibe drivers.

### lpoptions -d PRINTER
- define uma impressora padrão, como o 'lpadmin -d'.

### lpstat
- comando que retorna impresoras disponíveis com a opção '-p';
- a opção '-t' exibe maiores detalhes;
- a opção '-v' exibe conexões usadas pelas impressoras;
- a opção '-d' exibe a impressora padrão.

### lpr
- 'Line Printer Remote' é o comando para imprimir um arquivo fornecido a seguir;
- a opção '-P' permite escolher a impressora para cuja fila enviar o arquivo;
- a opção '-o' habilita subopções de modo de impressão:
	- landscape: modo paisagem;
	- two-sided-long-edge: retrato duplex;
	- two-sided-short-edge: paisagem duplex;
	- media=: seguido de 'A4', 'Letter', 'Legal', 'DL', 'COM10' permite selecionar o tamanho do papel;
	- collate=: agrupa documento com os valores 'true' ou 'false';
	- page-ranges: permite selecionar páginas ou intervelo de páginas;
	- fit-to-page: redimensiona o arquivo para caber no papel;
	- outputorder=: imprime na ordem 'reverse' ou 'normal';
- '-#N' define o número de cópias com 'N'.

### lp
- versão mais simples do lpr.

### lpq
- comando que exibe a lista da fila de impressão;
- com a opção '-a', exibe-se a fila de todas as impressoras e o ID do trabalho na coluna 'Job';
- com a opção '-P' e uma impressora fornecida a seguir, exibe a fila de impressão respectiva.

### lprm JOB_ID
- comando que exclui um trabalho de impressão cujo ID de trabalho seja fornecido;
- a opção '-P' permite especificar a impressora pelo nome;
- um hífen '-' no lugar do ID exclui todos os trabalhos da impressora padrão;
- '**cancel**' é um comando alternativo do CUPS para a mesma finalidade, seguido do nome da impressora e do ID do trabalho, separados por um traço.

### lpmove
- comando que move um trabalho de uma fila de impressão para outra, ao se fornecerem o nome da impressora, o ID do trabalho após um traço e o nome da impressora destino após um espaço.

------------------------------------------------------------

## FILE HANDLING

### file 
- retorna o tipo de um arquivo cujo caminho for fornecido a seguir.

### cd 
- muda o diretório corrente;
- **opções:**
    - .. equivale ao diretório pai;
    - ~ equivale ao diretório home do usuário ou /root;
    - \- equivale ao diretório anteriormente visitado.

### mv 
- move ou renomeia arquivos e diretórios;
- **opções:**
    - '-i' interactive: pede confirmação para sobrescrever;
    - '-f' force: força sobrescrever;
    - '-v' verbose: mostra o processo.

### cp 
- copia arquivos e diretórios;
- **opções:**
    - '-i', '-f' e '-v' equivale aos mesmos em 'mv';
    - '-r', '-R' ou '--recursive' copiam inclusive arquivos e subdiretórios de um diretório;
    - '-b' backup: cria uma cópia de segurança dos arquivos que eventualmente sejam substituídos no diretório de destino;
    - '-a', '-d', '-p': preservam as propriedades do arquivo, como data de modificação e permissões.

### mkdir
- cria diretórios;
- **opções:**
    - '-v' equivale ao mesmo em 'mv';
    - '-m' mode: permite definir permissões do novo diretório;
    - '-p' parents ou path: permite criar diretórios pais até o diretório desejado.

### rm 
- remove arquivos e diretórios;
- **opções:**
    - '-i', '-f' e '-v' equivale aos mesmos em 'mv';
    - '-R', '-r' incluem arquivos e diretórios filhos à remoção de um diretório.

### rmdir 
- remove diretórios vazios;
	- '-p' remove o diretório com subdiretórios especificados.


### ls
- comando básico para listar conteúdo de diretórios;
- **opções:**
	- '-l' exibe os resultados em forma de lista;
	- '-a' exibe todos os arquivos, incluindo ocultos;
	- '-h' exibe dados de forma humanizada;
	- '-d' exibe atributos de arquivos para um diretório fornecido, em vez de listar seu conteúdo;
	- '-i' exibe inodes dos arquivos.

- o comando '**ls -la**' retorna uma coluna com símbolos alfabéticos representando o tipo do arquivo e as permissões de:
	- 'u' usuário, 
	- 'g' grupo, 
	- 'o' outros;
- **tipos de arquivo:**
	- '-' arquivo normal;
	- 'd' diretório;
	- 'l' link simbólico - symlink;
	- 'b' dispositivo de bloco;
	- 'c' dispositivo de caracter, que pode ser a representação de um dispositivo virtual ou físico;
	- 's' socket;
- **permissões:**
	- '-' nenhuma permissão; octal 0;
	- 'x' execução; para diretórios, permite abrir o diretório; octal 1;
	- 'w' gravação, escrita; octal 2;
	- 'r' leitura; octal 4.
	- **permissões especiais:**
		- 't' **Stick Bit** substitui 'x' em outros; octal 1:
			- reforça a propriedade exclusiva do usuário sobre arquivos criados no diretório, impedindo a exclusão por outros usuários;
		- 's' **Set GID** substitui 'x' em grupo; octal 2:
			- aplicado a diretórios, faz com que arquivos criados no diretório herdem o grupo do diretório no lugar do grupo do usuário;
		- 's'  **Set UID** substitui 'x' em usuário; octal 4:
			- dá aos usuários as permissões de execução de arquivos a outros usuários.

### tar *options directory*
- arquiva diretórios e seus respectivos conteúdos em pacotes \*.tar;
- **opções para empacotamento:**
    - '-c', '--create' criam o arquivo \*.tar;
    - '-v' verbose para exibir cada arquivo que será incluído;
    - '-p' para preservar as propriedades dos arquivos a serem arquivados;
    - '-f' para especificar o nome do arquivo \*.tar com o que for digitado a seguir;
    - normalmente, todas as opções acima são usadas combinadas em '-cvpf';
    - outro uso comum é a combinação do empacotamento com a compressão:
        - com gzip: '-z' em '-czvf';
        - com bzip2: '-j' em '-cjvf'
    - '-tf' exibe a lista dos arquivos que foram arquivados no pacote especificado;
- **opções para desempacotamento:**
    - '-x', '--extract' opção para desempacotar, normalmente usada na combinação '-xvf', o nome do arquivo \*.tar, '-C' para em seguida especificar o diretório destino;
    - para desempacotar e descompactar: '-xzvf' ou '-xjvf'.

### gzip
- comprime arquivos em arquivos \*.gz;
- **opções:**
    - '-d' para descomprimir com gzip;
    ou usar **gunzip** sem opções, para descompactar sem precisar de opções;
    - '-c' para comprimir e manter o arquivo original, com a sintaxe:
    	- ```$ gzip -c file.tar > finalfile.tar.gz ```

### bzip2
- comprime arquivos com compressão maior, em arquivos \*.bz2;
    - usa-se **bunzip2** para descomprimir;
    - '-k' é a opção que substitui o '-c' do *gzip*.

### xz
- comprime arquivos com maior taxa de compressão dos três, em arquivos \*.xz;
    - usa-se **unxz** para descomprimir;
    - assim como no *bzip2*, o *xz* mantém o arquivo original com a opção '-k'.

### cpio
- também usado para empacotar e desempacotar arquivos, análogo ao *tar*, podendo gerar pacotes \*.cpio \*.tar.
- sua sintaxe demanda receber o output de comandos como o 'ls', que lista arquivos para serem direcionados para o input do *cpio* com o pipe:
    ```$ ls | cpio -o > arquivo.cpio```
- para extrair os arquivos, usa-se:
    ```$ cpio -id < arquivo.cpio```

### dd
- faz cópias de arquivos byte a byte;
- **sintaxe:**
	- ```$ dd if=oldfile of=newfile ```

- exemplo:

	- ```$ dd status=progress if=/dev/zero of=image.iso bs=1M count=1024```

		- em que 'if' significa input file;
		- 'status=progress' opcional e exibe o andamento do processo, opção sem a qual o comando não exibe coisa agluma até finalizar;
		- '/dev/zero' exemplifica o arquivo de entrada usando o arquivo 'zero';
		- 'of' significa output file;
		- 'bs' para informar a quantidade de bytes por segundo; aqui a unidade está especificada em megabytes, mas sem especificação a unidade usada é byte;
		- 'count' contando a quantidade de segundos, que aqui resulta num arquivo de 1GB.

- como exemplo, pode-se usar esse comando para copiar um hd inteiro, cum sua lista de partições, com a sintaxe:

	- ```$ dd if=/dev/sda of=hd.mbr bs=4096	```

- para restaurar: 

	- ```$ dd if=hd.mbr of=/dev/sda bs=4096	```

### ln
- comando para criar links;
- sintaxe: ```ln TARGET LINK_NAME```, em que:
	- 'TARGET' é o destino para onde o link aponta;
		- sem opçẽs, o 'ln' cria um **hardlink**, que se baseia em 'inodes' \(index nodes);
	- 'LINK_NAME' é o nome do link;
	- com a opção '-s', o 'ln' cria um **symlink** ou **soft link** \(link simbólico) que, para poder ser movido, 
precisa que o TARGET seja o caminho completo e exato para onde o symlink aponta.

### locate
- comando que realiza busca por padrões fornecidos através do banco de dados '/var/lib/mlocate.db', gerado pelo updatedb;
- **sintaxe de exemplo:** ```$ locate jpg ```;
- **opções:**
	- '-i' ignora maiúsculas e minúsculas;
	- '-A' refina por resultados que contenham todos os padrões fornecidos separados por espaço;
	- '-c' conta e retorna o número de vezes que um padrão ocorre;
	- '-e' verifica se um item de '/var/lib/mlocate.db' ainda existe antes de exibir.

### updatedb
- comando que atualiza o banco de dados '/var/lib/mlocate.db';
- seu comportamento é controlado por '/var/lib/mlocate.db', cujas linhas contém:
	- 'PRUNEFS=' todos os tipos de sistema de arquivos listados a seguir, separados por espaço, serão ignorados pelo updatedb;
	- 'PRUNENAMES=' diretórios separados por espaço que não serão analisados;
	- 'PRUNEPATHS=' caminhos que devem ser ignorados;
	- 'PRUNE_BIND_MOUNTS=' com 'yes' ou 'no', define se as bind mounts serão ignoradas.

### md5sum
- retorna o registro hash da última alteração de um arquivo fornecido.
- outputs a 32-character hexadecimal number.

### sha256sum
- algoritmo aprimorado do comando anterior.
- outputs a 64-character hexadecimal number.

### sha512sum
- algoritmo aprimorado do comando anterior.
- outputs a 128-character hexadecimal number.

### find STARTING_PATH OPTIONS EXPRESSION
- busca arquivos de acordo com opções específicas;
- **opções:**
    - '-name': opção case-sensitive para procurar pelo nome dos arquivos;
    - '-iname': opção para buscar sem case-sensitive;
    - '-type': filtra por tipo:
		- 'f': opção para arquivos;
		- 'd': opção para diretórios;
        - 'l': opção para links simbólicos;
        - 'b': opção para o tipo block;
    - '-cmin': filtra por arquivos que tiveram status alterado \(chmod):
        - '+3': para alterados há mais de três minutos;
        - '-3': para alterados há menos de três minutos;
    - '-ctime': filtra por arquivos que tiveram status alterado há 'N' * 24h \(N dias);
    - '-amin': arquivos acessados há 'N' minutos;
    - '-atime': arquivos acessados há 'N' * 24h;
	- '-amin N', '-cmin N', '-mmin -N' filtra por arquivos acessados, com atributos alterados ou modificados, respectivamente, há 'N' minutos;
	- '-maxdepth N' define a profundidade máxima numa árvore de diretórios, em que 'N' será o nível máximo;
	- '-mindepth N' é o inverso, pesquisando a partir de uma profundidade fornecida em 'N';
	- '-size +NM' para filtrar por arquivos maiores que 'N' megabytes, em que 'M' pode ser substituído por 'c' para bytes, 'k' para kilobytes ou 'G' para gigabytes;
	- '-not' retorna o que não corresponde ao critério de busca;
	- '-exec' após o critério de busca permite executar um comando fornecido a seguir com os resultados obtidos;
	- '-executable' o mesmo do anterior para arquivos com permissão de execução;
	- '-writable' o mesmo do anterior para arquivos com permissão de escrita;
	- '-readable' retorna apenas arquivos com permissão de leitura para o usuário que está buscando;
	- '-empty' filtra por arquivos e diretórios vazios;
	- '-mount' exclui dispositivos montados da busca;
	- '-fstype' seguido de um tipo de sistema de arquivos restringe a busca a eles;
	- '-user USERNAME' retorna apenas resultados com arquivos de 'USERNAME';
	- '-group GROUPNAME' retorna apenas resultados com arquivos do 'GROUPNAME';
	- '-delete' exclui os arquivos do resultado da busca;
	- **permissões especiais**:
		- ```-perm numeric-value``` ou ```-perm symbolic-value``` exclusivamente;
		- ```-perm -numeric-value``` ou ```-perm -symbolic-value``` inclusivamente;
		- ```-perm /numeric-value``` ou ```-perm /symbolic-value``` qualquer permissão especial;
		- em que 'numeric-value' pode ser 4000 para SUID ou 2000 para SGID ou /6000 para qualquer; e symbolic-value u+s ou g+s.

------------------------------------------------------------

## REDIRECTS

### xargs
- transforma comandos em argumentos de outros programas;
- **exemplos**
	- passar o output de 'find' como argumento de 'ls -l';

		- ```$ find /usr/sbin -iname 'i*' | xargs ls -l ```

	- com a opção '-i' no 'xargs', o programa preenche todas as chaves com o output do primeiro comando antes do pipe; a opção '-c' em 'bash' permite executar comandos colocados entre as aspas:

		- ```$ find /etc -iname '*.conf' -maxdepth 1 | xargs -i bash -c "echo listando o arquivo de configuração {}; ls -l {}" ```

### tee
- permite visualizar e salvar em um arquivo o stdout de um programa
em um redirecionamento.

### | Pipe
- redireciona a saída (std-output) de um comando para a entrada (std-input) do que se seguir, trabalhando portanto da esquerda para a direita.

### \< Less Than - STDIN
- entrada de dados padrão, equivale a **'0>'**;
- exemplo:
```
# cat </etc/shadow
```
exibe o conteúdo de shadow;

### \> Greater Than - STDOUT
- saída de dados padrão, equivale a **'1>'**;
- redireciona a saída para um arquivo, cujo nome deve seguir o símbolo, e então o cria ou sobrescreve;
- **>>** uma vez duplicado, o maior que adiciona a saída para o final do arquivo (append - apensar), mas também cria o arquivo, caso não exista.

- exemplos:

	- toda a saída de 'processo' é direcionada para o 'arquivo' que, caso não exista, é criado:

		- ```$ processo > arquivo ``` 

	- o conteúdo do output do cat é redirecionado para o novo arquivo.

		- ```# cat /etc/apt/sources.list 1>/home/user/copy.sources.list ```


	- para não sobrescrever o arquivo de destino, pode-se habilitar o noclobber no bash com:
		- ```$ set -o noclobber``` ou ```$ set -C```; 
		- desabilita-se com: ```$ set +o noclobber``` ou ```$ set +C```

### 2> 2>> STDERR
- saída de erro padrão, equivale a '2>'.

### Here Document and Here String
- Here Document permite redirecionar várias linhas para um documento ou comando, até o termo de fim 'EOF':

	```
$ test.txt <<EOF
> string line 1
> string line 2
> EOF
	```

- Here String permite redirecionar uma linha para um documento ou comando:
	- ```$ test.txt <<<"string line 1" ```

### & Ampersand
- executa um comando em segundo plano;
- combinado a um redirecionador, alude aos descritores de arquivo 1 e 2 simultaneamente, permitindo operações com o stdout e stderr em conjunto, feito em:
	- ``` &> ``` ou ```>&```;
- combinado a um dos descritores de arquivo permite redirecionamentos de um descritor para outro:
	- ``` 1>&2 ``` redireciona o stdout para o stderr; o inverso se expressa com: ``` 2>&1```.

------------------------------------------------------------

# SYSTEM ADMINISTRATION

## SYSTEM BASE

### lspci
- lista componentes PCI conectados e seus endereços hexadecimais;
- opções: 
	- '-s DEVICE_ADDRESS_NUM -v' detalhes ainda maiores de um dispositivo cujo endereço hexadecimal seja fornecido.
	- '-s DEVICE_ADDRESS_NUM -k' mais detalhes de driver (kernel module).
	
### lsusb
- lista dispositivos USB conectados e seus ID's;
- opções:
	- '-v -d ID' retorna detalhes a respeito de um dispositivo especificado;
	- '-t' retorna os dispositivos em árvore por barramento.

### lsmod
- lista os módulos de kernel em uso, com as colunas: 
	MODULE: descrição do módulo;
	SIZE: mostra a quantidade de RAM em bytes;
	USED BY: módulos dependentes.

### modprobe
- comando para carregar ou descarregar módulos do kernel;
- **sintaxe:** 
	- ```# modprobe -r MODULE_NAME```.

### dmesg
- exibe o conteúdo do 'kernel ring buffer', mantido no arquivo '/var/log/dmesg', onde ficam armazenadas as mensagens de carregamento do kernel.
	- '--clear' opção que apaga o conteúdo;
	- '-H' ou '--human' habilitam a paginação por padrão, dispensando o '| less'.

- NOTA: o arquivo '/var/log/messages' também armazena informações úteis a respeito de logs; todos esses arquivos também podem ser exibidos usando comandos como 'less' ou 'tail'.

### journalctl
- utilitário que exibe os registros de log gerados pelo 'systemd-journald', os quais são armazenados em diários binários;
- **opções:**
	- '-r' exibe as mensagens em ordem reversa;
	- '-f' retorna as mensagens mais recentes enquanto estiver em execução, equivalente a 'tail -f';
	- '-e' salta para o final do diário;
	- '-n N' e '--lines=N' exibem as N linhas mais recentes, sendo 10 o padrão quando não fornecido valor;
	- '-k' e '--dmesg' exibem mensagens do anel do kernel, equivalente a dmesg;
	- '-p' filtra por prioridade ou gravidade;
	- '-b -N' ou '--boot -N' filtram por inicializações anteriores fornecidas em '-N'; sem fornecer '-N' retornam o boot atual;
	- '--list-boots' lista inicializações registradas, com o número da inicialização \(0 para a atual e -1, -2, -3 etc. para anteriores), respectivos IDs e marcas de tempo;
	- '--since' e '--until' permitem fornecer um intervalo de tempo, que pode ser dado por expressões numéricas ou palavras-chave como 'yesterday', 'today', 'tomorrow', 'now';
	- '-u' filtra por unidade fornecida;
- pode-se filtrar o resultado por um programa passando seu caminho absoluto;
- por campo específico:
	- _PRIORITY= seguido de um dos 8 valores possíveis de syslog;
	- _SYSLOG_FACILITY= valores de código de recurso;
	- _PID= por PID de processo;
	- _BOOT_ID= ID de inicialização;
	- _TRANSPORT= transporte específico, como journal, syslog, stdout, kernel etc.;
- pode-se verificar o uso de disco pelo armazenamento de logs com a opção '--disk-usage'.

### logger
- comando que gera mensagem de log, util para testes e scripts;
- a opção '-p' permite definir o recurso \(facility) e a prioridade, conforme o arquivo de configuração do rsyslog, '/etc/rsyslog.conf';
- a opção '-t' permite inserir uma tag;
- tanto a mensagem quanto a tag são passadas entre aspas.

### systemd-cat
- equivalente systemd ao logger, normalmente concatenado com echo;
- ```$ systemd-cat -p emerg echo "This is not a real emergency."```.


### shutdown
- comando que envia os sinais SIGTERM e SIGKILL a todos os processos;
- quando as opções '-h' e '-r' não são usadas, o sistema alterna para o nível 1 de execução;
- o parâmetro 'time' é obrigatório e recebe valores como hora exata para desligamento no formato 'hh:mm', '+m', em que 'm' é o valor em minutos, ou ainda 'now' ou '0', para desligamento imediato;
- **opções:**
	- '-h' encerra o sistema;
	- '-r' reinicia o sistema;
	- '-F' força a checagem do sistema de arquivos durante o boot;
	- '-c' cancela uma programação de shutdown configurada.

### wall
- comando exclusivo de super-usuários que exibe uma mensagem para todos os usuários logados durante o desligamento, com a sintaxe:
	- ```# wall <<<"message"```
ou
	- ```# wall /path/to/file/to/show```

### ldd */absolut/path/to/bin*
- comando que exibe as bibliotecas de que um binário depende, com as quais ele possui vinculação dinâmica.

### ldconfig
- comando que gera o arquivo '/etc/ld.so.cache' a partir dos dados do arquivo '/etc/ld.so.conf', que contém o caminho para o diretório com links simbólicos de cada biblioteca;
- com a opção '-p' ou '--print-cache', o 'ldconfig' exibe o conteúdo de '/etc/ld.so.cache';
- além de mapear bibliotecas com 'ldconfig', pode-se incluir caminhos para bibliotecas com a variável 'LD_LIBRARY_PATH=/usr/local/mylib'.

### objdump
- utilitário que retorna informações sobre arquivos objeto;
	- '-p' ou '--private-headers' retorna dados de cabeçalho que podem ser filtrados com '| grep', feito NEEDED, SONAME etc..

------------------------------------------------------------

## PARTITIONS

### fdisk
- utilitário padrão para gerenciar partições MBR - Master Boot Record;
- para editar uma tabela de partição no disco 'sda':

	- ```# fdisk /dev/sda```

- **opções importantes:**
	- '-l' lista os discos ou partições em um disco fornecido;
	- 'm' menu de ajuda com as opções de interação do fdisk;
	- 'p' detalha informações a respeito do disco selecionado;
	- 'n' cria uma nova partição;
	- 'f' exibe o espaço ainda não alocado;
	- 'd' remove uma partição;
	- 't' seguido pelo número de uma partição permite alterar seu tipo; os tipos são identificados por códigos hexadecimais:
		- '83' para partições Linux;
		- '82' para partições Swap;
		- '8e' para partições Linux LVM;
		- '5' para partições estendidas;
		- para ver mais tipos de partições, usar a opção 'l';
	- 'q' sai do utilitário sem escrever nada em disco;
	- 'w' escreve as alterações em disco.

### gdisk
- utilitário para gerenciar partições GUID - GPT;
- para editar uma tabela de partição no disco 'sda':

	- ```# gdisk /dev/sda```

- **opções importantes:**
	- '?' ou 'h' para o menu de ajuda;
	- 'p' detalha informações a respeito do disco selecionado;
	- 'o' cria uma nova tabela de partições GUID - GPT;
	- 'n' cria uma nova partição;
	- 'l' exibe os tipos de partições suportados;
	- 'd' remove uma partição;
	- 't' seguido pelo número de uma partição permite alterar seu tipo; os tipos são identificados por códigos hexadecimais:
		- '8300' para partições Linux;
		- '8200' para partições Swap;
		- '8e' para partições Linux LVM;
		- para ver mais tipos de partições, usar a opção 'L';
	- 'q' sai do utilitário sem escrever nada em disco;
	- 'w' escreve as alterações em disco.
	
### mke2fs
- utiliário básico para a formatação em sistemas de arquivos ext;
- a sintaxe mke2fs básica é ```# mke2fs -t ext4 /dev/sda1```;
	- sem informar o tipo com '-t', o mke2fs formata ext2;
	- sem informar o tipo com a opção '-j', o mke2fs formata no primeiro formato com 'journal' ext3;
	- as configurações do 'mke2fs' podem ser verificadas no arquivo '/etc/mke2fs'.
	
### mkfs.ext4
- os utilitários mkfs.ext2, mkfs.ext3 e mkfs.ext4 são links simbólicos para padrões de funcionamento do formatador de sistema de arquivos **mke2fs**.
- a sintaxe de uso é ```# mkfs.ext4 /dev/sda1```;
- **parâmetros e opções:**
	- '-b SIZE' define o tamanho dos blocos, em que SIZE pode ser de 1024, 2048 ou 4096 por bloco;
	- '-c' verifica se a partição tem blocos defeituosos; '-c -c' faz uma verificação lenta;
	- '-d DIRECTORY' copia o conteúdo de um diretório específico para a raiz de um novo sistema de arquivos;
	- '-F' força a criação de um sistema de arquivos; '-F -F' força mesmo em dispositivos montados, apagando seu conteúdo original;
	- '-L VOLUME_LABEL' define um rótulo de volume de ao menos 16 caracteres;
	- '-n' modo teste que simula a criação de um sistema de arquivos;
	- '-q' modo silencioso, executa a formatação sem produzir saída para o terminal; útil para scripts;
	- '-V' modo verboso;
	- '-U' permite especificar UUID para uma partição; 'clear' limpa o ID existente, 'random' atribui um randômico e 'time' cria um UUID baseado em tempo.

### mkfs.xfs
- 'xfs' é o sistema de arquivos padrão  de distribuições feito RedHat 7;
- **opções:**
	- '-b size=VALUE' define o tamanho do bloco em bytes, sendo o mínimo 512, 4096 o padrão e 65536 o máximo;
	- '-m uuid=VALUE' define UUID da partição;
	- '-f' força a criação de um sistema de arquivos xfs;
	- '-l logdev=DEVICE' define o dispositivo da seção log;
	- '-l size=VALUE' define o tamanho da seção log;
	- '-q' modo silencioso;
	- '-L LABEL' define um rótulo no máximo 12 caracteres;
	- '-N' equivale ao '-n' de 'mke2fs', simulando a formatação.

### parted
- editor de partições para MBR e GPT;
- para editar uma tabela de partição no disco 'sda':

	- ```# parted /dev/sda```

- para mudar o disco selecionado:

	- ```# select /dev/sdb```

- **comandos:**
	- 'print' exibe as partições existentes no disco selecionado;
	- 'print devices' lista todos os dispositivos de bloco conectados ao sistema;
	- 'print all' exibe mas informações sobre os dispositivos;
	- 'print free' exibe o espaço livre nos dispositivos;
	- 'mklabel' cria uma tabela de partições, seguido do tipo:
		- 'mklabel msdos' para MBR;
		- 'mklabel gpt' para GPT;
	- 'mkpart' cria uma partição, seguindo a sintaxe: 'mkpart PARTTYPE FSTYPE START END', em que:
		- PARTTYPE é o tipo, que pode ser 'primary', 'logical' ou 'extended', no caso MBR;
		- FSTYPE é o rótulo do sistema de arquivos - 'file system';
		- START é o ponto onde a partição se inicia, que pode ser dado como:
			- '2s' para o segundo setor,
			- '1m' para o primeiro megabyte,
			- '1024B' para a quantidade em bytes ou
			- '0%' para o percentual de disco;
		- END especifica o ponto onde a partição termina, usando as mesmas unidades de START;
	- 'rm' remove a partição cujo número for fornecido a seguir;
	- 'rescue START END' recupera uma partição acidentalmente removida, informando os pontos aproximados de início e fim;
	- 'resizepart PARTNUMBER NEWEND' redimensiona uma partição desmontada e com espaço livre após seu final;
		- uma vez redimensionada, a partição precisa ter seu sistema de arquivos ampliado com o utilitário 'resize2fs':
			``` $ sudo resize2fs /dev/sdb3 ```
		- o procedimento inverso, com resize2fs e resizepart reduz uma partição;

		- ```# resize2fs /dev/sdb3 90m ```
		- ```# parted /dev/sdb3	```
		- ``` resizepart 3 300m	```
	- 'quit' para sair do utilitário.

------------------------------------------------------------

## FILE SYSTEMS

### du
- comando que retorna quantos blocos de 1 kilobyte estão sendo usados pelo diretório atual e pelos seus subdiretórios;
- **opções:**
	- '-h' retorna uma descrição mais humanizada, em megabytes, gigabytes etc.;
	- '-a' retorna uma contagem individual para cada arquivo contido no diretório e subdiretórios;
	- '-S' retorna o espaço utilizado pelo diretório atual menos os subdiretórios;
	- '-Sc' inclui o total;
	- '-dN' define a profundidade dos resultados, em que 'N' é um inteiro com a profundidade;
	- '--exclude="PATTERN"' exclui arquivos da contagem em que 'PATTERN' é o padrão a ser correspondido, por exemplo:
	```$ du -ah --exclude="*.bin" ``` exclui da contagem todos os arquivos da extensão '\*.bin'.

### df
- comando que retorna uma lista de dados dos sistemas de arquivos montados;
- **opções:**
	- '-h' retorna uma descrição mais humanizada, em megabytes, gigabytes etc.;
	- '-i' retorna por inodes, em vez de blocos;
	- '-T' inclui uma coluna com o tipo do sistema de arquivos de cada dispositivo montado;
	- '-t' filtra os resultados por um determinado tipo de sistema de arquivos fornecido;
	- '-x' filtra os resultados excluindo os dispositivos de um determinado tipo fornecido;
	- '--output=FIELD' seleciona os campos de colunas que se desejam no retorno, separados por vírgula:
		- ``` $ df -h --output=target,source,fstype,size,used,avail,pcent ``` retorna as colunas equivalentes;
		- outros campos podem ser: itotal, iused, iavail e ipcent, que retornam resultados por inode.

### fsck
- utilitário de verificação e correção do sistema de arquivos;
- sua sintaxe é ```# fsck /dev/sdb1 ```;
- o fsck deve ser usado somente em sistemas de arquivos não montados, sob pena de perda de dados;
- sem especificar o sistema de arquivos, o fsck chama o e2fsck, próprio para sistemas do tipo ext2/3/4;
- **opções:**
	- '-t' especifica o tipo do sistema de arquivos da partição fornecida a seguir;
	- '-A' verifica todos os sistemas de arquivos listados em '/etc/fstab';
	- '-C' exibe uma barra de progresso no caso dos sistemas ext2/3/4;
	- '-N' modo de teste, que apenas simula a verificação;
	- '-R' com '-A', pula a verificação do sistema de arquivos raiz;
	- '-V' modo detalhado, verboso;
	- '-p' tenta corrigir automaticamente os erros;
	- '-y' responde 'yes' a todas as interações;
	- '-n' oposto de '-y';
	- '-f' força a verificação.

### tune2fs
- utilitário de verificação e ajuste de parâmetros dos sistemas de arquivo ext2/3/4;
- sintaxe: ```# tune2fs -l /dev/sda1```;
- **opções:**
	- '-l' lista os parâmetros de uma partição;
	- '-c N' altera a contagem máxima de montagens até a próxima verificação automática, em que 'N' é o número de montagens;
	- '-C N' altera o status da contagem atual;
	- '-i' define o intervalo de tempo para verificações, com sub-opções feito '-i 1d' para dias, '-i 1m' para meses e '-i 1y' para anos;
	- '-L' define um rótulo de até 16 caracteres para o sistema de arquivos;
	- '-U' define um UUID;
	- '-m' define o percentual do sistema de arquivos exclusivo para operações com root;
	- '-e' define um comportamento do kernel quando um erro é encontrado, sendo possíveis:
		- 'continue' para continuar a execução normalmente;
		- 'remount-ro' para remontar como somente leitura, evitando mais erros;
		- 'panic' para causar um 'kernel panic';
	- '-j' acrescenta o recurso 'journal' a um sistema de arquivos ext2, convertendo-o em um ext3;
	- '-J' permite definir opções do uso do 'journal':
		- '-J size=' define o tamanho do diário em megabytes;
		- '-J location=' permite especificar o local do armazenamento do diário;
		- '-J device=' permite selecionar o dispositivo onde armazenar o diário;
		- podem-se especificar diversos parâmetros simultaneamente separados por vírgula;
	- '-f' força a completar uma operação, mesmo que sejam encontrados erros; cautela!
	
### xfs_repair
- é o equivalente ao fsck para o sistema de arquivos XFS;
- sintaxe: ```# xfs_repair -n /dev/sdb1 ```;
- **opções:**
	- '-n' verifica se há erros, sem ações de reparação; caso haja erros, executar o utiliário sem o parâmetro para corrigir;
	- '-v' modo verboso; '-v -v' ainda mais detalhes são exibidos;
	- '-d' modo dangerous, para reparar sistemas montados como somente leitura;
	- '-m N' permite limitar em N megabytes o uso de memória pelo utilitário;
	- '-l LOGDEV' e '-r RTDEV' para sistemas com logo externo e seções em tempo real.

### mount
- utilitário para montagem de sistemas de arquivos;
- sintaxe: ```# mount -t TYPE DEVICE MOUNTPOINT ```;
- usando apenas 'mount', retorna uma lista de todos os sistemas de arquivo montados;
- **opções:**
	- '-t' indica que o próximo dado é o tipo do sistema de arquivos:
		- '-t TYPE' retorna dispositivos montados com um tipo fornecido;
		- pode-se informar vários separados por vírgula;
	- '-a' monta todos os sistemas de arquivos listados em '/etc/fstab';
	- '-r' ou '-ro' monta como somente leitura;
	- '-w' ou '-rw' monta como gravável;
	- '-o' ou '--options' precede uma lista de opções de montagem separadas por vírgula;
		- 'atime' e 'noatime': habilita ou desabilita a informação de hora de acesso;
		- 'auto' e 'noauto': habilita ou desabilita a montagem automática com 'mount -a';
		- 'defaults': passa 'rw', 'suid', 'dev', 'exec', 'auto', 'nouser' e 'async' para mount
		- 'dev' e 'nodev': os dispositivos de caractere ou de bloco devem ou não ser interpretados;
		- 'exec' e 'noexec': permite ou não a execução de binários;
		- 'user' e 'nouser': permite ou não a montagem por um usuário comum;
		- 'group': permite montagem por usuário do mesmo grupo;
		- 'owner': permite montagem apenas ao proprietário do dispositivo;
		- 'ro' e 'rw': define montagem somente leitura ou gravável;
		- 'remount': tentar remontar um sistema de arquivos já montado, como em ```# mount -o remount,ro /dev/sdb1```, 
		em que o sistema de arquivos é montado novamente como somente leitura; pode ser usado o ponto de montagem: ```# mount -o remount,ro /mnt/data```
- para desmontar um sistema de arquivos, usa-se **unmount**, seguido pelo nome do dispositivo ou do ponto de montagem;
- **opções para umount:**
	- '-a' desmonta todos os sistemas de arquivos listados em '/etc/fstab';
	- '-f' força a desmontagem;
	- '-r' se o sistema de arquivos não puder ser desmontado, torna-o somente leitura.
	
### lsof
- utilitário que, seguido do nome do dispositivo que contém um sistema de arquivos que não pôde ser desmontado, lista os arquivos que estão sendo usados nesse sistema de arquivos e quais processos os estão usando.
 - ```$ lsof /dev/sdd2 ```
- **lsof -i** lista arquivos usados pela rede da 'internet':
	- pode-se incluir o IP de um host para filtrar: 'lsof -i@192.168.1.7';
	- ou porta: 'lsof -i :22';
	- ou uma ou mais portas de um host específico: 'lsof -i@192.168.1.7:22,80';
	- **outras opções além de -i:**
		- '-u' filtra por um usuário fornceido a seguir;
		- '-c' filtra por um comando.

### lsblk
- utilitário que lista os sistemas de arquivos;
- a opção '-f' seguida do caminho de uma partição retorna as seguintes informações:
	- NAME: nome do dispositivo que contém um sistema de arquivos;
	- FSTYPE: tipo do sistema de arquivos;
	- LABEL: rútulo do sistema de arquivos;
	- UUID: identificador universal;
	- FSAVAIL: espaço disponível;
	- FSUSE%: porcentagem de uso;
	- MOUNTPOINT: onde é montado.

### blkid
- utilitário alternativo para exibir os sistemas de arquivos;
- com '-o list', os dados são organizados na tela.

------------------------------------------------------------

## PROCESS MANAGEMENT

### ps
- retorna um instantâneo dos processos da sessão atual;
- **opções:**
	- '-u username' retorna todos os processos para um usuário fornecido;
	- '-u username u' retorna todos os processos para um usuário, adicinando uma coluna descrevendo qual usuário iniciou o processo;
	- 'au' retorna todos os processos; caso a saída for muito longa, usa-se ```ps ua | less``` para o comando 'less' paginar a saída;
	- 'aux' inclui execuções do sistema;
	- 'auxf' indica com backslash \\ quais processos deram origem a outros processos;
	- 'axfl' adiciona uma coluna com o PID do processo 'pai' PPID;
	- para retornar dados de um determinado processo, pode-se filtrar seu nome com grep: 

		- ``` $ ps aux | grep -i processname ```

### pstree
-  retorna os processos em estrutura de árvore, feito o comando 'tree' para diretórios e arquivos;
	- 'pstree -p' inclui o PID dos processos.

### top
- um dashboard simples para monitoramento de processos no terminal;
- teclas para usar durante a execução do *top*:
	- 'z' altera a cor dos dados;
	- 'M' lista os processos que usam mais memória;
	- 'P' lista os processos que usam mais processamento;
	- 'L' permite digitar uma string com o nome de um processo a se localiar na lista;
	- 'q' para quit;
- **opções:**
	- *'-p PID'* mostra o processo pelo PID fornecido;
	- "'-u username'* mostra os processos de um determinado usuário.
	
### pgrep 
- retorna o PID do processo fornecido.

### pidof
- retorna o PID do processo somente quando o nome fornecido está exatamente como o do processo desejado.

### kill
- força encerrar um processo pelo respetivo PID fornecido;
- pode ser utilizado com sinais, os quais são exibidos com a opção '-l';
- quando nenhum sinal é fornecido, o *kill* usa o sinal *15 SIGTERM* \(-term ou -15) por padrão;
- o sinal *kill* propriamente dito é o *9 SIGKILL* \(-kill ou -9): encerra imediatamente;
- o sinal *1 SIGHUP* \(-hup ou -1) reinicia o processo com eventuais novas configurações de um arquivo de configuração;
- o sinal *2 SIGINT* \(-int ou -2) interrompe o processo, feito o ctrl+c;
- o sinal *3 SIGQUIT* \(-quit ou -3) fecha o processo;
- o sinal *18 SIGCONT* \(-cont ou -18) solicita que o processo termine;
- o sinal *19 SIGSTOP* \(-stop ou -19) interrompe processo em execução;
- processos de um usuário qualquer só podem ser encerrados por ele mesmo ou pelo root;
- costuma-se usar a substituição de comando com pgrep, quando não se sabe o PID do processo, usando a seguinte sintaxe:

	- ``` # kill -9 $(pgrep processname) ```.

### pkill
- encerra um processo sem o PID, quando o nome do processo é fornecido.

### killall
- encerra todas instâncias de um processo sem o PID, mas somente quando o nome exato do processo é fornecido.

### jobs
- exibe os processos em segundo plano, inclusive os iniciados com o caracter especial '&';
- **opções**
	- '-l' lista os processos em segundo plano com o PID;
	- '-n' lista os que mudaram de status desde a última notificação;
	- '-p' lista os IDs dos processos;
	- '-r' lista apenas processos em execução;
	- '-s' lista apenas processos interrompidos \(suspensos);
	- '%n' lista um processo especificado pelo número ID jobspec 'n';
	- '%str' processo que começa por 'str';
	- '%?str' peocesso que contém 'str;
	- '%+' ou '%%' job atual, iniciado por último;
	- '%-' processo anterior.

### fg %
- fg seguindo de '%' e o número do processo em segundo plano \(bg), traz o processo para o primeiro plano;
- ctrl+z e '**bg %ID**' retornam o processo para o segundo plano.

### nohup
- mantém um comando em segundo plano ativo mesmo quando uma sessão é encerrada e reaberta:
	- ``` $ nohup ping 8.8.8.8 & ```
- um arquivo 'nohup.out' é gerado no diretório da sessão; para o exemplo do ping, caso ele seja consultado com:
	- ``` $ tailf nohup.out ``` os resultados do ping continuam sendo escritos;
- o processo poderá ser encerrado com:

	```
$ pgrep ping
5542
$ kill -9 5542
	```

### free
- retorna o consumo de memória RAM e SWAP pelo sistema;
- **opções:**
	- '-m' retorna em megabytes.

### uptime
- retorna informações da sessão de execução do sistema:
	- horário em que o comando foi executado;
	- up;
	- tempo em que o sistema está ligado nessa sessão;
	- quantidade de usuários logados;
	- load average: média de processos utilizando recursos nos últimos 1min., 5min., 15min.;
os números do 'load average' sinalizam a utilização dos recursos de um servidor que, caso permaneçam por muito tempo perto do valor '1', podem representar uma sobrecarga do sistema.
	
### watch
- atualiza comandos periodicamente, como se criasse um daemon;

	- ``` # watch iptables -nvL ```

		- executa um reset do 'iptables -nvL', que exibe as regras de firewall, a cada dois segundos, que é o tempo padrão;

- encerra-se com ctrl+c;
- para configurar o intervalo de atualizações, usa-se:

	- ``` $ watch -n 10 command ```

		- em que 10 é o tempo em segundos que pode ser substituído pelo valor desejado;

- útil para monitorar a alteração de conteúdo de um arquivo em tempo real com o uso de ferramentas feito o comando 'cat'.

### at
- comando que agenda tarefas únicas, para o daemon 'atd', cujo status é verificado com 'systemctl status atd';
- o comando abre um prompt para inserção de comandos a executar que é encerrado por ctrl+D;
- tem como equivalente o comando 'batch', que trabalha em carga baixa de sistema;
- **sintaxe:**
 ```$ at HOUR:MIN DD.MM.YY```
	- em que a data e hora podem ser substituídas por palavras reservadas como:
		- teatime, now, noon, midnight, today, tomorrow, now +valor etc.;
- **opções para at:**
	- '-c' retorna o conteúdo de comandos de um trabalho pelo ID fornecido;
	- '-d' exclui trabalhos por ID, que pode ser consultado com 'atq'; 'at -d' é um alias para 'atrm';
	- '-f' lê o trabalho a partir de um arquivo em vez da entrada padrão;
	- '-l' lista tarefas pendentes; com root, lista inclusive tarefas de outros usuários; é um alias para 'atq';
	- '-m' envia email para o usuário, mesmo se não houver saída;
	- '-q' define uma fila alfabética; quanto maior a letra, maior o valor de nice;
	- '-v' retorna a hora em que o trabalho será executado;
	- '-r' remove um trabalho cujo ID seja informado;
- os agendamentos ficam armazenados no diretório '/var/spool/at' ou '/var/spool/cron/atjobs/', em arquivos com permissão 700 \(somente proprietário e root podem ver, editar e executar);
- o controle de uso do 'at' é feito pelos arquivos '/etc/at.allow' e '/etc/at.deny'.

### atq
- lista as tarefas agendadas com seus IDs.

### atrm
- exclui uma tarefa agendada pelo seu ID respectivo fornecido na sequência, separando por espaço se for mais de um;
- o root pode excluir a tarefa de qualquer usuário.

### screen
- um multiplexer mais simples que o tmux, comentado a seguir;
	- '$ screen'; espaço ou enter iniciam uma nova sessão;
	- default prefix: ctrl+a
	- detach \(suspender sessão): ctrl+a +d
	- exibir sessões ativas: '$ screen -ls' 
	- retornar a uma sessão que seja a única: '$ screen -r'
	- retornar a uma sessão entre várias: '$ screen -s sessionname' ou '$ screen -s PID'
	- abrir outra janela: ctrl+a +c
	- alternar para a próxima janela: ctrl+a +n
	- alternar para a janelas anterior: ctrl+a +p
	- encerrar janela: ctrl+a +k ou 'exit'
	- encerrar sessão: ctrl+a +\

### tmux
- um multiplexer com mais recursos do que o 'screen';
	- default prefix: ctrl+b
	- abrir outra janela: ctrl+b +c
	- renomear janelas: ctrl+b +,
	- alternar para a próxima janela: ctrl+b +n
	- alternar para a janela anterior: ctrl+b +p
	- alternar para janela específica pelo número da janela: ctrl+b +2
	- alternar de janela com setas: ctrl+b +w
	- fechar janela: ctrl+b +&
	- detach session: ctrl+b +d
	- para exibir sessões ativas: '$ tmux -ls' 
	- renomear sessão: '$ tmux rename-session -t sessionnumber newsessionname'
	- para retornar a uma sessão ativa: '$ temux attach -t sessionname'
	- split pane vertically / horizontally: ctrl+b +% / : ctrl+b +" 
	- mover entre painéis: ctrl+b +arrows
	- fechar painéis: ctrl+b +x
	- encerrar sessão única: '$ tmux kill-session'
	- encerrar uma sessão entre várias: '$ tmux kill-session -t sessionname'


### update-alternatives
- o comando permite alterar links simbólicos do sistema contidos no diretório 
/etc/alternatives/
- o uso mais comum desse comando é com a sintaxe:

	- ``` $ update-alternatives --config vim```

		- permitindo selecionar o comportamento do comando 'vim'.

------------------------------------------------------------

## LOCAL AND TIME

### date
- comando que exibe a hora e a data do sistema, além do fuso horário atual;
- **opções:**
	- '-u' exibe o horário UTC;
	- '-s' altera a data e a hora, como exemplificado abaixo;
	- '-I' formato ISO 8601; pode-se anexar '-Idate', '-Ihours', '-Iminutes', '-Iseconds' ou '-Ins' para refinar o resultado;
	- '-R' formato RFC 5322;
	- '--rfc-3339' formato RFC 3339;
	- '+%s' tempo do Unix, em segundos desde 01/01/1970;
	- '--date='@1564013011'' aplica data com o tempo do Unix;
	- '--debug' seguido de uma data válida, permite solucionar problemas em aplicativos que geram datas;
- definir hora e data com date: 

	- ```# date --set="11 Nov 2011 11:11:11"``` ou 

	- ```# date +%Y%m%d -s "20111125"```, para data, e 

	- ```# date +%T -s "13:11:00"```, para hora.

### hwclock
- exibe a hora do relógio do hardware;
- a opção '--verbose' mostra em detalhes;
	- o campo ```Calculated Hardware Clock drift``` informa o sincronismo entre hora de sistema e hora do hardware;
- ```# hwclock --set --date "4/12/2019 11:15:19"``` ajusta o relógio do hardware;
- ```# hwclock --hctosys``` ou '-s' ajusta o relógio do sistema a partir do relógio do hardware;
- ```# hwclock --systohc```,  ou '-w', para sincronizar o relógio do hardware a partir do relógio do sistema.

### timedatectl
- comando systemd que exibe mais detalhes a respeito de hora, data e fuso horário;
- o campo 'RTC time' exibe a hora do relógio do hardware;
	- 'timedatectl set-time 'AAAA-MM-DD HH:MM:SS'' ajusta a hora, como comando preferencial com systemd;
	- 'timedatectl set-ntp no' desativa o NTP: **Network Time Protocol**, hora da rede;
 	- 'timedatectl list-timezones' lista timezones disponíveis;
	- 'timedatectl set-timezone TIME/ZONE' redefine o link simbólico '/etc/localtime', que aponta para dados em '/usr/share/zoneinfo/;
	- '**/usr/share/zoneinfo/**':
		- diretório que contém informações sobre diferentes fusos horários possíveis;
		- a estrutura de subdiretórios e arquivos em '**/usr/share/zoneinfo/**', segue:
			- **/usr/share/zoneinfo/REGION/LOCALE**
		- para definir um fuso horário, cria-se um link simbólico em '/etc/localtime', como no exemplo:
		 ```$ ln -s /usr/share/zoneinfo/Canada/Eastern /etc/localtime```
		 ```# hwclock --systohc```, para sincronizar o relógio do hardware a partir do relógio do sistema;
		- o symlink '/etc/timezone' se define da mesma maneira que '/etc/localtime'.

### ntpq
- utilitário para monitorar o status NTP do daemon ntpd;
- 'ntpq -p' exibe um resumo do status, com os seguintes campos:
	- remote: host do provedor NTP;
	- refid: ID de referência do provedor;
	- st: estrato do provedor;
	- when: número em segundos desde a última consulta;
	- poll: número em segundos entre as consultas;
	- reach: ID de status das conexões, sendo acrescido 1 a cada conexão bem sucedida;
	- delay: tempo em ms entre a consulta e a resposta do provedor;
	- offset: tempo em ms entre a hora do sistema e a hora NTP;
	- jitter: deslocamento em ms entre a hora do sistema e o NTP na última consulta;
- sem opções e argumentos, o ntpq entra em modo interativo; '?' é uma opção de ajuda para ver os comandos do ntpq.

### ntpdate
- cliente NTP que atualiza a data e hora do sistema.

### tzselect
- 'time zone select' é o programa interativo que permite configurar o fuso horário do sistema;
- **$TZ** é a variável de ambiente que contém o nome da região correspondente ao fuso configurado.

### localectl
- comando systemd que permite consultar ou definir a localidade do sistema:
 ```# localectl set-locale LANG=en_US.UTF-8 ```.

### locale
- comando que exibe todas as variáveis para definições de localidade:
	- LC_COLLATE: define ordem alfabética;
	- LC_CTYPE: caracteres maiúsculos e minúsculos;
	- LC_MESSAGES: idioma para exibir mensagens;
	- LC_MONETARY: unidade monetária;
	- LC_NUMERIC: separadores para formato numérico, feito milhar e decimal;
	- LC_TIME: formato de data e hora;
	- LC_PAPER: tamanho padrão de papel;
	- LC_ALL: sobrepõe todas as variáveis, incluindo LANG;
- 'locale -a' exibe todas as configurações possíveis;
- a atribuição 'LANG=C' \(Common), em script, força resultados iguais aos do padrão do sistema em que ele foi escrito.

------------------------------------------------------------

## PACKAGE MANAGEMENT

### dpkg *options package*
- gerenciador de pacotes básico do Debian;
- **opções:**
	- '-i' instala o pacote cujo nome é fornecido a seguir;
	- '-r' remove o pacote fornecido;
	- '-P' *purge* remove o pacote fornecido e os arquivos de configuração correspondentes;
	- '--force' força uma remoção ou instalação, mesmo em caso de quebra de dependências, o que significa risco de quebra do próprio sistema;
	- '-I' retorna informações detalhadas sobre um pacote;
	- '--get-selections' lista todos os pacotes instalados o sistema;
	- '-L' lista todos os arquivos instalados por um pacote fornecido.

### dpkg-query -S /exact/path/to/file
- retorna a que pacote pertence o arquivo fornecido através de seu caminho.

### dpkg-reconfigure package
- refaz as configurações de um pacote fornecido, voltando às configurações da primeira instalação.

### apt-get
- 'advanced package tool' é o gerenciador de pacotes que inclui ferramentas de resolução de dependências;
- **parâmetros e opções:**
	- 'update' atualiza o índice de pacotes;
	- 'install' instala um pacote fornecido na sequência; opções para install:
		- '-f' procura consertar os pacotes quebrados, instalando dependências ausentes;
		- '-s' simula uma instalação;
		- '-d' apenas baixa o pacote e suas dependências, sem instalar coisa alguma;
		- '-y' responde 'yes' automaticamente aos avisos;
		- '--reinstall' reinstala pacotes já instalados em novas versões;
		- '-b, --compile, --build' compila pacotes de código fonte após baixar;
	- 'remove' remove um pacote fornecido;
	- 'purge' ou 'remove --purge' removem um pacote fornecido e todos os arquivos de configuração correspondentes;
	- 'upgrade' atualiza as versões dos pacotes;
	- 'dist-upgrade' atualiza o sistema;
	- 'source' baixa o pacote de código fonte correspondente a um pacote fornecido na sequência;
	- 'clean' limpa o cache de pacotes baixados.
	
### apt-cache
- ferramenta para executar operações com o índice de pacotes;
- **parâmetros:**
	- 'depends' retorna a lista de dependências de um pacote fornecido na sequência;
	- 'rdepends' retorna uma lista de dependência reversa, contendo os pacotes que dependem do pacote fornecido; 
	- 'search' retorna uma lista com todos os pacotes que contêm um padrão fornecido na sequência;
	- 'show' retorna detalhes de um pacote fornecido na sequência;
	- 'showsrc' retorna os registros de pacotes fonte de um pacote fornecido.
### RPM Package Manager
- ferramenta essencial de sistemas RedHat e derivados; equivale ao dpkg do Debian;
- **opções:**
	- '-i' instala o pacote fornecido a seguir;
	- '-v' verbose - detalha o processo;
	- '-h' exibe uma barra de cerquilhas, representando o progresso do processo; 
	- '-ivh' são frequentemente utilizados em conjunto;
	- '-U' se existir uma versão anterior no sistema, atualiza para a mais recente;
	- '-F' se caso usando '-U', só exista a versão recente, em vez de uma antiga, evita que uma nova cópia do mesmo pacote seja instalada;
	- '-e' erase - desinstala um pacote fornecido na sequência;
- **opções modo query:**
	- '-qa' query all - lista todos os pacotes instalados no sistema;
	- '-qi' query info - lista informações sobre um pacote *instalado*;
	- '-ql' query list - lista os arquivos que estão dentro de um pacote *instalado*;
	- '-qip' lista informações sobre um pacote que ainda *não* foi instalado;
	- '-qlp' lista os arquivos que estão dentro de um pacote que ainda *não* foi instalado;
	- '-qf /path/to/file' query file - retorna o pacote instalado que possui um arquivo fornecido;

### YellowDog Updater Modified *YUM*
- ferramenta capaz de resolver dependências e com outros recursos; equivale ao 'apt-get' do Debian;
- **parâmetros e opções:**
	- 'search' retorna os pacotes que possuem nome ou descrição contendo algum padrão fornecido na sequência;
	- 'install' instala um ou mais pacotes fornecidos na sequência;
	- 'update' atualiza o pacote fornecido ou todos os pacotes com atualização disponível, caso nenhum pacote seja fornecido;
	- 'check-update' verifica se há atualizações para um pacote fornecido ou para todo o sistema, como acima;
	- 'remove' ou 'erase' remove um pacote instalado fornecido;
	- 'whatprovides' retorna o nome do pacote que provê determinado arquivo fornecido a seguir;
	- 'info' retorna informações sobre um pacote;
	- 'deplist' lista as dependências de um pacote;
	- 'repolist' lista repositórios configurados ativos;
	- 'localinstall' realiza instalação local de pacotes resolvendo suas dependências;
	- 'groupinstall' e 'groupremove' instala e remove grupos de pacotes, respectivamente.
	
### YUM repositories
- os repositórios usados pelo yum ficam listados no diretório '/etc/yum.repos.d/';
- cada repositório é representado por um arquivo '\*.repo', como 'CentOS-Base.repo';
	- o conteúdo dos arquivos '\*.repo' segue o padrão:
	```
[nome_do_repositório]
name= Nome descritivo do repositório
baseurl=url://endereço/para/o/repositório
	```
- pode-se adicionar repositórios criando novos arquivos '\*.repo' 
- o arquivo '/etc/yum.conf' contém diversas configurações e também pode conter repositórios; 
- opções do arquivo:
	- 'cachedir' guarda o caminho para o armazenamento de cache, que pode ser alterado, mas o padrão é '/var/cache/yum';
		- para limpar o cache, usa-se:
			- ```# yum clean packages``` em que 'packages' remove todos os pacotes, mas pode ser substituído pelo nome de um pacote específico ou por 'metadata', conforme convir.
	- 'keepcache' com valor 0 exclui os arquivos de cache; com valor 1, os mantém;
	- 'repodir' lista os dieretórios em que se encontram arquivos '\*.repo';
	- 'gpgcheck' determina se deve se fazer verificação de assinatura GPG dos pacotes;
- pode-se adicionar repositórios usando a ferramenta 'yum-config-manager', usando a sintaxe:
	- ```# yum-config-manager --add-repo https://rpms.remirepo.net/enterprise/remi.repo```
- pode-se obter a lista de todos os repositórios com o comando:
	- ```# yum repolist all```
- habilita-se um repositório com:
	- ```# yum-config-manager --enable updates```

### DNF
- o dnf é um fork do yum, usado no Fedora, e equivale ao apt do Debian;
- muitas opções e parâmetros são os mesmos do 'yum': search, install, remove, info;
- **parâmetros e opções:**
	- 'upgrade' equivale ao 'update' do yum e ao 'upgrade' do apt;
	- 'provides' equivale ao 'whatprovides' do yum;
	- 'list --installed' equivale ao '-qa' do rpm;
	- 'repoquery' lista o conteúdo de um pacote;
	- 'repolist' lista todos os repositórios configurados;

- para adicionar um repositório:
	- ```# dnf config-manager --add_repo URL``` em que URL é a URL completa do repositório;

### Zypper
- o zypper é a ferramenta de gerenciamento de pacotes OpenSUSE;
- **operadores, parâmetros e opções:**
	- 'refresh' atualiza metadados de pacotes; equivale ao 'update' do apt;
	- 'search' ou 'se' procura um pacote fornecido a seguir; 
		- com '-i', retorna se o pacote está instalado; sem fornecer o pacote, retorna todos os instalados no sistema;
		- com '--provides' retorna o pacote que contém um arquivo cujo nome ou caminho é fornecido;
	- 'install' ou 'in' instala um pacote; para instalar pacote baixado, fornecer o caminho na sequência;
	- 'update' atualiza os pacotes do sistema;
	- 'list-updates' retorna uma lista de atualizações disponíveis;
	- 'remove' ou 'rm' remove um pacote fornecido, incluindo pacotes que dependerem dele;
	- 'info' retorna dados a respeito de um pacote fornecido;
	- 'repos' exibe os repositórios configurados;
	- 'modifyrepo' permite administrar repositórios, com as opções:
		- '-e' habilita um repositório cujo alias listado com o operador 'repos' for fornecido;
		- '-d' desabilita um repositório conforme acima;
		- '-f' habilita o autorefresh, tornando a ação do operador 'refresh' automática;
		- '-F' desabilita o autorefresh;
	- 'addrepo' seguido da URL do repositório adiciona um repositório;
	- 'removerepo' seguido do alias do repositório o remove.

------------------------------------------------------------

# SECURITY

## PERMISSIONS

	
### chmod
- comando que permite alterar as permissões de arquivos;
- sintaxe: 
	- ```$ chmod [ugoa][+-=][rwx],[ugoa][+-=][rwx],[ugoa][+-=][rwx] file```, em que 'a' representa todos, ou 
	- ```$ chmod 000 file```, em que 0 representa o resultado de uma operação com octais desejada;
- o comando ainda permite usar a opção '-R' para operação recursiva em diretórios, estendendo as permissões para arquivos e subdiretórios contidos.

### chown
- comando que permite alterar o proprietário de arquivos;
- sintaxe: ```# chown USERNAME:GROUPNAME FILENAME```;
	- ```# chown: GROUPNAME FILENAME```para mudar apenas o grupo e
	- ```# chown USERNAME FILENAME``` para mudar apenas o proprietário.

### umask
- comando que exibe em octais as permissões padrão para a criação de novos arquivos;
- para visualizar no modo simbólico, usa-se a opção '-S';
- o umask permite alterar esse padrão, bastando fornecer a nova configuração como com o exemplo a seguir:
	- ```$ umask u=rwx,g=rwx,o=```;
- nessa configuração o comando retorna o padrão em octais da seguinte forma:
	- ``` 007 ```.

### chroot
- permite usar um diretório como novo diretório root isolado do root do sistema;
- ferramenta equivalente aos recursos de conteinerização;
- **sintaxe:** ```# chroot OPTIONS DIRECTORY COMMAND ```;
	- COMMAND frequentemente é um shell, cujo binário passa a ser usado a partir desse diretório.

### unshare
- permite instanciar namespaces \(espaços lógicos) isoladas do sistema operacional, como ferramenta suplementar para isolamento de processos;
- **sintaxe** ```# unshare OPTIONS DIRECTORY COMMAND ```.

------------------------------------------------------------

## USER MANAGEMENT

### useradd
- cria um novo usuário cujo nome for fornecido no final do comando;
- **opções:**
	- '-c' cria uma nova conta com comentários personalizados;
	- '-d' com diretório pessoal personalizado;
	- '-e' permite definir uma data de expiração da nova conta, quando ela será desabilitada;
	- '-f' define o número de dias até a expiração de uma senha, que deverá ser atualizada ou a conta será desabilitada;
	- '-g' permite especificar GID do grupo primário;
	- '-G' adiciona a grupos secundários separados por vírgulas;
	- '-k' permite especificar um diretório 'skel' personalizado, usada apenas combinada à '-m';
	- '-m' cria um diretório pessoal a partir do 'skel' padrão;
	- '-M' sem diretório inicial;
	- '-s' com um shell de login específico;
	- '-u' permite especificar UID.

### su
- 'switch user' é o comando que permite a troca de usuário;
- com a sintaxe ```su - ``` garante o carregamento do ambiente do usuário destino: ler arquivo '.profile' e ir para o respectivo diretório home;
- sem fornecer o nome de usuário, o padrão é mudar para 'root';
- com a opção '-c', permite executar um comando com o privilégio de outro usuário fornecido.
- com o comando **su** se pode chamar shell de login ou sem login;
	- ```# su - user2```, ```# su -l user2``` ou ```# su --login user2``` iniciam shell de login interativo como 'user2';
	- ```# su user2``` inicia um shell sem login interativo como 'user2';
	- ```# su - root``` ou ```# su -``` iniciam um shell de login interativo como root;
	- ```# su root``` ou ```# su``` iniciam um shell interativo sem login como root.

### sudo 
- permite que usuários constantes no arquivo **'/etc/sudoers':** possam executar comandos como superusuário temporariamente;
- para incluir usuário entre os 'sudoers':

	- ```# usermod -aG sudo USERNAME```
	- ```# useradd -aG sudo USERNAME ```
- **sintaxe do arquivo '/etc/sudoers':**
		- ``` usuário host=(usuário:grupo) comando ```;
		- exemplo: ``` root	ALL=(ALL:ALL) ALL ```;
		- leia-se: o usuário root pode se logar com todos os hosts, em nome de todos os usuários e todos os grupos, além de executar todos os comandos;
		- palavras úteis:
	- o arquivo '/etc/sudoers' costuma ser editado pelo comando ```# visudo ```
	- linhas possíveis:
		- ``` Defaults 	timestamp_timeout=N ``` define o tempo limite de uso do 'sudo' para 'N' minutos; o padrão assumido sem essa linha é 15 min.;
		- ``` Defaults 	editor=/usr/bin/nano ``` define o 'nano' como editor padrão para visudo;
		- 'User_Alias', 'Host_Alias' e 	'Cmnd_Alias' podem ser definidos no arquivo '/etc/sudoers' com listas de nomes, IPs e caminhos absolutos separados por vírgulas.
- pode-se iniciar shells de login interativo e sem login interativo usando 'sudo' seguindo adiante conforme a sintaxe acima; porém para os outros casos:
	- ```$ sudo su -u user2 -s``` para iniciar shell sem login interativo;
	- ```$ sudo -i``` para shell de login interativo como root;
	- ```$ sudo -i <command>``` para um shell de login interativo como root retornando ao usuário original após a execução do comando.
	- ```$ sudo su root``` ou ```$ sudo su``` iniciam um shell sem login interativo como root;
	- ```$ sudo -s``` ou ```$ sudo -u root -s``` iniciam um shell sem login como root.
- os usuários que podem  '**sudo**', cuja sintaxe padrão é: 
 ```$ sudo -u USERNAME COMMAND ```;

### id
- 'id USERNAME' permite consultar UID, GID e o grupo do novo usuário;
- como root, retorna dados do root; para dados de um usuário, fornecer o nome.

### groups
- 'groups USERNAME' permite consultar o grupo do novo usuário.

### passwd
- permite configurar senha do usuário fornecido no fim do comando;
- no caso de um novo usuário, recomenda-se a sintexe: ```# passwd -e USERNAME```;
- a opção '-e' expira a nova senha, forçando o novo usuário criar uma nova no próximo login.
**opções gerais:**
	- '-d' apaga a senha de um usuário, desabilitando a conta;
	- '-e' força a alteração da senha;
	- '-i' define dias de inatividade após a expiração de uma senha, para que ela seja atualizada antes de uma desativação; o valor -1 remove a inatividade;
	- '-l' bloqueia a conta; uma exclamação é inserida antes da senha criptografada no arquivo '/etc/shadow', desabilitando o acesso do usuário;
	- '-n' define um tempo de vida mínimo para a senha; MIN_DAYS;
	- '-S'  ou '--status', retorna campos com:
		- login do usuário;
		- 'P' para senha válida, 'L' para senha bloqueada ou 'NP' para nenhuma senha;
		- data da última alteração da senha;
		- idade mínima em dias para alteração da senha; 0 pode ser alterada a qualquer momento;
		- idade máxima em dias de validade da senha; 99999 desabilita expiração;
		- período de aviso em dias para expiração;
		- período de inatividade da senha após a expiração e antes do bloqueio; -1 remove a inatividade;
		- \(campos que coincidem com os 7 primeiros dos 9 do arquivo '/etc/shadow');
	- '-u' desbloqueia a conta; remove a exclamação em '/etc/shadow', reabilitando o usuário;
	- '-x' define tempo de vida máximo da senha; MAX_DAYS;
	- '-w' define número de dias de aviso antes que uma senha expire.

### chage
- 'change age' é um comando para alterar validade de senhas de um usuário, usado apenas pelo root;
- **opções:**
	- '-d N USERNAME' ou '--lastday N USERNAME' especificam 'N' dias até a senha expirar; 0 força alteração no próximo login;
	- '-E YYYY-MM-DD USERNAME' ou '--expiredate YYYY-MM-DD USERNAME' especificam data de bloqueio da conta.
	- '-I N USERNAME' ou '--inactive N USERNAME' para 'N' dias de inatividade, feito '-f' e '--inactive' de usermod; 0 para desabilitar o bloqueio; o valor -1 remove a inatividade;
	- '-l' lista informações sobre a expiração da senha, sendo a única forma do comando que pode ser usada por usuários comuns;
	- '-m N USERNAME' ou '--mindays N USERNAME' configuram 'N' dias mínimos para alteração da senha; 0 para qualquer momento;
	- '-M N USERNAME' ou '--maxdays N USERNAME' máximo de dias de validade da senha; 99999 para desabilitar expiração;
	- '-W N USERNAME' ou '--warndays N USERNAME' 'N' dias de aviso de senha expirada;
- sem as opções, abre-se um prompt para alteração de todas as opções.

### chfn
- altera o campo de comentário \(5º campo) do arquivo '/etc/passwd', com opções, string entre aspas e o nome do usuário a ter os dados alterados;
- **opções:**
	- '-f' '--full-name';
	- '-h' '--home-phone';
	- '-o' '--other-info';
	- '-w' '--work-phone';
- sem as opções, abre-se um prompt para alteração de todas as opções.

### usermod
- permite modificar atributos de um usuário fornecido no final do comando;
- **opções:**
	- '-c' adiciona comentários personalizados;
	- '-d' altera o diretório; combinada à '-m', move o que estiver no diretório pessoal atual para o novo diretório pessoal;
	- '-e' altera data de expiração;
	- '-f N' ou 'usermod --inactive N' configura 'N' dias de inatividade após expiração e antes de bloqueio.
	- '-g' altera GID de grupo primário, como useradd;
	- '-G' adiciona a grupos secundários separados por vírgulas, como useradd; sem grupos fornecidos, remove os existentes; combinada à '-a', adiciona os grupos secundários fornecidos que ainda não estiverem configurados;
	- '-l' altera o nome de login;
	- '-L' bloqueia a conta fornecida; uma exclamação é inserida antes da senha criptografada no arquivo '/etc/shadow', desabilitando o acesso do usuário;
	- '-s' altera o shell de login;
	- '-u' altera UID;
	- '-U' remove a exclamação em '/etc/shadow', desbloqueando o usuário.

### userdel
- comando para remover um usuário fornecido na sequência;
- a opção '-r' adiciona recursividade ao comando, removendo o diretório de usuário.

### groupadd
- comando para criar grupos;
- sintaxe de costume: ```# groupadd -g 1090 GROUPNAME```, em que a opção '-g' permite especificar o GID.

### gpasswd
- define senhas de grupo, quando desejado;
- usuários de outros grupos que tiverem a senha podem ingressar temporariamente com o comando '**newgrp**';
- **opções:**
	- '-a' adiciona um usuário fornecido a seguir a um grupo informado no final do comando;
	- '-d' remove usuário do grupo;
	- '-r' remove a senha do grupo;
	- '-R' restringe acesso dos membros ao grupo;
	- '-M' ajusta a lista de membros, com vírgula como separador;
	- '-A' ajusta a lista de administradores, com vírgula como separador.

### groupmod
- comando para modificar grupos;
- sintaxe de costume: ```# groupmod -n WEB-GROUPNAME -g 1050 GROUPNAME```.

### groupdel
- comando que remove um grupo fornecido a seguir;
- para remover um grupo, ele não pode ser grupo principal de usuário algum.

### newgrp
- permite ingressar temporariamente um grupo de que o usuário corrente não faz parte através da senha de grupo;
- quando o grupo não possui senha, apenas usuários que fazem parte dele podem usar o 'newgrp' para usar o grupo como primário temporariamente.

### pwconv
- comando que gera o arquivo '/etc/shadow' a partir de '/etc/passwd';
- 'pwunconv' retorna os dados de '/etc/shadow' para '/etc/passwd' e exclui o primeiro;
- equivalente para grupos: 'grpconv'.

### fuser
- exibe usuário de arquivo;
- verifica o diretório atual com ```# fuser . ```;
- com a opções '-v', lista colunas:
	- nome do arquivo;
	- USER: proprietário;
	- PID: ID do processo;
	- ACCESS: tipo de acesso:
		- 'c' diretório atual;
		- 'e' executável em execução;
		- 'f' arquivo aberto para leitura;
		- 'F' arquivo aberto para escrita;
		- 'r' diretório raiz;
		- 'm' arquivo mmap ou biblioteca compartilhada;
		- '.' espaço reservado;
	- COMMAND: comando afiliado ao arquivo;
- com as opções '-n' ou '--namespace' pode-se especificar protocolo e porta/socket de rede:
 ```# fuser -vn tcp 80 ``` retorna informações sobre o servidor Apache;
- com as opções '-k' ou '--kill' elimina os processos que estão acessando o arquivo.

### ulimit
- utilitário que retorna blocos de arquivos flexíveis do usuário corrente;
- **opções:**
	- '-S' especifica os flexíveis \(soft);
	- '-H' especifica os rígidos \(hard);
	- '-a' retorna todos os limites flexíveis atuais; o mesmo que '-Sa';
	- '-Ha' para todos os limites rígidos;
	- para recursos do Shell:
		- '-b' tamanho máximo do buffer socket;
		- '-f' tamanho máximo de arquivos escritos pelo shell e seus processos-filhos;
		- '-l' tamanho máximo da memória que pode ser bloqueada;
		- '-m' tamanho máximo do conjunto residente \(RSS, resident set size) para um processo na RAM;
		- '-v' quantidade de memória virtual;
		- '-u' número máximo de processos disponíveis para um usuário;
- **sintaxe:** '-f' seguido de um valor em kilobytes ou 'unlimited' define um limite de blocos para '-S' ou '-H' ou para ambos, se não especificar.
- **/etc/security/limits.conf**
	- arquivo que mantém as configurações de limite, o qual deve ser alterado para que as configurações de limite sejam permanentes; pode haver o diretório '/etc/security/limits.d/';
	- o arquivo contém orientações para o preenchimento das colunas; 
	- pode-se atribuir configuarção para usuário ou grupo, este último precedido por '@'.

### last
- comando que retorna uma lista detalhada dos últimos usuários logados e suas sessões;
- seguido de um nome de usuário, last retorna suas respectivas sessões;
- a coluna após o nome de usuário na lista indica o terminal: pts significa 'Pseudo Terminal Slave', oposto a tty, 'TeleTypeWriter';
- os dados são extraídos do arquivo '**/var/log/wtmp**';
- **lastb** exibe tentativas de login incorretas; dados de '**/var/log/btmp**';
- a opção '-f' para last e lastb permite selecionar outros arquivos wtmp e btmp gerados pelo logrotate.

### who
- exibe usuários atualmente logados, com dados extraídos do binário '/var/log/wtmp';
- **opções:**
	- '-b' ou '--boot' exibem a hora da última inicialização do sistema;
	- '-r' ou '--runlevel' exibe o nível de execução atual;
	- '-H' ou '--heading' exibe o cabeçalho das colunas;
	- '-a' para mais detalhes;
- a coluna após o nome de usuário na lista indica o terminal: pts significa 'Pseudo Terminal Slave', oposto a tty, 'TeleTypeWriter', ':0' para o modo gráfico.

### w
- exibe usuários logados, com dados extraídos do binário '/var/log/wtmp', detalhando:
	- hora atual e tempo de atividade do sistema;
	- os 3 números médios de carga \(load average);
	- oito colunas com usuários e suas ações:
		- USER: nome de usuário;
		- TTY: nome do terminal;
		- FROM: IP do host remoto;
		- LOGIN@: tempo de login;
		- IDLE: tempo ocioso;
		- JCPU: tempo usado por todos os processos ligados ao tty, incluindo trabalhos em segundo plano;
		- PCPU: tempo usado pelo processo atual;
		- WHAT: processo atual;
- pode-se passar nome de usuário para especificá-lo, como com who.

------------------------------------------------------------

## NETWORK

### nmcli
- utilitário de linha de comando, equivalente ao 'nmtui', que permite configurar o daemon do NetworkManager;
- **categorias ou objetos do nmcli:**
	- general: status e operações gerais do NetworkManager:
		- STATE: coluna do status da conexão;
		- CONNECTIVITY: 
			- full para ok, 
			- Portal para necessidade de autenticação;
		- WIFI e WWAN: redes sem fio; o sufixo HW diz respeito ao dispositivo;
	- networking: controle de rede;
	- radio: controle de rádio;
		- ```$ nmcli radio wifi off``` permite desligar um dispositivo wi-fi para economia de energia;
		- ```$ nmcli radio wifi on``` permite religar;
	- device: dispositivos gerenciados;
		- ```$ nmcli device wifi list```: lista as redes sem fio disponíveis, com o SSID da rede para conexão;
		- ```$ nmcli device wifi connect SSID_NAME```: conecta à rede abrindo uma caixa de diálogo no modo gráfico para a inserção da senha; em modo texto exclusivamente, a senha pode ser inserida na mesma linha do comando, com a sintaxe: ```$ nmcli device wifi connect SSID_NAME password PASSWORD```;
		- ifname pode ser adicionado ao final para a seguir fornecer o nome de um dispositivo escolhido, caso haja mais de um;
	- connection: conexões;
		- ```$ nmcli connection down SSID_NAME``` desativa uma conexão;
		- ```$ nmcli connection up SSID_NAME``` ativa uma conexão;
		- o nome de um dispositivo pode ser usado para restabelecer uma conexão;
	- agent: agente polkit;
	- monitor: monitor das mudanças no daemon.

### ifconfig
- comando legado, ainda fornecido pelo pacote '**net-tools**';
- sem opções, o comando exibe as interfaces de rede ativas:
	- RX linha que mostra a taxas de recebimento de pacotes,
	- TX taxas de transmissão de pacotes;
- com o nome de uma interface, um IPv4 e máscara CIDR e 'add', permite configurar um IP;
- **opções e subcomandos:**
	- '-a' exibe todas as interfaces, incluindo inativas;
	- 'add' precede a adição de um endereço IPv6;
	- 'netmask' precede a inserção de uma máscara de rede;
	- 'down' ou 'up' após o nome de uma interface desativa ou ativa, respectivamente;
	- 'mtu' permite ajustar o 'Maximum Transmission Unit' \(MTU) de uma interface fornecida.

### ip
- comando completo para gerenciamento de configurações de rede;
- **objetos, opções e subcomandos:**
	- 'address', 'addr', 'a' ou 'ip-address' equivalem a 'ifconfig -a';
	- 'link' lista links de interface;
	- 'add' adiciona IPv4 ou IPv6;
	- 'dev' especifica uma interface pelo nome fornecido a seguir;
	- 'link' configura interface de baixo nível, protocolos VLANs, ARP ou MTUs e permite desabilitar uma interface:
		- 'ip link set IFACE_NAME down' desativa uma interface; up para ativar;
		- 'ip link show' lista as interfaces com detalhes; pode se especificar para obter detalhes dela;
		- 'ip link set IFACE_NAME mtu 2000' permite ajustar o MTU de uma interface;
	- '**ip route**' equivale a '**netstat -r**' e '**route**', retornando uma tabela de roteamento; para IPv6: '**ip -6 route**', '**netstat -6r**' e '**route -6**', respectivamente; 'via' é a palavra que antecede a adição do IP de um roteador \(gateway) com 'ip route'.

### netstat
- exibe conexões ativas de rede e sockets Unix;
**opções:**
	- '-a' exibe os status de cada conexão;
	- '-e' exibe o usuário dos processos que estão requisitando as conexões;
	- '-i' exibe dados de interfaces de rede;
	- '-l' ou '--listening' filtram por portas/sockets ouvintes \(portas abertas); 
	- '-p' exibe o processo local que está requisitando as conexões;
	- '-t' ou '--tcp' filtram pelo protocolo TCP;
	- '-u' ou '--udb' filtram pelo protocolo UDP.
	- '-e' ou '--extend' exibem mais detalhes;
	- '-n' ou '--numeric' retornam números de portas e endereços, no lugar de nomes.

### route
- comando que retorna uma tabela de dados de rotas da rede local e permite editar rotas, feito 'ip route';
- **palavras-chave**:
	- 'add' antecede a adição de um IP;
	- 'gw' antecede a adição do IP de um roteador \(gateway).

### ping
- comando que permite testar uma conexão, com eco ICMP; 
- '**ping6**' é o equivalente para IPv6;
- sintaxe comum: ```$ ping -c 3 192.168.50.2```, em que '-c 3' limita o teste ao envio de 3 pacotes.

### traceroute
- utilitário que retorna a rota de um pacote até um destino fornecido a seguir pelo IP;
- '**traceroute6**' é o equivalente para IPv6;
- cada reteador no caminho responde com uma mensagem ICMP de Time-To-Live \(TTL) excedido;
- são enviados 3 pacotes UDP com dados inúteis para a porta 33434, que são incrementados a cada vez que são enviados;
- o comando retorna uma linha para cada roteador que os pacotes atravessam, com o IP de cada interface e o tempo de ida e volta dos pacotes;
- quando retorna '*' no lugar do tempo, significa que a mensagem TTL excedido para um pacote não foi recebida;
- a opção '-I', usada como root, substitui solicitações de eco UDP por ICMP, que são mais eficazes;
- a opção '-T -p 80', como root, solicita eco TCP, em que '-p' especifica a porta; esta opção é útil, considerando que respostas ICMP podem estar bloqueadas.

### tracepath
- semelhante ao 'traceroute', mas rastreia tamanhos de 'Maximum Transmission Unit' \(MTU) pelo caminho, enviando pacote com datagrama UDP extenso;
- o MTU é uma configuração de interface ou limite de hardware para a maior unidade de dado de protocolo que é possível transmitir ou receber;
- '**tracepath6**' é o equivalente para IPv6.

### nc
- '**netcat**' utilitário simples para o Sendmail, que é intalado pelo pacote ncat ou nmap-ncat, e permite testar conexões; 
- **opções:**
	- '-e' instrui a encaminhar tudo o que recebe para a entrada padrão de um executável fornecido a seguir;
	- '-l' recebe dados, em vez de enviar;
	- '-u' UDP;
	- '-v' verbose é útil para testar conexões, quando não há o Ping instalado, ao passar o nome do host destinatário e a porta.

### ss
- 'socket service', assim como o legado '**netstat**', retorna o status de *listeners* e conexões atuais;
- **opções:**
	- '-a' exibe todos os sockets;
	- '-l' sockets de escuta;
	- '-p' processos associados à conexão;
	- '-n' bloqueia pesquisas de nome para portas e endereços;
	- '-t' mostra conexões TCP;
	- '-u' mostra conexões UDP;
- 'netstat' e 'ss', com as devidas opções \(normalmente -tulnp), retornam as colunas:
	- Recv-Q: número de pacotes que um socket recebeu, mas não passou para seu programa;
	- Send-Q: número de pacotes que um socket enviou e não foram confirmados pelo receptor.

### nmap
- mapeador de rede que escaneia portas especificando IP ou nome de host;
- pode-se especificar mais de um, com espaços, ou intervalos, com '-', ou subredes, com '*' ou CIDR;
- '-p' permite especificar uma porta para escanear, fornecendo número ou nome;
- '-F' executa escaneamento rápido das 100 portas mais comuns;
- '-v' para saída detalhada; '-vv' para ainda mais detalhes.

### ssh-keygen
- permite gerar chaves 'secure shell' através de um prompt próprio, que solicita a confirmação do local onde o arquivo será armazenado e uma PASSPHRASE;
- **opções:**
	- '-b' permite definir o número de bits do algoritmo, conforme possível;
	- '-t' especifica um algoritmo fornecido a seguir;
	- '-l -f' lista as impressões digitais das chaves, passando o caminho do arquivo da chave após '-f';
	- '-v' exibe a arte aleatória \(randomart);
	- '-R' exclui as chaves pertencentes a um host fornecido a seguir;
- **ssh-copy-id** para enviar a chave pública para o arquivo '~/.ssh/authorized_keys' de um host remoto: ```$ ssh-copy-id -i ~/.ssh/PUBLIC_KEY_FILE.pub USERNAME@IP_HOST ```.

### ssh-agent
- utilitário executado em segundo plano que armazena a PASSPHRASE, a fim de agilizar conexões.

### ssh-add
- utilitário que adiciona a PASSPHRASE ao 'ssh-agent' em execução na memória.

### ssh
- o cliente SSH é instalado pelo pacote 'openssh-client';
- o servidor SSH é instalado pelo pacote 'openssh-server';
- sintaxe comum para estabelecer conexão: ```$ ssh USERNAME@HOST_IP ```;
- quando o USERNAME é omitido, a conexão é feita com o nome de usuário local;
- **opções:**
	- '-f' segundo plano, usado com '-N';
	- '-l' permite inserir o nome de usuário para login;
	- '-L' inserir 'LOCAL_PORT:REMOTE_HOST:HOST_PORT' para tunelamento;
	- '-N' dispensa login para um usuário fornecido a seguir;
	- '-p' inserir a porta;
	- '-R' tunelamento para porta remota;
	- '-X' tunelamento para interface X11.

### curl
- utilitário que permite transferir dados de ou para servidores via protocolos de rede como HTTP, HTTPS, FTP;
- amplamente utilizado para baixar arquivos, fazer requisições web e enviar dados para APIs;
- **opções:**
	- '-o FILE' salva a saída em um arquivo, ao invés de exibir na tela;
	- '-L' segue redirecionamentos HTTP;
	- '-s' silencia a saída, mostrando apenas erros;
	- '-X METHOD' especifica o método HTTP \(GET, POST, etc.);
	- '-d DATA'	envia dados no corpo da requisição \(ex: para POST);
	- '--data' precede dados entre aspas.

### getent
- o utilitário retorna entradas de bancos de dados de serviços de nome a partir de qualquer fonte configurável pelo '/etc/nsswitch.conf', como com a sintaxe ```$ getent hosts```.

### host
- utilitário que permite procurar entradas DNS para um nome ou IP fornecido;
- retorna os conjuntos de registros A, AAAA e MX;
- a opção '-t' permite especificar um registro feito 'NS' nameserver, 'MX' mailserver ou 'SOA'.

### dig
- comando mais detalhado que 'host';
- consulta registros A;
- podem ser usadas opções como '+short' ou '+nocookie', além da '-t', feito 'host'.