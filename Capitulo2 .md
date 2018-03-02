# A estrutura das pastas e dos arquivos

Para começar, quero enfatizar que as coisas no Linux não funcionam da mesma forma que no Windows. No entanto, saber como navegar de pasta em pasta e saber como listar os arquivos é muito improtante! Por causa disso, nós vamos estudar juntos o funcionamento dos arquivos a partir de agora.


## Organização das pastas
--------

Entender o sistema que gerencia os arquivos no Linux é um pouco complicado no começo sobretudo quando estamos acostumado com o Windows. Com efeito, aqui você não vai encontrar `C:\`, `D:\` ou algo parecido. Os arquivos são organizados de uma maneira completamente diferente.

Em vez de separar cada dísco rígido, leitor de CD, leitor de disquete, leitor de memória...
O Linux "coloca" meio que tudo no mesmo lugar.

> Mas como fazer para saber se a pasta na qual estamos está no primeiro dísco rígido, no segundo, no leitor de CD ? Bom, isto parece uma bagunça porém, não é.

#### Dois tipos de arquivos

Para simplificar, existe dois grandes tipos de arquivos no Linux:

* **os arquivos clássicos** : são os arquivos que você conhece, são envolvidos os arquivos de texto (`.txt`, `.doc`, `.odt`...), de som (`.wav`,`.mp3`, `.ogg`), mas também os arquivos de programa. Em sumo, tudo isso são arquivos que você já conhece e encontra no Windows;

* **os arquivos especias** : alguns arquivos são especias pois **representam** alguma coisa. Por exemplo, o seu leitor de CD é um arquivo para o Linux. Ali onde o Windows faz a diferença entre o que é arquivo e o que não é, Linux, ele, diz que **tudo é arquivo**. É um concepção muito diferente, um pouco bizara, mas não se preocupe, você vai se acostumar com isso.

#### A Raíz

Num sistema de arquivos, sempre há o que chamamos de raiz, ou seja, "**uma grande pasta base que contêm todos as outras pastas e arquivos**".

No Windows, há várias raízes. `C:\`´é a raiz do disco rígido, `D:\`é a raiz de seu leitor de CD (por exemplo).

No Linux, **há uma e somente uma única raíz** : "`/`". Como você pode ver, não há uma letra para o leitor pois justamente, o Linux não dá nome aos leitores como o Windows faz. Ele 'simplesmente fala: "**A base, é /**".

#### A arquitetura das pastas

No Windows, uma pasta pode ser representada da maneira seguinte:
`C:\Program Files\Winzip`. Podemos dizer que `Winzip`é uma subpasta da pasta  `Program Files`, que ela mesma está na raíz.

Você vai notar que é a barra invertida `\` (também chamado de *backslash*) que serve de separador aos nomes das pastas.

No Linux, é ao contrário o `/`que serve de separador. Como já dizemos, não há um `C:`no Linux, a raíz (o começo) se chama apenas `/`.

A pasta do nosso superprograma se pareceria à alguma coisa como: `/usr/bin/`. Dizemos que `bin`é uma subpasta da pasta `usr`,que ela mesma está na raíz.

> O Linux gerencia sem problemas os nomes dos arquivos contendo espaços, acentos e letras maiúsulas. No entanto, você enontrará mais nomes em minúsculo sem acentos nem espaços, como `usr`, `bin`,`apache`, etc. Lembre que você não está obrigado a seguir a mema regra mas, a maioria dos programas que você instalar preferem usar nomes em minúsculo sem espaços nem acentos.

#### As pastas da raiz

No Windows, nós geralmente achamos as mesmas pastas na raiz:
`Documents and Settings, Program Files, Windows`...
No Linux, as pastas são completamente diferentes. Nós vamos aqui dar uma breve e rápida lista das pastas mais comuns que sempre se encontram na raíz do Linux. Não é necessário decorar essa lista. Use-a caso você queira saber o que é cada coisa.

* **bin** : contém os arquivos de programas (os executáveis) que vão ser usados por todos os usuários da máquina.
* **boot** : arquivos que permitem o Linux inicializar.
* **dev** : arquivos que contêm os periféricos. Suas subpastas representam cada uma um periférico. Assim, você por exemplo vai encontrar dentro dela o arquivo que representa o leitor de CD.
* **etc** : arquivos de configuração.
* **home** : repertórios pessoais. É aqui que você vai encontrar seus arquivos pessoais, um pouco como o meus documentos do Windows.

Cada usuário do computador possui uma pasta pessoal. Por exemplo, no meu caso a minha pasta pessoal se encontra no `/home/josuegrace/.`Se tivesse um outro usúario (chamamos ele de matheus) no meu computador, ele teria também uma pasta própria a ele: `/home/matheus/.`
* **lib** : pastas que contêm as bibliotecas compartilhadas (geralmente os arquivos `.so`) usados pelos programas. Esses arquivos são meio que o equivalente dos arquivos `.dll` do Windows.
* **media** : quando um dispositivo removível (como uma carta de memória SD ou uma chave USB) foi inserida no computador, o Linux permite accessá-lo a través da subpasta `media`. Isto se chama montagem.
* **mnt** : é parecido com o `media`, porém por um uso temporário.
* **opt** : repertório usado para os *add-ons* dos programas.
* **proc** : contêm as informações do sistema.
* **root** : é a pasta pessoal do usúario "root", o super-usúario da máquina.
* **sbin** : contêm os progamas importantes do sistema.
* **tmp** : pasta temporária usado pelos programas para armazenar arquivos.
* **usr** : é uma das maiores pastas, dentro da qual será instalada a maioria dos programas do usúario.
* **var** : essa pasta contêm os "*logs*" do funcionamento da máquina.

#### Diagrama da arquitetura

(incluir imagem aqui).

A raiz em cima é o `/`. Ela possui várias pastas que contêm várias pastas que por suas vezes contêm outras pastas e arquivos, etc.

## pwd & which : onde estou ?
------
O número de pastas e de arquivos criados depois da instalaçaõ do sistema é tão grande que seria fácil de se perder. Com efeito, um número muito grande de programas foram pre-instaldos para você poder usufruir das possibilidades do Linux.

Nós vamos agora ver como se repertoriar na arborescência das pastas. Você saberá então em qualquer momento onde você está no seu disco rígido.

**`pwd`: mostrar a pasta atual**

Quando você abre o terminal pela primeira vez, Linux posiciona você na sua pasta pessoal, seu `home`. No meu caso por exemplo, a pasta dentro da qual serei colocado será: `/home/josuegrace`.

Normalmente, o prompt de comando indica o nome da pasta onde estamos:

	joesuegrace@josuegracestudy:~$

Se você está se lembrando bem, o nome da pasta está entre o ":" e o "$". Então aqui estamos dentro da pasta "`~`", que significa a nossa pasta pessoal.

Essa indicação do prompt de comando é muito prático porém, é bom saber que existe um outro meio de saber o nome da pasta atual. É o comando **`pwd`**. `pwd`é a abreviação de "Print Working Directory", ou seja, "mostre a pasta atual".

É um comando muito simples que não pega nenhum parâmetro. Você pode testar.
> joesuegrace@josuegracestudy:~$ pwd

	/home/josuegrace

**`which`: saber a localizaçao de um certo comando**

O que faz este comando ? Ele permite localizar a posição de um programa correspondente a um comando.

*Um comando não é nada mais que um outro programa que podemos chamar a qualquer momento e em qualquer lugar dentro do console.*

O comando `which`pega um parâmetro: o nome do comando que você quer saber a localização.

Vamos testar:
> joesuegrace@josuegracestudy:~$ which pwd

	/bin/pwd

`pwd`se encontra então na pasta `/bin/`! O "pwd" no final não é o nome de uma pasta porém, o do programa em si.

> Você vai notar que os programas no Linux em geral não têm extensão (no Windows a extensão mais usada em geral é o `.exe`).

Todos os programas não estão colocados numa mesma pasta. Teste por exemplo o comando `which`!
Nós vamos então digitar `which which` no terminal.
> josuegrace@josuegracestudy:~$ which which

	/usr/bin/which

Desta vez o programa não se encontra na pasta `/bin` porém na pasta `/usr/bin`!

## `ls`: listar os arquivos e as pastas
-----
`ls` é um dos comandos que nós usamos no capítulo precedente. Aqui nós vamos entrar mais em detalhes no seu funcionamento (e de seus vários parâmetros...)

Comecemos por digitar "ls" sem parâmetro dentro da nossa pasta pessoal.
> josuegrace@josuegracestudy:~$ ls

	Desktop  Examples  images  log  tutos

O Ubuntu ativa a coloração dos arquivos e das pastas por default, você deveria então ver tudo colorido. As pastas aparecem em azul escuro. Você poderá notar que a pasta `Examples` está em azul claro: isto significa que é um atalho para uma pasta que está em outro lugar no disco.

> Se a cor não aparecer, você pode adicionar o parâmetro `--color=auto`, assim: `ls --color=auto`. Se ao contrário você não quer ter cor, use o parâmetro `--color=none`.

O comando `ls` aceita um grande número de parâmetros. Não é viável citar todos aqui; no entanto, nós vamos descobrir os parâmetros mais úteis. Isto vai te treinar a usar e combinar comandos.

**-a: listar todos os arquivos e pastas escondidos**

No Linux, é possível "esconder" arquivos e pastas. Isto não é uma proteção, pois sempre é possível os listar quando queremos. É mais usado para não lotar sua tela.

A sua pasta `home` é um bom exemplo pois ele é cheio de arquivos e pastas escondidos. Adicionando o parâmetro `-a`, é possível ver todos os arquivos e pastas escondidos.
> josuegrace@josuegracestudy:~$ ls -a

	.                               .gnome                .nano_history
	..                              .gnome2               .nautilus
	.armagetron                     .gnome2_private       .openoffice.org2
	.bash_history                   .gnome_private        .pgadmin3
	.bash_logout                    .gstreamer-0.10       .pgpass
	.bashrc                         .gtkrc-1.2-gnome2     .profile
	.blender                        .gweled               .qt
	.config                         .ICEauthority         .recently-used
	.DCOPserver_mateo21-desktop__0  .icons                .recently-used.xbel
	.DCOPserver_mateo21-desktop_:0  images                .ssh
	Desktop                         .inkscape             .sudo_as_admin_success
	.dmrc                           .java                 .themes
	.emilia                         .jedit                .thumbnails
	.esd_auth                       .kde                  .Trash
	.evolution                      .lesshst              .tsclient
	Examples                        .lgames               tutos
	.face                           .local                .update-manager-core
	.fontconfig                     log                   .update-notifier
	.gaim                           .macromedia           .vlc
	.gconf                          .mcop                 .wormux
	.gconfd                         .mcoprc               .Xauthority
	.geany                          .metacity             .xine
	.gimp-2.2                       .mozilla              .xsession-errors
	.gksu.lock                      .mozilla-thunderbird


Agora você entende porque esses arquivos são escondidos: a lista é longa.
Dos elementos que começam por um ponto "." alguns são pastas, outros arquivos. A melhor forma de diferenciar é comparar as cores: as pastas são em azul, o resto tem uma cor por default (branco por exemplo, ou preto).

Os dois primeiros são um pouco estranhos: "." e "..". O primeiro representa na verdade a pasta atual, e ".." representa a pasta pai, ou seja, a pasta precedente na arborescência. Por exemplo, aqui estou no `home/josuegrace`, ".." representa então a pasta `home`.

> O parâmetro `-A` (a maíusculo) tem o mesmo significado: ele lista a mesma coisa menos os elementos "." e "..". Tome cuidado com as letras maíusculas!

**`-F`: indicar o tipo do elemento**
Esse parâmetro é muito útil para quem não usar a cor no terminal. Ele acrescenta um símbolo no final dos elementos para que se possa fazer uma distinção entre arquivos, pastas, atalhos...

> josuegrace@josuegracestudy:~$ ls -F
	Desktop/  Examples@  images/  log/  tutos/

Com isso, é possível ver que todos são pastas menos `**Examples**` que é um atalho (por causa da presença do `**@**`).

**`-l`: lista detalhada**

O parâmetro `-l` é um dos mais úteis. Ele mostra uma lista detalhando cada elemento da pasta.

> josuegrace@josuegracestudy:~$ ls -l

	total 16
	drwxr-xr-x 2 josuegrace josuegrace 4096 2007-09-24 17:22 Desktop
	lrwxrwxrwx 1 josuegrace josuegrace   26 2007-09-19 18:31 Examples -> /usr/share/example-content
	drwxr-xr-x 2 josuegrace josuegrace 4096 2007-09-25 15:17 images
	drwxr-xr-x 3 josuegrace josuegrace 4096 2007-09-25 11:11 log
	drwxr-xr-x 3 josuegrace josuegrace 4096 2007-09-19 19:51 tutos

Vamos linha por linha.
Cada coluna tem seu próprio significado. Da esquerda para direita:

	1. direitos sobre o arquivo (teremos um capítulo inteiro explicando o funcionamento dos direitos no Linux);
	2. número de links físicos;
	3. nome do proprietário do arquivo (aqui no caso sou eu!). Se o arquivo fosse criado por uma outra pessoa, patrick por exemplo, o seu nome apareceria no lugar do meu;
	4. grupo no qual pertence o arquivo (falaremos disto no capítulo sobre os direitos). É possível que o nome do grupo seja o mesmo que o do proprietário;
	5. o tamanho do arquivo, em bytes;
	6. a data da última modificação;
	7. nome do arquivo (ou pasta).

	> Você vai notar que no caso do atalho (se diz **link símbolico**), o comando precisa para onde aponta o atalho (neste caso /usr/share/example-content).

**`-h`: mostrar o tamanho em Ko, Mo, Go...**

Quando se faz um `ls -l`, o tamanho aparece em bytes. O problema é que às vezes não é legível. Por exemplo:
> josuegrace@josuegracestudy:~$ ls -l

	total 9500
	-rw-r--r-- 1 root root 3576296 2007-04-03 17:05 Experience ubuntu.ogg
	-rw-r--r-- 1 root root  229674 2007-04-03 17:05 fables_01_01_aesop.spx
	-rw-r--r-- 1 root root  848013 2007-04-03 17:05 gimp-ubuntu-splash.xcf
	-rw-r--r-- 1 root root 1186219 2007-04-03 17:05 kubuntu-leaflet.png
	-rw-r--r-- 1 root root   47584 2007-04-03 17:05 logo-Edubuntu.png

Se você adiciona o parâmetro `h` ("h" para dizer *Human Readable*, "legível para humanos"), você vai ter os tamanhos dos arquivos de um jeito mais legível (normal, se você é humano):
> josuegrace@josuegracestudy:~$ ls -lh

	total 9,3M
	-rw-r--r-- 1 root root 3,5M 2007-04-03 17:05 Experience ubuntu.ogg
	-rw-r--r-- 1 root root 225K 2007-04-03 17:05 fables_01_01_aesop.spx
	-rw-r--r-- 1 root root 829K 2007-04-03 17:05 gimp-ubuntu-splash.xcf
	-rw-r--r-- 1 root root 1,2M 2007-04-03 17:05 kubuntu-leaflet.png
	-rw-r--r-- 1 root root  47K 2007-04-03 17:05 logo-Edubuntu.png

Com isso, podemos ver que o arquivo `Experience ubuntu.ogg` tem 3,5 Mb, `logo-Edubuntu.png` tem 47 Kb, etc.

**`-t`: filtrar por data da última modificação**

Aqui está uma opção cujo o interesse é subestimado! `-t` permite filtrar por data de última modificação, em vez de filtrar por ordem alfabética por default.

Vemos então em primeiro lugar o último arquivo que modificamos, e em último o que não foi modificado por muito tempo.
> josuegrace@josuegracestudy:~$ ls -lt

	total 16
	drwxr-xr-x 2 mateo21 mateo21 4096 2007-09-25 15:17 images
	drwxr-xr-x 3 mateo21 mateo21 4096 2007-09-25 11:11 log
	drwxr-xr-x 2 mateo21 mateo21 4096 2007-09-24 17:22 Desktop
	drwxr-xr-x 3 mateo21 mateo21 4096 2007-09-19 19:51 tutos
	lrwxrwxrwx 1 mateo21 mateo21   26 2007-09-19 18:31 Examples -> /usr/share/example-content

Na prática, combinamos `-t` com `-r` que inverte a ordem de listagem dos arquivos. Às vezes a gente prefere ver o último arquivo modificado por último na lista. Combinamos também às vezes todos os parâmetros que acabamos de ver, o que dá um bonito `ls -larth` que podemos lembrar facilmente. ;-)

> josuegrace@josuegracestudy:~$ ls -larth

	total 380K
	-rw-------  1 mateo21 mateo21   26 2007-09-19 16:40 .dmrc
	-rw-r--r--  1 mateo21 mateo21   89 2007-09-19 16:40 .gtkrc-1.2-gnome2
	-rw-------  1 mateo21 mateo21   16 2007-09-19 16:40 .esd_auth
	drwx------  2 mateo21 mateo21 4,0K 2007-09-19 16:40 .update-notifier
	lrwxrwxrwx  1 mateo21 mateo21   26 2007-09-19 18:31 Examples -> /usr/share/example-content
	-rw-r--r--  1 mateo21 mateo21  220 2007-09-19 18:31 .bash_logout
	drwxr-xr-x  4 root    root    4,0K 2007-09-19 18:31 ..
	drwxr-xr-x 10 mateo21 mateo21 4,0K 2007-09-25 16:03 .jedit
	-rw-r--r--  1 mateo21 mateo21 1,1K 2007-09-25 16:03 .pgadmin3
	drwxr-xr-x 47 mateo21 mateo21 4,0K 2007-09-25 16:03 .
	-rw-------  1 mateo21 mateo21 1,8K 2007-09-25 16:38 .bash_history
	-rw-------  1 mateo21 mateo21  17K 2007-09-25 16:52 .recently-used
	drwx------  2 mateo21 mateo21 4,0K 2007-09-25 16:54 .gconfd
	-rw-------  1 mateo21 mateo21   39 2007-09-25 17:18 .lesshst
	-rw-r--r--  1 mateo21 mateo21  53K 2007-09-25 17:21 .xsession-errors

> Ps: Esta lista foi reduzida pois há muitos arquivos no meu `home`.

O arquivo escondido ".xsession-errors" é então o último a ser modificado nesta pasta no meu computador.

> Em vez de reescrever `ls -larth` todas as vezes (é um pouco longo), é possível criar um "apelido", quer dizer um comando sinônimo. Por exemplo, podemos criar o "apelido" `ll` que é automaticamente transformado por Linux em `ls -larth`. Veremos como criar "apelidos" quando soubermos nos servir de um editor de arquivos.

## cd: mudar de pasta
------

Bom, faz muito tempo que estamos só nesta pasta `home` e nós gostaríamos de sair dela.
O comando que nós vamos estudar aqui se chama `cd`, uma abreviação de *Change Directory* (mudar de pasta). É um comando muito importante que você vai utilisar umas milliares de vezes na sua vida (no mínimo).

Ao contrário do `ls`, o comando `cd` não pega muitos parâmetros porém, apenas um: o nome da pasta dentro do qual você quer ir.

Se quisermos ir para raíz, basta digitar `cd /`:
> josuegrace@josuegracestudy:~$ cd /

	josuegrace@josuegracestudy:/$

> josuegrace@josuegracestudy:/$ pwd

	/

Note que agora que o prompt de comando mudou o `~` para `/` pois estamos na raíz. Vamos listar os arquivos e pastas que estão no `/`:
> josuegrace@josuegracestudy:/$ ls -F

	bin/    dev/   initrd/          lib/         mnt/   root/  sys/  var/
	boot/   etc/   initrd.img@      lost+found/  opt/   sbin/  tmp/  vmlinuz@
	cdrom@  home/  initrd.img.old@  media/       proc/  srv/   usr/  vmlinuz.old@

Você vai ver muitas pastas que nós descrevmos mais cedo neste capítulo. Vamos para subpasta `usr`:
> josuegrace@josuegracestudy:/$ cd usr

Vamos ver o que há dentro dela:
> josuegrace@josuegracestudy:/usr$ ls -F

	bin/  games/  include/  lib/  local/  sbin/  share/  src/  X11R6/

E o que há dentro da pasta `games` ?
> josuegrace@josuegracestudy:/usr$ cd games

	josuegrace@josuegracestudy:/usr/games$

Esquematicamente, acabamos de fazer o seguinte :
(inserir a imagem aqui)

Vamos supor agora que quero voltar na pasta anterior, ou seja, `/usr`. Como que eu faço ?

Podemos utilisar os dois pontos assim :
> josuegrace@josuegracestudy:/usr/games$ cd ..

	josuegrace@josuegracestudy:/usr$

Se nós quisessemos voltar de duas pastas, nós escreveriamos `../..` ("volta atrás, e volta de novo"). Isto nos levaria de volta para raiz:
> josuegrace@josuegracestudy:/usr/games$ cd ../..

	josuegrace@josuegracestudy:/$

Existem duas maneiras de mudar de pastas: indicando um **caminho relativo**, ou indicando um **caminho absoluto**.

#### Os caminhos relativos

Um caminho relativo é um caminho que depende da pasta dentro da qual você está. Nós usamos isto há pouco tempo atrás quando nós fomos para subpasta `games` de `usr` digitando apenas seu nome:
> josuegrace@josuegracestudy:/usr$ cd games

Fazendo isto, nós estamos usando um caminho relativo, ou seja, relativo à pasta atual. Se fizessemos isto desde a pasta raíz, daria um erro:
> josuegrace@josuegracestudy:/$ cd games

	bash: cd: games: Arquivo ou diretório não encontrado

Para poder ir no `games`, nós deveríamos primeiro indicar a pasta que a contêm. (`usr`):
> josuegrace@josuegracestudy:/$ cd usr/games

	josuegrace@josuegracestudy:/usr/games$ cd games

#### Os caminos absolutos

Ao contrário dos caminhos relativos, os caminhos absolutos funcionam não importa a pasta onde estamos. Ele é fácil de reconhecer: ele sempre começa pela raíz (`/`). Você deve depois fazer a lista das pastas dentro das quais você que entrar. Por exemplo, supondo que estou na pasta `home/josuegrace` e que eu quero ir para pasta `/usr/games`. Com um caminho absoluto:
> josuegrace@josuegracestudy:~$ cd usr/games

	josuegrace@josuegracestudy:/usr/games$

Se nós quisessemos fazer a mesma coisa com um caminho relativo, iria ficar assim:
> josuegrace@josuegracestudy:~$ cd ../../usr/games

	josuegrace@josuegracestudy:/usr/games$

O que significa "**volta atrás para / `home` depois volta atrás para `/` depois vai para frente para `usr` e finalemente vai para frente para `games`**"

Vai ser você que vai ter que escolher cada vez como escrever seu caminho.

#### Voltar ao repertório `home`

Se você quer voltar no seu repertório `home` pessoal, existem várias opções:
	* **O jeito bruto**: basta escrever o caminho absoluto inteiro:
	> josuegrace@josuegracestudy:/usr/games$ cd /home/josuegrace

		josuegrace@josuegracestudy:~$

	* **O jeito esperto**: mais curto e mais prático, você pode usar o apelido `~` que significa a mesma coisa.
	> josuegrace@josuegracestudy:/usr/games$ cd ~

		josuegrace@josuegracestudy:~$

	* **O jeito super esperto**: se não colocar nenhum parâmetro no comando `cd`, isto leva diretamente ao repertório pessoal.
	> josuegrace@josuegracestudy:/usr/games$ cd

		josuegrace@josuegracestudy:~$

#### Autocomplete do caminho

Esse truque é muito importante e você deve usar ele. A idea é simples: você está com preguiça de digitar : `cd /usr/games/algumaCoisa`. Então você vai simplesmente pedir ao computador para completar o caminho sozinho.

O autocomplete do caminho funciona da mesma maneira que aquele dos comandos que nós vimos no capítulo anterior: com a tecla `Tab`(Tabulação). Vamos fazer um teste juntos. Se coloque primeiro no `/usr`:
> josuegrace@josuegracestudy:~$ cd /usr

	josuegrace@josuegracestudy:/usr$

Depois digita apenas `cd ga`, e aperte `Tab`. É mágico, o nome da pasta foi automaticamente completado.

	josuegrace@josuegracestudy:/usr$ cd games/

Vamos volar agora no `/usr` e tentar apenas `cd l`, e depois aperte `Tab`. Nada acontece: isto significa que o computador não encontrou a pasta que corresponde à sua pesquisa, ou é porque há muitas pastas que começam por "l". Faça `Tab` de novo:
> josuegrace@josuegracestudy:/usr$ cd l

	lib/   local/
	josuegrace@josuegracestudy:/usr$ cd l

Há uma lista de pastas que começam com "l"!. Você pode agora refinar sua busca digitando mais uma letra. Digite por exemplo "o" para que o Linux advinhe que você quer entrar na pasta local. Digite então "o", e depois aperte `Tab`, e o nome será completado!

	josuegrace@josuegracestudy:/usr$ cd local/

## du: o tamanho das pastas
-----

O comando "`du`", *Disk Usage* (uso do dísco), dá as informações sobre o tamanho que cada pasta ocupa no seu dísco.

Vá para `/usr/games`, e digite `du`:
> josuegrace@josuegracestudy:~$ cd /usr/games

	josuegrace@josuegracestudy:/usr/games$ du
	5732    .

Como esta pasta não tem subpasta, o comando `du` nos dá o tamanho total de todos arquivos contidos dentro da pasta. Porém, se você vai para `home`, este contêm muitas subpastas. Neste caso, o comando `du` vai retornar o tamanho de cada subpastas, e depois o tamanho total no final ("."):
> josuegrace@josuegracestudy:/usr/games$ cd

	josuegrace@josuegracestudy:~$ du
	400     ./.Trash
	4       ./.themes
	32      ./.mozilla-thunderbird/8vyw6pqo.default/Mail/Local Folders
	36      ./.mozilla-thunderbird/8vyw6pqo.default/Mail
	12      ./.mozilla-thunderbird/8vyw6pqo.default/US
	...
	...
	264     ./.jedit/jars
	4       ./.jedit/macros
	380     ./.jedit/settings-backup
	856     ./.jedit
	82484   .

**`-h`: o tamanho para os humanos**

Nós vimos esse parâmetro para o comando `ls`. Então ele funciona da mesma forma com o comando `du`!
> josuegrace@josuegracestudy:~$ du -h

	400K    ./.Trash
	4,0K    ./.themes
	32K     ./.mozilla-thunderbird/8vyw6pqo.default/Mail/Local Folders
	36K     ./.mozilla-thunderbird/8vyw6pqo.default/Mail
	12K     ./.mozilla-thunderbird/8vyw6pqo.default/US
	...
	...
	264K    ./.jedit/jars
	4,0K    ./.jedit/macros
	380K    ./.jedit/settings-backup
	856K    ./.jedit
	81M     .

A minha pasta `home` ocupa então 81 Mb no dísco rigido.

**`-a`: mostar o tamanho das pastas E dos arquivos**

Por default, `du` só mostra o tamanho das pastas. Para ter também o tamanho dos arquivos, adicione então a opção `-a` (all):
> josuegrace@josuegracestudy:~$ du -ah

	...
	8,0K    ./.jedit/settings-backup/abbrevs~5~
	24K     ./.jedit/settings-backup/history~1~
	8,0K    ./.jedit/settings-backup/abbrevs~4~
	380K    ./.jedit/settings-backup
	44K     ./.jedit/pluginMgr-Cached.xml.gz
	856K    ./.jedit
	81M     .

**`-s`: mostar apenas o grande total**

Para ver apenas o espaço total que a pasta ocupa sem ver os detalhes das subpastas, use `-s` (combinado aqui com `-h` para mais legibilidade):
> josuegrace@josuegracestudy:~$ du -sh

	81M     .

A minha `home` ocupa 81 Mb.
