# 🦾 Embedded System

# 🖥️ Linguagem de Montagem
<div align="center"><a href="https://github.com/IsaacAlves7/devops/blob/master/pages/asm.md"><img src="https://user-images.githubusercontent.com/61624336/181294284-1d0ffc08-c687-4594-a7ec-de59536bb5f3.svg"></a></div><br />

Em geral, quando iniciamos um curso sobre uma linguagem de programação, começamos estabelecendo os conceitos básicos sobre ela. Porém, no caso da linguagem de montagem, também conhecida como **assembly** (usaremos frequentemente essa palavra do inglês), esse nem sempre é o caminho mais utilizado. Por que não?

<img src="https://user-images.githubusercontent.com/61624336/181294302-a1a3d074-dd89-4a40-9ef5-70af4bb05e21.svg" align="right">

O motivo principal está no fato de a linguagem de montagem ser muito próxima ao hardware. Ou seja, você precisa, com frequência, acessá-lo diretamente com os comandos da linguagem de montagem, escrevendo em registradores e memórias, por exemplo, para realizar o que deseja com o seu programa.

Entendendo que precisamos acessar o hardware diretamente de forma tão frequente com a linguagem de montagem, concluímos que precisamos conhecer bem a arquitetura desse hardware. Portanto, nas primeiras aulas, entenderemos as arquiteturas de hardware e os circuitos digitais mais comuns de um computador. Esteja certo de que isso facilitará o seu aprendizado da linguagem de montagem, permitindo que você a domine em qualquer arquitetura de hardware digital que necessite atuar no futuro.

Conheceremos uma arquitetura que inspirou e influenciou muitos projetos de computadores até os dias atuais: A **arquitetura von Neumann**. Como exemplo, veremos o primeiro computador com programa armazenado: O **computador IAS**.

> Seja paciente com o caminho de aprendizado antes de poder escrever programas em **assembly**. Depois disso e de ter de lidar com acesso a hardware, interrupções e acesso à memória, você realmente entenderá como a máquina funciona. Será como se seu cérebro tivesse sido religado, para que, a qualquer momento em que escrever um código, possa ver como a máquina o processa em profundidade.

## Processo de compilação de um programa
<div align="center"><img src="https://estacio.webaula.com.br/cursos/go0374/galeria/aula1/img/figura1.svg"></div>


## Como os computadores evoluíram?

### Evolução dos computadores
Antes de entramos nos detalhes da **arquitetura de von Neumann**, conheceremos a evolução dos computadores até chegarmos na organização interna de um computador atual. Veja abaixo:

<details><summary><b title="(click to open)">🖥️ Computadores Analógicos (1645-1945)</b></summary>
  &nbsp;
  
- Criados para uma finalidade específica;
- Os resultados da computação analógica são usados no próprio sistema;
- As variáveis utilizadas em computadores analógicos são analogias entre quantidades, como a intensidade de uma corrente elétrica, o ângulo de giro de uma engrenagem, o nível de água em um recipiente etc.;
- Exemplos de computadores analógicos– ábaco, régua de cálculo, mecanismo de Antikythera, máquina de Pascal e máquina das diferenças de Babbage (veja a seção Explore + para referências).
  
</details>

<details><summary><b title="(click to open)">🖥️ Computadores digitais (1945-1955)</b></summary>
  &nbsp;
  
- Conseguem resolver os problemas com o uso de operações que empregam diretamente os números;
- Máquinas projetadas para armazenar e manipular dados representados somente por algarismos ou dígitos. Estes últimos só podem assumir dois valores distintos, 0 e 1, daí a denominação computador digital;
- Podem resolver problemas com a utilização de uma sequência programada de instruções;
- Utilizavam, em geral, cartões perfurados para a entrada de dados e instruções;
- A primeira geração usava 19.000 válvulas, dispositivos eletrônicos já obsoletos atualmente, que tinham a função de controlar a corrente elétrica para amplificar a tensão de entrada;
- Exemplo: **ENIAC** (Computador e Integrador Numérico Eletrônico, em inglês, Electronic Numerical Integrator and Computer), da Universidade da Pennsylvania. Era usado pelo exército americano para o cálculo de tabelas de balística. Uma _máquina decimal_, ou seja, não baseada em `0s` e `1s` (binária) como as que conhecemos hoje. Para programar era preciso configurar cabos e chaves. O consumo de energia era alto para os padrões atuais de computadores, em torno de 200 kW.
  
</details>

<details><summary><b title="(click to open)">🖥️ Computadores digitais com transistores (1955-1965)</b></summary>
  &nbsp;
  
  - Trouxeram a evolução na redução do tamanho dos computadores, além de aumentar consideravelmente a capacidade de armazenamento;
  - O **transistor** funciona como um interruptor eletrônico, uma chave de liga e desliga, para executar operações lógicas com números binários.
  
</details>

<details><summary><b title="(click to open)">🖥️ Computadores digitais com circuitos integrados (1965-1980)</b></summary>
  &nbsp;
  
  - Os circuitos integrados, como o nome revela, integra inúmeros transistores e outros componentes eletrônicos em um único encapsulamento de dispositivo, miniaturizando as unidades de computadores;
  - Desde o desenvolvimento do primeiro microprocessador pela INTEL, em 1971, os computadores começaram a dar saltos em poder de processamento. O primeiro microprocessador comercial, o 4004, possuía 2.300 transistores integrados. O modelo 8086, primeiro da família x86, foi lançado em 1978;
  - Hoje, um Intel Core i7-6950X possui 4,7 bilhões de transistores.
  
</details>

## Organização interna de um sistema computacional
Conheceremos, agora, a organização interna de um computador atual.

### Componentes básicos de um sistema computacional atual
A figura 1 mostra os componentes básicos de um sistema computacional padrão. A distinção de componentes é a mesma em sistemas computacionais tão díspares como um computador pessoal, um **CLP** (controlador lógico-programável) industrial ou um microcontrolador, este último integrando todos esses componentes em um único circuito integrado (CI).

<img src="https://user-images.githubusercontent.com/61624336/181353587-1f33ad3b-9c4c-4836-9b66-4a89e01213af.png" align="right">

Vejamos, a seguir, a descrição de cada um dos componentes:

- A UCP, no inglês denominada como **CPU** (Central Processing Unit) incluia Unidade Lógica e Aritmética (ULA) e a Unidade de Controle (UC). É o componente principal de um sistema computacional, conhecido como **processador** ou **microprocessador** em um computador pessoal. Na execução das instruções que realiza, a UCP recebe dados armazenados na memória, tanto os códigos das instruções do programa armazenado como os dados a serem processados;
- A **memória** podem ser de diversos tipos em um computador (ex.:RAM (Random Access Memory), ROM, cache, registradores). A RAM é a memória principal, tendo a função de disponibilizar os códigos dos programas em execução e seus dados para o processamento pela UCP. Por isso, a RAM é tão importante quanto a UCP para o processamento de um programa;
- **Unidades de Entrada e Saída (E/S)** são dispositivos que trabalham na disponibilização dos dados de entrada e saída para processamento, permitindo as interações entre o computador com usuários e outros dispositivos externos, como monitor de vídeo, mouse, teclado, pendrive, HD, webcam, impressora, sistemas de aquisição de dados em laboratórios e indústrias, entre outros;
- **Barramento** ou BUS ou sistemas de vias é responsável por interligar todos os componentes de um sistema computacional. Trata-se de vias de comunicação compostas por diversos fios, ou trilhas, em uma placa de circuito impresso, pelas quais passam os dados digitais em processamento. Estes, como sabemos, são valores `0` ou `1` que representam números. Recordemos a seguir esse sistema de numeração.

## Sistema de numeração em computadores
<img src="https://user-images.githubusercontent.com/61624336/181509320-9e73fa40-5953-4bed-9bf9-f10a23f93ce6.svg" align="right">

A representação numérica utilizada por todos nós está na forma denotação posicional. Sabemos que um número é formado por algarismos. Nessa notação, dependendo da posição relativa do algarismo em um número, o seu valor é diferente.

Distintos sistemas de numeração possuem uma quantidade de algarismos também distintos.

> No **sistema de numeração decimal**, que utilizamos no dia a dia, a base é `10`, ou seja, temos algarismos de `0` a `9` para representar cada posição de um número. O valor total do número é a soma dos valores relativos de cada algarismo, que é dado pelo algarismo multiplicado pela base elevada à potência relativa à posição.

**Exemplo**:

<pre>
3765<sub>10</sub> = 3 x 10<sup>3</sup> + 7 x 10<sup>2</sup> + 6 x 10<sup>1</sup> + 5 x 10<sup>0</sup>
</pre>

O **sistema binário**, utilizado pelos computadores, possui apenas dois algarismos (0 e 1), sendo assim de base 2. Cada algarismo nessa base é conhecido como **bit**. Veja um exemplo com número binário de 4 bits:

**Exemplo**:
<pre>
1011<sub>2</sub> = 1 x 2<sup>3</sup> + 0 x 2<sup>2</sup> + 1 x 2<sup>1</sup> + 1 x 20 = 1110
</pre>

Com o conceito de notação posicional foi possível a conversão entre diferentes bases. Por exemplo, a conversão de base binária para base octal ou hexadecimal parte do princípio que os números octais e os números hexadecimais correspondem, respectivamente, a combinações de 3 e 4 algarismos binários (bits), permitindo uma fácil conversão entre estes sistemas, como pode ser visto no exemplo a seguir, que mostra o mesmo valor numérico em base octal, hexadecimal e binária.

![img02](https://user-images.githubusercontent.com/61624336/181380881-12ad27c9-06e4-4f78-bd40-aea405b6a693.png)

Na conversão da base decimal para uma base B, realizam-se divisões sucessivas do número decimal pelo número B, a base desejada. Essas divisões são feitas até que o quociente da divisão seja menor do que B. O número na base B será formado pelos restos e o último quociente das operações de divisão, sendo o último quociente o algarismo mais significativo, conforme exemplificado nas conversões da tabela a seguir.

<table>
  <tr>
    <td>18<sub>10</sub> = ?<sub>2</sub></td>
    <td>465<sub>10</sub> = ?<sub>8</sub></td>
    <td>3587<sub>16</sub> = ?<sub>16</sub></td>
  </tr>
  
  <tr>
    <td>18:2 = 9 (resto = <b>0</b>)</td>
    <td>465:8 = 58 (resto = <b>1</b>)</td>
    <td>3587:16 = 224 (resto = <b>3</b>)</td>
  </tr>
  
  <tr>
    <td>9:2 = 4 (resto = <b>1</b>)</td>
    <td>58:8 = 7 (resto = <b>2</b>)</td>
    <td>224:16 = 14 (resto = <b>0</b>)</td>
  </tr>
  
  <tr>
    <td>4:2 = 2 (resto = <b>0</b>)</td>
    <td><b>721<sub>8</sub></b></td>
    <td><b>E03<sub>16</sub></b></td>
  </tr>
  
  <tr>
    <td>2:2 = <b>1</b> (resto = <b>0</b>)</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
  
  <tr>
    <td>10010<sub>2</sub></td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
  
</table>

Na conversão da base decimal para uma base B, realizam-se divisões sucessivas do número decimal pelo número B, a base desejada. Essas divisões são feitas até que o quociente da divisão seja menor do que B. O número na base B será formado pelos restos e o último quociente das operações de divisão, sendo o último quociente o algarismo mais significativo, conforme exemplificado nas conversões da tabela a seguir.

- https://play.yduqs.videolib.live/home?token=3ee7e72c0fa1489ab67321a97ed1a28b

# A arquitetura de von Neumann

<div align="center">

| [<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d6/JohnvonNeumann-LosAlamos.jpg/300px-JohnvonNeumann-LosAlamos.jpg" width="110"><br><sub>John von Neumann</sub>](https://pt.wikipedia.org/wiki/John_von_Neumann) |
| :---: |
  
</div>

**John von Neumann** foi um matemático húngaro que viveu a maior parte da vida nos Estados Unidos e deixou contribuições significativas para a evolução dos computadores. A contribuição pela qual é lembrado até hoje consiste em um computador sequencial binário com o conceito de programa armazenado.

> **Saiba mais**: Um dos primeiros computadores do tipo foi o **IAS**, a máquina de von Neumann, concluído em 1952 no Princeton Institute for Advanced Studies, que dá a esse computador suas iniciais. O primeiro protótipo constitui a base de todos os computadores de propósito geral que o seguiram.

## Componentes da máquina de von Neumann
Os componentes básicos dessa arquitetura são mostrados na figura 2, a seguir.

<img src="https://user-images.githubusercontent.com/61624336/181512218-35428a3f-c7cc-466b-a051-8971940b22b6.png" height="277">

Vejamos, a seguir, a descrição de cada um desses componentes.

1. **Memória principal** = Armazena dados e instruções.

2. **Unidade Logica e Aritmética (ULA)** = Realiza operações lógicas e aritméticas com dados binários.

3. **Unidade de controle (UC)** = Interpreta e envia sinais de controle para executar as instruções armazenadas na memória. Com a ULA, forma a Unidade Central de Processamento (UCP).

4. **Dispositivos de entrada e saída (E/S)** = Enviam e recebem dados externos ao computador a partir de sinais de controle.

> **Comentário**: Os computadores atuais possuem as funções e a estrutura geral das máquinas com a arquitetura de von Neumann. Por isso, é apropriado incluir, neste ponto, uma breve descrição da operação do computador IAS, já citado como o primeiro baseado na arquitetura de von Neumann.

## O computador IAS
A memória do IAS possuía 1000 posições, denominadas **palavras**, cada uma consistindo em 40 bits, com dados e instruções armazenados na memória. Como mostrado na figura 3, a seguir, cada número é representado por um bit de sinal e um valor de 39 bits. As instruções de 20 bits são denominadas instruções da esquerda e da direita, cada uma com um código de 8 bits da operação a ser executada (opcode) e um endereço com 12 bits que determina uma posição na memória de 0 a 999.

### Formato de armazenamento de dados e instruções no computador IAS
![img03](https://user-images.githubusercontent.com/61624336/181519754-56dd3a7d-2d01-4029-afb2-d0d8f4a09be5.png)

Para executar as instruções de um programa, a unidade de controle do IAS efetua a busca das instruções na memória. As instruções são executadas uma de cada vez. A unidade de controle utiliza registradores internos no processo de execução das instruções. A figura 4, a seguir, apresenta um diagrama mais detalhado com esses registradores internos do computador IAS.

![img04](https://user-images.githubusercontent.com/61624336/181521641-7493e454-847e-4838-ab3d-4563f12dcdd3.png)

A seguir são apresentadas as descrições básicas desses registradores e uma ideia inicial de como eles são usados na busca e na execução das instruções.

> **Comentário**: _O processo de busca e execução de instruções em uma arquitetura_ é de importância crucial para o entendimento da linguagem de montagem. Ele será mostrado posteriormente.

- **Registrador de endereçamento à memória** (Memory Address Register– MAR) guarda o endereço da memória de onde o dado do MBR será lido ou para onde o dado do MBR será transferido.
- **Registrador de instruções** (Instruction Register– IR) guarda um código de 8 bits, o _opcode_ da instrução que está sendo executada.
- **Registrador de armazenamento temporário de instruções** (Instruction Buffer Register– IBR) guarda, temporariamente, a instrução da direita de uma posição da memória.
- **Contador do programa** (Program Counter– PC) guarda o endereço da próxima instrução a ser buscada na memória, instrução essa que vem em pares.
- **Registrador temporário de dados** (Memory Buffer Register– MBR) funciona como buffer (armazenamento temporário de dados) da memória, guardando o dado (palavra) a ser transferido para a memória ou recebendo o dado da memória.
- **Acumulador** (Accumulator– AC) **e Quociente de Multiplicação** (Multiplier Quotient– MQ) são utilizados para guardar os operandos e o resultado de operações efetuadas na ULA, temporariamente. Quando se realiza uma multiplicação de dois números de 40 bits, por exemplo, o resultado é um número de 80 bits. Dessa forma, os 40 bits mais significativos ficam no acumulador (AC) e os 40 bits menos significativos, no registrador de MQ.

- https://play.yduqs.videolib.live/index.html?token=0f4de707c0c741b7883cf18fc67f9aca

# Estruturas de interconexão em computadores
Vimos que todo computador possui um conjunto de componentes básicos:

- A UCP ⬌ a memória e os dispositivos de entrada/saída, que precisam se comunicar entre si, trocando dados.

É preciso que existam conexões entre os componentes básicos para que o processamento do programa armazenado aconteça. Essa coleção de caminhos que liga os vários módulos é chamada de **estrutura de interconexão**. Precisamos saber como cada um dos componentes funciona e que tipo de dados trocam para entender o projeto dessas **estruturas de interconexão**. Examinemos cada componente.

<img src="https://user-images.githubusercontent.com/61624336/181780076-a5aae974-7a2e-44e3-abcf-911c505660c3.png" align="left" height="197">

**Memória**: A figura 5, a seguir, mostra os dados e sinais de entrada e saída necessários em uma memória. A capacidade de armazenamento de uma memória é função direta do número de posições (ou palavras) que ela possui. O tamanho em bits de cada posição é igual, e cada posição possui um único endereço numérico. Usando sinais de controle (Leitura e Escrita, na figura), uma memória pode ser lida ou escrita na posição especificada por um endereço. O Endereço e os Dados (na figura) são conjuntos de bits em paralelo na entrada da memória (no caso de Dados, também na saída). O número de bits em paralelo depende, é claro, do número máximo de posições a ser endereçado (no caso do endereço) e do tamanho em bits de cada posição (no caso dos dados).

<img src="https://user-images.githubusercontent.com/61624336/181782236-f3e8a6fd-dc5b-4e0c-9c8d-457ede2d56b6.png" align="left" height="147">

**Entrada e Saída (E/S)**: Na figura 6, a seguir, vemos que os módulos de E/S funcionam de forma semelhante às memórias em termos das operações de leitura e escrita. Os dados são separados naqueles que irão para dentro ou para fora do computador (internos ou externos), sendo que um mesmo módulo de E/S pode controlar mais de um dispositivo externo. Chama-se de porta a cada interface de dispositivo externo. Sinais de interrupção também podem ser enviados para o processador a partir de um módulo de E/S.

<img src="https://user-images.githubusercontent.com/61624336/181809575-6a47b065-6d75-404b-bcce-9e39b5d77de2.png" align="left" height="107">

**Processador (UCP)**: A UCP, mostrada na figura 7, a seguir, inclui a ULA e a UC, processando instruções lidas de endereços da memória, lendo e processando dados desta, escrevendo dados depois de processados e usando sinais para controlar a operação de todo o sistema. Além disso, podem também receber sinais de interrupção vindo de um módulo de E/S.

A estrutura de interconexão deve atender aos diferentes tipos de transferência dentro do computador. Podemos identificar os principais tipos a seguir, o que irá definir os **caminhos de comunicação para o projeto da estrutura de interconexão do computador**.

1. **Memória para UCP**: O processador precisa ler uma instrução ou um dado da memória.
2. **UCP para a memória**: O processador precisa escrever um dado na memória.
3. **E/S para UCP**: O processador precisa ler dados de um dispositivo de E/S por meio de um módulo de E/S.
4. **UCP para E/S**: O processador precisa enviar dados para um dispositivo de E/S por meio de um módulo de E/S.
5. **Dispositivos de E/S para a memória**: Pelo acesso direto à memória (DMA), um módulo de E/S pode enviar e receber dados diretamente da memória, sem necessitar da UCP. Esse é um recurso disponibilizado para aumentar a velocidade de transmissão entre dispositivos.

## Interconexão por barramentos
A criação de barramentos em sistemas computacionais visa a reunir linhas de comunicação de bits em paralelo para transmitir em conjunto vários dígitos 0 e 1. Em geral, um computador precisa dispor internamente de endereços e dados para realizar as operações, como vimos nas estruturas de interconexão que examinamos anteriormente. Mas, como existe ociosidade no uso de cada via de endereço e dados de cada componente, essas vias poderiam ser compartilhadas.

Essa é a ideia do barramento, o compartilhamento dessas vias de endereço e de dados entre os diferentes componentes. Com isso, como mostrado na figura 8, a seguir, o barramento é composto por linhas de endereço, dados e controle. Este último é usado para controlar o sincronismo, estabelecendo quem tem acesso ao barramento e pode utilizar as linhas em cada intervalo de tempo. 

### Linhas de endereço, dados e controle em um barramento
![img10](https://user-images.githubusercontent.com/61624336/181825680-429d0f2b-669d-4f05-abb8-8e8ed7bc0902.png)

- https://play.yduqs.videolib.live/index.html?token=9c4bf8dd4d84484b85b4e2e260e6610b

# 💻 Linguagem de máquina e desempenho
Você, certamente, sabe que sistemas computacionais só entendem 0s e 1s. Esses números, os dígitos binários (bits), constituem a linguagem de máquina, ou seja, os códigos numéricos para as instruções que um computador específico pode executar diretamente.

Estando um nível abaixo da linguagem de montagem, a linguagem de máquina é difícil de ser lida e escrita, pois não se assemelha em nada à linguagem humana e seus códigos variam de computador para computador.

Desenvolveremos programas simples em linguagem de máquina para o computador IAS com o intuito de compreender melhor o hardware e a ligação estreita dessa linguagem com a linguagem de montagem.

Trataremos também de analisar o desempenho de arquiteturas de computadores. A melhora no desempenho dessas máquinas é uma das principais vantagens para o uso da linguagem de montagem. Veremos como calcular e comparar o desempenho de computadores baseado no tempo de execução das instruções.

## Relação entre as linguagens de programação
A **programação de computadores** depende de uma linguagem, uma sintaxe codificada que facilita ao programador ditar quais comandos o computador deve realizar para processar os dados. Nos primeiros computadores essa programação não possuía uma sintaxe ou palavras para representar os comandos. A programação tinha de ser feita com o uso dos códigos binários das instruções (opcodes), o que se convencionou chamar de **linguagem de máquina**. No computador IAS, por exemplo, o código binário da instrução que soma o dado do **registrador Acumulador** (`AC`) com uma **posição de memória** (`Mem[X]`), colocando o resultado no AC `(AC = AC + Mem[X])`, é dado por:

```asm
00000101
```

Para fugir da tarefa extenuante, os programadores pioneiros desenvolveram uma forma de traduzir os códigos binários para uma notação simbólica, mais próxima do entendimento humano. Essa forma foi um programa para fazer a tradução, chamado de **montador** (assembler). O montador traduz uma versão simbólica de uma instrução para uma versão binária. Por exemplo, a **instrução** descrita acima para o IAS `(AC = AC + Mem[X])`, pode ser escrita no montador como:

[![.RB](https://img.shields.io/badge/-IasAcMemX.asm-fff?style=social&logo=AssemblyScript&logoColor=orange)](#)

```asm
ADD M(X)
```

> O montador gera para essa instrução o código binário dado acima: `00000101`. Como você já deve saber, essa linguagem simbólica é chamada de **assembly** ou **linguagem de montagem**.

A **linguagem de montagem** trouxe ganhos evidentes em relação à tediosa linguagem de máquina.

- **Linguagem de máquina**: O uso da linguagem de máquina necessita que todos os códigos e endereços tenham de ser lembrados pelo programador. Além disso, é difícil alterar ou encontrar erros em programas escritos em linguagem de máquina. Sem esquecer que cada computador terá o próprio conjunto de códigos de instrução. Sendo assim, existe uma linguagem de máquina para cada arquitetura de computador.

- **Linguagem de montagem**: Já na linguagem de montagem, os mnemônicos podem servir à várias arquiteturas, pois a conversão destes nos opcodes corretos para a arquitetura usada é tarefa do montador. Mesmo assim, esta linguagem não pode ser considerada independentemente da máquina.

Mesmo trazendo facilidades, a linguagem de montagem ainda evidencia a necessidade de o programador pensar em cada passo que a arquitetura deve seguir para realizar o processamento dos dados. Essa característica traz a capacidade de operar no limiar de eficiência da arquitetura, controlando cada aspecto no desempenho do hardware. Fica claro que muitas linhas de código em assembly são necessárias para realizar funções, que em linguagens de nível mais alto tendem a ser realizadas com menos linhas de código.

> É inegável a produtividade trazida pelas linguagens de programação de alto nível e de seus compiladores, que convertem os programas escritos em instruções.

## Linguagem de máquina no IAS
A visualização da execução de algumas instruções em linguagem de máquina no computador IAS é importante para entender a arquitetura e a ligação estreita dessa linguagem com a linguagem de montagem.

> Executaremos instruções usando o <a href="https://www.ic.unicamp.br/~edson/disciplinas/mc404/2017-2s/abef/IAS-sim/">IAS Simulator - V 1.0.4</a>.

Vimos que o IAS funciona com a execução de programa armazenado na memória. No simulador para IAS nós escrevemos o nosso programa no campo _Enter Memory Map_ (entre com o mapa de memória). O **código em binário** que escrevemos nesse campo, ou que carregamos de um arquivo, será usado para preenchimento da memória com as instruções e os dados necessários ao processamento do nosso programa. O **simulador** apresenta um diagrama da arquitetura do IAS, no qual podemos acompanhar os registradores acionados durante a execução do programa. O simulador apresenta também os valores guardados nos registradores em cada passo da execução.

