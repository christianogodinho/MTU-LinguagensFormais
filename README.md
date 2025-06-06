# Trabalho da matéria de Linguagens Formais & Teoria da Computação

## Instruções

## 1 Do objetivo

A Máquina de Turing Universal (MTU) consiste em uma Máquina de Turing (MT) que recebe como entrada um par (*M*, *w*), onde *M* é uma Máquina de Turing e *w* é uma entrada para esta e a executa sob essa entrada. O Projeto Final desta disciplina consiste em implementar uma Máquina de Turing Universal Determinística (além da MTU ser determinística, *M* também será uma Máquina de Turing Determinística com fita finita à esquerda e infinita à direita) conforme a especificação que segue.

## 2 Da codificação

A entrada à MTU será a função de transição de uma MT, seguida por um separador e uma entrada para a MT. A função de transição da MT de entrada deverá ser codificada na forma de uma sequência de transições, seguidas, cada uma, por um separador. A MTU deverá parar aceitando a palavra de entrada se atingir o estado final (único) ou se atingir um estado (não-final) a partir do qual não há transição possível de ser disparada. Entretanto, no primeiro caso (parada em estado final) ela deve escrever após a palavra constante na fita (i.e. a partir do primeiro símbolo em branco à direita da palavra) "`#A`"; no segundo caso, deve escrever na mesma posição "`#R`”. Dessa forma, esse será o indicativo de quando a MT para aceitando ou rejeitando a entrada (observe-se que se a MTU para rejeitando uma palavra, então isso significa que a entrada não é uma palavra da linguagem aceita pela MTU e não que a MT parou rejeitando a sua palavra de entrada).

Uma transição da MT de entrada é definida pela seguinte tupla: estado origem; símbolo lido; símbolo escrito; movimento; estado destino. Cada um dos símbolos será definido como segue (por simplicidade, adota-se a numeração unária).

**Estado origem:** Cada estado será denotado por um símbolo “`q`” seguido de um número (em notação unária) que o identifica unicamente. O estado inicial, especificamente, será o estado "`q1`". O estado final (único, a partir do qual nenhuma transição se origina), será designado por "`qf`". A quantidade de símbolos “`1`” após o símbolo "`q`" identifica o estado (conforme notação numérica unária).

**Símbolo lido:** Cada símbolo será denotado por um símbolo “`a`” seguido de um número (em notação unária) que o identifica unicamente. O símbolo branco, especificamente, será “`b`”. A quantidade de símbolos “`1`” após o símbolo “`a`” identifica o símbolo (conforme notação numérica unária – note-se que dessa forma se é capaz de codificar qualquer quantidade enumerável de símbolos). O símbolo de início da fita será “`s`”.

**Símbolo escrito:** Conforme símbolo lido.

**Movimento:** Um símbolo do conjunto {`R`, `L`}, onde "`R`" denota movimento para a direita e “`L`” denota movimento para a esquerda.

**Estado destino:** Conforme estado origem.

Adota-se o símbolo separador de transições “`#`”; dessa forma, uma MT de entrada tem a forma "`q1a1a11Rq11#q11a11a111Lq11#···#q11a1111a11111Rqf`". Essa MT deve ser seguida do separador "`$`" e uma entrada (uma sequência conforme “símbolo lido"). Assim, uma possível entrada para a MTU seria “`q1a1a11Rq11#q11a11a111Lqf#q11a1a11Rq1$a1a11`”. Ao final do processamento dessa MT pela MTU, a fita deve conter a palavra “`q1a1a11Rq11#q11a11a111Lqf#q11a1a11Rq1$A11a111#A`", onde a substituição de “`a`” por “`A`” indica que o cabeçote está nessa posição (note-se que para a MT o símbolo é a concatenação do “`a`” com a quantidade de símbolos “`1s`” que o segue).
