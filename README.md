## Programação Funcional

#### Indice

1.  [Programação Funcional](#ProgFun)  
2.  [Expressões e Valores](#Expressoes)
3.  [Redução](#Reducao)
4.  [Tipos](#Tipos)
5.  [Funções e Definições](#FunDef)
6.  [Numeros Inteiros](#NumInt)
7.  [Definição de Funções Simples](#FunSimpl)
8.  [Números Reais](#NumReal)
9.  [Valores Relacionais e Lógicos](#ValReLog)
10. [Funções com Condicionais](#FunCond)
11. [Escrevendo Funções com Currying](#FunCurry)
12. [Caracteres e Strings](#CaracStr)
13. [Listas](#Listas)
14. [Lista por Compreensão](#ListCompr)
15. [Manipulando Listas com Funções](#ManipListas)
16. [Funções em Lista com Tuplas](#FuncLisTup)
17. [Descrevendo Listas a partir de Listas](#ListList)
18. [Operações Aplicativas em Listas](#ApListas)
19. [Operações em Listas com funções Acumulativas](#ListAcum)
20. [Recursão](#Recursao)

### [Programação Funcional (Haskell)]()<a name="ProgFun"></a>
Como o nome sugere, a essência da **Programação Funcional (PF)** como método de programação é a construção de funções. A utilização da palavra *função* é mais no sentido matemático do que no sentido utilizado nas linguagens de programação convencionais. Na matemática, uma função é um objeto que devolve uma lista de todas as variáveis para as quais ele varia, onde o resultado é construido por meio de uma fórmula (*algoritmo*) que calcula o valor correspondente. Assim, por exemplo, se escrevermos: **y = x^2** dizemos que **y** é função de **x** pois, quando **x** varia, **y** também varia como seu quadrado.

A Programação Funcional envolve notação e conceitos de classes ou conjuntos que soam familiares a qualquer pessoa com pouca experiência matemática. O principal papel do programador é construir a função para resolver um determinado problema. Essa função, que pode envolver outras funções, é expressa numa notação que obedece aos princípios matemáticos.

As funções definidas pelo programador são chamadas em P.F. de **scripts**.

O papel do computador é agir como um avaliador ou executor de expressões e impressor dos resultados. A expressão representa um valor a ser obtido, cuja tarefa o computador é capaz de realizar.

A forma básica de interação entre o programador e o computador é:
```
Lê -> Calcula -> Exibe
```
A seqüência de interação entre o programador e o computador é chamada de **seção**.

O ambiente de interação utilizado será o ambiente **Codebench** - É um ambiente de aprendizagem disponibilizado pelo [Instituto de Computação](https://codebench.icomp.ufam.edu.br) da UFAM, que permite a utilização de várias linguagens de programação. Nesse ambiente usaremos as linguagens **Haskell** e **Python 3** para escrever os *scrips*. Cabe observar que algumas características conceituais presentes em programação funcional não tem uma representações direta nas linguagens. A linguagem **Haskell** incorpora a maioria dos conceitos, porém a linguagem **Python** não implementa todos os conceitos.

Uma propriedade característica da P.F. é que uma expressão possui um valor bem definido, não importando a **ordem** da avaliação pelo computador. O significado de uma expressão é o seu **valor** e a tarefa do computador é encontrá-lo. Por exemplo o valor da expressão 6 * 7 é 42. 
Nos exemplos, a entrada fornecida pelo usuário por meio da interface interativa do Haskell será apresentada pelo sinal ">". 
```
> 6*7
42
```
Os scripts são na verdade uma lista de definições de funções, feitas pelo programador e gravado em arquivos com **\<nome do arquivo\>.hs** para a linguagem Haskell, que devem ser carregados no ambiente interativo da linguagem para a sua execução. 

A instalação dos ambientes das linguagens não será tratada neste texto.

Exemplos de definições de funções:
```
Script Haskell:

quadrado n = n * n

menor n m 
    | n <= m = n 
    | otherwise = m
```

O propósito da definição de uma função é fazer uma associação entre um *nome* e o cálculo do seu *valor*.

Um conjunto de associações entre nomes e seus valores é chamado de **contexto** ou **ambiente**. A interação do usuário com o ambiente de execução da linguagem é chamado de **seção**. O exemplo de uma seção é apresentado a seguir:
```
Ambiente Haskell:

> quadrado 3 + 4
49

> menor 3 4
3

> quadrado ( menor 3 4 )
9
```
O avaliador pode utilizar as associações para fazer simplificações. Algumas expressões podem ser avaliadas sem que seja indicado o contexto, por exemplo: 3 + 4.

Isto é possível porque algumas operações são consideradas primitivas e fazem parte do contexto inicial do avaliador (chamado **Prelude** em Haskell). As operações aritméticas (+, *, -, /, etc.) e fornecimento de operações pré-definidas (mod, div, even, odd, etc.) são exemplos do contexto inicial da linguagem Haskell.

Os *scripts* podem ser modificados a qualquer momento, submetidos ao avaliador e um novo contexto será iniciado. Podemos anexar ao *script* definido anteriormente as novas definições:
```
Script Haskell:

lado =  12

area = quadrado lado
```
```
> area          
144

> menor (area + 4) 150
148

```
### [Expressões e Valores]()<a name="Expressoes"></a>
**Expressão** é uma noção fundamental em P.F. Existem muitos tipos de expressões e nem todas podem ser descritas neste formalismo, mas todas possuem características comuns.

A característica mais importante da notação matemática é que uma **expressão** é usada somente para descrever (ou denotar) um **valor**.

O significado de uma expressão é o seu valor e nada mais. O valor de uma expressão depende somente dos valores dos seus constituintes e, essas subexpressões, podem ser substituídas pelos seus valores.

Uma expressão pode conter **"nomes"** para quantidades desconhecidas, embora seja comum na matemática entendermos que diferentes ocorrências do mesmo nome se referem ao mesmo valor, ainda que desconhecido.

Estes nomes são chamados **"variáveis"**, mas estas variáveis não variam como nas linguagens de programação convencionais, pois elas sempre denotam o mesmo valor. A esta propriedade chamamos de **Transparência Referencial**.

Entre os tipos de valores que uma variável pode denotar encontram-se: números (Inteiros ou Reais), valores-verdade (Booleanos), caracteres, tuplas (Pares), funções e listas.

### [Redução]()<a name="Reducao"></a>
O computador avaliar as expressões pela redução da expressão para a sua **"forma equivalente mais simples"** e imprime o resultado.
**Avaliação**, **Redução** ou **Simplificação** são intercambiáveis. Utilizaremos o símbolo **"=>"** para indicar **"reduzido a"**.

Como exemplo vamos mostrar as possíveis reduções para a expressão: **Quadrado (3 + 4)**, onde a definição de Quadrado é como segue:
```
Quadrado x = x * x
```
Redução-1:
```
Quadrado (3 + 4)    => Quadrado 7   (+)
                    => 7 * 7        (Quadrado)
                    => 49           (*)
```
Redução-2:
```
Quadrado (3 + 4)    => (3 + 4) * (3 + 4)    (Quadrado)
                    => 7 * (3 + 4)          (+)
                    => 7 * 7                (+)
                    => 49                   (*)
```
Nos exemplos os símbolos entre parênteses indicam a operação que foi utilizada para fazer a redução (ou transformação). Quando uma expressão não pode mais ser reduzida então ela é impressa.
No primeiro exemplo a ordem de aplicação das reduções foram: (+), (Quadrado), (\*). 
No segundo exemplo a ordem foi : (Quadrado), (+), (+), (\*). Assim a primeira opção gastou um número menor de reduções que a segunda. 

É importante fazer a distinção entre um valor e sua representação através de expressões.  A forma equivalente mais simples não é o valor,  mas, a sua representação.
Existem muitas representações de um mesmo valor, por exemplo o valor: "**quarenta e nove**", pode  ter as seguintes representações:

```
decimal         = 49
romano          = XLIX
Expressão       = 7 * 7
binário 16 bits = 0000000000110001
```
Uma expressão está na **forma canônica** ou **forma normal** se ela não pode mais ser reduzida.
Alguns valores não possuem representação canônica e outros não possuem representação finita. Ex. O número **PI** não possui representação decimal finita.
Algumas expressões não podem ser reduzidas porque elas não denotam valores bem definidos no sentido matemático. 
```
Ex. Uma divisão de um número qualquer por zero, 1/0. 
```
Uma tentativa de avaliar esta expressão pode ocasionar um erro ou cair numa seqüência muito longa sem produzir resultados.
Para manter a condição de que toda expressão deve denotar um valor, é conveniente introduzir um símbolo para representar o valor indefinido: **"NIL"**

### [Tipos]()<a name="Tipos"></a>
Na notação que iremos seguir, o universo de valores é particionado em coleções organizadas chamadas tipos. 
Os tipos podem ser:
- **Básicos**, cujos valores são chamados de primitivos. Os números, os valores booleanos e os caracteres.
- **Derivados**, cujos valores são construídos de outros tipos. O tipo par ou tupla: (tipo-1, tipo-2), onde "tipo-1" e "tipo-2" são os tipos que formam o par; ou a o tipo lista, cujo definição é : [ tipo ], que pode ser uma sequência de qualquer tipo definido.

Uma operação é efetuada na forma tradicional:
```
<operando>  <operador> <operando>
1 + 1
2 * 3
5 div 6
```
Uma expressão bem formada possui o seu tipo deduzido a partir dos tipos dos seus constituintes. A este princípio chamamos **"Tipagem Forte"**. 

A maior conseqüência da disciplina imposta pelo conceito de tipagem forte é que uma expressão que não possa ter o seu tipo identificada não é bem formada e será rejeitada antes de ser avaliada.
```
Script Haskell:

ay x =  'A'         
```
Para qualquer x, a resposta será constante e igual a 'A', sendo o tipo inferido "CHAR".
```
Script Haskell:

bee x  = x + ay x   
```
Ao identificado o tipo da função *bee*, há uma tentativa de somar o resultado de *ay* que é "CHAR", ocorrendo um erro de tipo. 

Existem dois estágios de avaliação para uma expressão : análise sintática e análise de tipo.

### [Funções e Definições]()<a name="FunDef"></a>

Uma **função** é uma regra de correspondência que associa cada elemento de um tipo A com um único elemento de um segundo tipo B. O tipo A é chamado tipo **fonte** (domínio) e o tipo B de tipo **alvo** (contra domínio).
```
f :: A -> B
```
O tipo de *f* é A->B , caso A e B tenham tipo. A função *f* toma argumentos em A e retorna resultados em B. Se *x* é um elemento de A, *f(x)* ou *f x* denota a aplicação de *f* para *x*.

O valor resultante da aplicação da função é o **único elemento** em B associado com *x* pela aplicação da regra de correspondência *f*.

É importante separa a função da sua aplicação para um argumento. Em alguns textos matemáticos encontramos "a função *f*(x)" , quando o correto seria dizer a "função *f*" .Em tais textos funções raramente são consideradas como argumentos para outras funções.

Em Programação Funcional, funções são **valores como outro qualquer**, e podem ser passados como **argumentos para outras funções**.

É importante manter em mente a distinção entre um valor da função e uma particular definição dela. Existem muitas definições possíveis para a mesma função:
```
Script Haskell:

dobro1 x = x + x

dobro2 x = 2 * x
```
Apesar dos procedimentos diferentes para obter a correspondência entre o argumento e o resultado, as funções **dobro1** e **dobro2** denotam a mesma função e podemos afirmar que, "dobro1 = dobro2" é matematicamente verdade.

Dependendo do procedimento escolhido uma definição pode ser mais ou menos eficiente, no sentido de que as reduções de uma implementação podem ser menores, portanto mais rápida, que de uma outra.

### [Números Inteiros]()<a name="NumInt"></a>

Em Programação Funcional, há dois tipos básicos de números: os números **inteiros (Int)** e os números **reais (Float)**. Cada linguagem usa um identificador própio para nomear seus tipos, portanto é necessário descobrir qual o nome utilizado pela linguagem que será usada, por exemplo os inteiros são denominados **Int** em **Haskell** e **int** em **Python**. Essas linguagem possuem outras denominações com faixas maiores para estes tipos de números. 

#### Operadores
Os **Operadores Aritméticos** são os símbolos que representam certas transformações entre um número ou um grupo deles. 

Os símbolos dos operadores aritméticos utilizados na programação funcional para inteiros, são os mesmos utilizados na matemática. 

Abaixo é apresentada uma tabela com os principais operadores para inteiros e suas respectivas denominações:

|operador | denominação|
|---------|------------|
| + | adição|
| - | subtração |
| * | multiplicação|
| / | divisão |
| ^ | exponenciação |
| div| divisão inteira |
| mod | resto inteiro |
| even | é  par |
| odd | é ímpar |

#### Expressões
As Expressões Aritméticas podem ser aplicadas juntas numa única expressão aritméticas para gerar um valor. 

Quando várias operações aparecem juntas na expressão, certas regras de precedência são providenciadas para resolver possíveis ambiguidades. 

A precedência das regras para operadores aritméticos, segue a seguinte ordem de cima para baixo na tabela:

| operador | denominação|
|----------|------------|
| ^ | exponenciação |
|* , / , div , mod |operadores de multiplicação |
|+ , - | operadores de adição|

  

Quando os operadores surgem numa expressão com o mesmo nível de precedência, é aconselhável usar parenteses para evitar ambiguidades.

Na PF as expressões são escrita como na matemática elementar, ou seja:
```
Ambiente Haskell:

> ((3 + 5) * 6) / (9 ^ 2)
0.5925925925925926
```
Verifique a expressão acima sem os parenteses no ambiente de programação.


#### Intervalos
Os Intervalos podem ser vistos como uma série de números gerados a partir de uma definição matemática, ou seja, um conjunto de elementos enumerados.

Se quisermos os números inteiros de 1 a 10, basta escrevermos estes dois números entre colchetes, separados por dois pontos seguidos. Assim temos **[1..10]** indicando que queremos um conjunto de números inteiros. Os números gerados, podem ser vistos como uma *lista* de números inteiros. Os números 1 e 10 são chamados de **limitadores**. Podemos colocar quaisquer limitadores desde que sejam números inteiros.

A maneira de escrever intervalos é na forma **[a..b]**, onde **a** e **b** são números inteiros, indicando que haverá uma lista de números inteiros incrementados na ordem de **a** para **b**,aumentando de 1 em 1. 

Se o valor de *a > b*, então o resultado será uma lista sem números, ou seja, uma **lista vazia**.

Exemplos de intervalos em programação funcional :
```
Ambiente Haskell:

>[1,3..9]
[1, 3, 5, 7, 9]

>[1..3]
[1,2,3]

>[0,2..8]
[0, 2, 4, 6, 8]

>[0..9]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Uma outra maneira de escrever intervalos é na forma **[a,b..c]**, que indica uma progressão aritmética **a,a+d,a+2*d,...,** e assim por diante, onde **d = b - a**.

#### Tuplas
As Tuplas são vistas como uma combinação de elementos com o objetivo de formar novos elementos, pelos pares de elementos formados.

Se quisermos ter dois números agrupados, formando um par, basta os colocar entre parenteses separados por virgula, ou seja, (1,2). 

Isto significa uma tupla, formada pelo par de números inteiros (Int,Int).

Como podemos observar as tuplas são definidas por elementos entre parenteses, com isso as tuplas podem possuir vários elementos, na forma **(x1,x2,...xn)** onde cada elemento pode ser uma expressão **x1,x2,...,xn** e possuindo os tipos **t1,t2,...,tn**, respectivamente. 

No exemplo acima, os tipos são inteiros.

Para formar os elementos da tupla podemos nos valer de expressões aritméticas como:
```
> (4+2,3-1)
(6, 2) 

> ([2,3,4],3-1)
([2, 3, 4], 2)
```

### [Definição de Funções Simples]()<a name="FunSimpl"></a>
O ambiente da PF pode ser visto como uma calculadora bastante atraente que possui algumas funções e operadores embutidos. 

Porém, para resolver problemas mais sofisticados e que atenda a determinados requisitos, necessitamos definir novas funções para a resolução do problema. 

Essas funções seguem a definição matemática onde **f x -> y**.

Podemos definir uma função para somar dois números inteiros, escrevendo **soma x y = x + y**, onde *x* e *y* são parâmetros que recebem diferentes valores, para obter o resultado da função.

As linguagens possuem alguma funções pré-definidas como por exemplo, em Haskell, a função **sum** que calcula o somatório e **product** que calcula o produtório. 

A sintaxe dessas funções é colocar a função na frente de um intervalo de números inteiros, ou seja, **sum [1..10]** gerando o valor **55**.

#### Atributos Locais
As definições de funções podem incluir definições de valores com definição local. 

Nas descrições matemáticas frequentemente achamos expressões qualificadas pela palavra *"onde"* (*where* em inglês). 

Como exemplo observe a seguinte função :
```
              f(x,y) = (a+1) * (a+2),  onde a = (x+y)/2.
```

O mesmo dispositivo pode ser utilizado nas definições de atribuições locais para funções:
```
Script Haskell:

f x y = (a + 1) * (a + 2)
        where a = (x + y) / 2
```
O sinal "=" é usada para introduzir uma definição local.

#### Operadores e Funções
Os operadores e funções possuem diferenças, quanto ao seu posicionamento entre os parâmetros em PF. Os operadores sempre tratam com dois argumentos, ou seja, sua avaliação sempre requisitará somente dois elementos, sendo por este motivo também chamados de **operadores binários**.

A função, pode receber desde nenhum argumento, até um número conveniente para o problema a ser solucionado. Pode-se afirmar que a grande diferença entre operadores e funções, está na forma de escreve-los junto aos seus argumentos.

Quanto ao posicionamento entre os argumentos, os operadores são colocados entre os seus dois operandos e as funções são frequentemente colocadas antes dos seus parâmetros.

Para executar a adição entre dois números com o operador "+" temos, 2 + 2. Com a função definida como **soma**, temos **soma 2 2**. Podemos chamar um operador como uma função usando parenteses, por exemplo o operador "+":
```
> (+) 2 3
5
```
 Podemos chamar uma função como operador usando o aspas simples para esquerda, como exemplo usaremos a função "soma":
```
soma x y = x+y

> 5 `soma` 7
12
```

### [Números Reais]()<a name="NumReal">
Os números **reais** são muitas vezes conhecidos por **fracionais** e também por **ponto flutuante**. Em PF são denominados pelo tipo **Float**.

Um valor numérico somente será tratado como número de ponto flutuante se ele possuir o ponto decimal como por exemplo o número 3.14159.

As operações aritméticas básicas definidas sobre os inteiros, + , - , *, /, também estão definidas para os reais. 

Porém não há resto de divisão e a operação de exponenciação na forma , *Float -> Int -> Float*, elevando reais a inteiros. 

Abaixo mostramos a tabela dos operadores principais para números reais:

|Operador | Denominação|
|---------|------------|
|+|adição|
|-|subtração|
|*|multiplicação|
|/|divisão|
|^|exponenciação|
|sqrt|raiz quadrada|


Como nos números inteiros as expressões aritméticas podem ser vistas como uma série de operações aritméticas, efetuadas para gerar um valor. 

Também as regras de precedência são providenciadas para resolver possíveis ambiguidades. 

A precedência das regras para operadores aritméticos, segue a seguinte ordem :

|Operador|Denominação|
|--------|-----------|
|^|exponenciação|
|sqrt|raiz quadrada|
|* , / |operadores de multiplicação e divisão|
|+ , - |operadores de adição e subtração|

Quando os operadores surgem numa expressão com o mesmo nível de precedência, é aconselhável usar parenteses para evitar ambiguidades.

Em PF as expressões são escritas como na matemática elementar, ou seja, *((3.0 + 5.0) * 6.0) / (9.0 ^ 2)* e assim por diante. Teste a expressão acima sem os parenteses no ambiente de programação.


#### Intervalos
A definição de intervalos é a mesma de intervalos para números inteiros. Porém os limitadores e os elementos gerados, são números reais.

A maneira de escrever intervalos na forma **[a..b]**, onde **a** e **b** são números reais, indicando que haverá uma lista de números reais incrementados na ordem de **a** para **b**, aumentando na mesma proporção do primeiro limitador até chegar no segundo limitador. Se **a > b**, então o resultado será uma lista sem números, uma lista vazia.

Teste os seguintes exemplos: 
```
> [1.1..3.1]

> [1.1..3.2]

> [1.1..9.3]

> [9.0..1.0]
```
A outra maneira de escrever intervalos na forma **[a,b..c]**, indica uma progressão aritmética **a,a+d,a+2*d,...,** e assim por diante, onde **d = b - a**.

Teste o seguinte exemplos: 
```
> [1.1,1.2..3.1]
```
#### Tuplas
As tuplas são elementos formados por combinação de elementos. Conforme o número de elementos que a tupla possui, ela passa a ser chamada de **n-upla**. 

Geralmente não estamos interessados em trabalhar com 1-upla, e sim com duplas, triplas, etc.

As tuplas possuem vários elementos que não necessariamente pertencem ao mesmo domínio (tipo). Assim como definimos uma tupla (1,1) de tipo (Int,Int), podemos definir uma tupla *(1.0,1.0)* de tipo *(Float,Float)*, e uma tupla *(1.0,1)* de tipo *(Float,Int)*.

Podemos também usar expressões aritméticas e intervalos para fazerem parte de uma tupla, como por exemplo, **([1.1..3.1],[1,3..9])**, gerando a tupla **([1.1,2.1,3.1],[1,3,5,7,9])**.

Existem duas funções muito usadas para trabalhar com tuplas, são elas **fst** que pega o primeiro elemento da tupla e **snd** que pega o segundo elemento da tupla. 

A sintaxe é a função antes da tupla, assim, **fst (2.3,4)** gera o valor **2.3**

Já sabemos como definir funções simples, agora podemos definir novas funções para trabalhar com reais e tuplas. Para calcular a área de um círculo, definimos a seguinte função:
```
Script Haskell:

areacirc r = const * r ^ 2
                 where const = 3.14
```
Para pegar o primeiro elemento de uma dupla (2-upla)
```
fst (x,y) = x
```
Para pegar o segundo elemento de uma dupla (2-upla)
```
snd (x,y) = y
```

### [Valores Relacionais e Lógicos]()<a name="ValReLog"></a>
As palavras **verdadeiro** e **falso**, representam valores lógicos, significando se determinado valor de um determinado tipo (domínio), ao ser comparado a outro do mesmo tipo (domínio), é verdadeiro ou falso.

Esses valores são também chamados de **booleanos**, em homenagem ao matemático inglês **Geoge Boole** (1815-1864) que definiu uma álgebra a partir da lógica.

Nas linguagens de programação os valores verdadeiro e falso, são representados pelo tipo Bool, e são escritos **True** para verdadeiro e **False** para falso. 

Os valores Booleanos são importantes por retornarem valores de comparações entre expressões. 

Para comparar valores booleanos, precisamos de operadores específicos chamados de relacionais.

Abaixo, mostramos os operadores, seu significado e o resultado da operação:


|Operador|Descrição|Sintaxe|Resultado|
|--------|---------|-------|---------|
|>|maior|A > B|retorna True se o valor de A for maior que o de B senão retorna False|
|<|menor|A < B|retorna True se o valor de A for menor que o de B senão retorna False|
|==|igual|A == B|retorna True se o valor de A for igual ao de B senão retorna False|
|>=|maior ou igual|A >= B|retorna True se o valor de A for maior ou igual ao de B senão retorna False|
|<=|menor ou igual|A <= B|retorna True se o valor de A for menor ou igual ao de B senão retorna False|
|/=|diferente|A /= B|retorna True se o valor de A for diferente do valor de B senão retorna False|



#### Operadores
Os valores booleanos podem ser combinados usando operadores lógicos. Esses operadores servem para combinar determinadas comparações de valores lógicos.

Os operadores são:
```
    ||      (ou),
    &&      (e),
    not     (não).
```
Abaixo mostramos uma tabela de como os operadores funcionam com valores lógicos.

|Sintaxe|Descrição|Resultado|
|-------|---------|---------|
|A \|\| B|A ou B|retorna True se A ou B tiver o valor True|
|A && B|A e B|retorna True se A e B tiverem o valor True|
|not A|não A|retorna True se A tiver o valor False|

As possíveis combinações dos valores lógicos A e B , leva a construção da tabela verdade .

#### Expressões Lógicas

Podemos ver as expressões lógicas, como expressões que geram valores lógicos. Teste os exemplos:
```
 > 1 <  2  &&  2 < 3           
 > not (1 < 2)      
 > 3 < 2  &&  (2 < 3 || 1 == 2)
```

O operador **not** (não) tem prioridade maior do que **&&** (e).

O operador **&&** (e) tem prioridade maior que **||** (ou).

Quando as operações lógicas possuírem a mesma prioridade, serão executadas da esquerda para a direita.

É uma boa prática colocar parenteses quando houver operadores da mesma prioridade.

#### Tuplas de Valores Lógicos e Números
Como visto em tuplas de inteiros e tuplas de reais, as tuplas podem possuir valores de diferentes tipos, sendo chamadas de **polimórficas**.

Acrescentamos mais um tipo na construção de tuplas, uma tupla com valores booleanos, **(Bool,Bool)**, que podem assumir True ou False. 

Abaixo mostramos operações que podem ser efetuadas com pares de valores com os tipos conhecidos.
```
>(4+2,4.0)
(6,4.0)

>(3,4) == (4,3)
False

>(3,6) < (4,2)
True
```

Exemplo da definição de uma função usando operadores lógicos. A função compara o valor de um número real com a constante pi.
```
Script Haskell:

igualPi x = x == const
        where const = 3.14
```

### [Funções com Condicionais]()<a name="FunCond"></a>

#### Notação com Guards

Em muitas situações precisamos definir o valor de uma função de acordo com os casos que podem ocorrer.

Consideremos a função que verifica o menor de dois números.
```
menor x y
 | x <= y = x
 | x > y = y
```
Essa definição consiste de duas expressões, cada qual distinguida pela expressão de valores booleanos, chamados de **guards** ("\|").

A primeira alternativa da definição diz que o valor de **menor x y** é **x** se a condição **x <= y** for verdadeira.

A segunda alternativa da definição diz que o valor de **menor x y** é **y** se a condição **x > y** for verdadeira.

Os dois casos, **x <= y** e **x > y** , testam exaustivamente todas as possibilidades, sendo então o valor da função menor definido para todos os valores **x** e **y**.

Outra maneira de definir a função menor é :
```
menor x y
 | x <= y = x
 | otherwise = y
```
A palavra especial "**otherwise**" pode ser vista como uma abreviação conveniente para a condição que retorna o valor **True** quando todos os "**guards**" anteriores retornaram o valor **False**.

Em geral, a expressão usando "**guards**" segue a forma:
```
f x1 x2 ... xn
 | condição_1 = exp_1
 | condição_2 = exp_2
   : 
 | condição_n = exp_n
```

#### [Escrevendo Funções com Currying]()<a name="FunCurry"></a>
Todas as funções que definimos até aqui, possuem **tipos** e geram valore que podem ser do mesmo tipo ou não.

Se **t1** e **t2** são tipos, então **t1 -> t2** é o tipo de uma função que, dado um argumento do tipo **t1** produz como resultado o tipo **t2**.

A função do tipo **t1 -> t2** é dita tendo argumentos do tipo **t1** e resultado no tipo **t2**.

Na matemática, o resultado da aplicação da função **f** para o argumento **x** é tradicionalmente escrita como **f(x)**. Em muitas situações, esses parenteses podem ser omitidos em PF.

Se **t1, t2 ,...,tn** são expressões de tipo então, **t1 -> t2 -> ... -> tn**.

A forma anterior pode ser usada como abreviação para o tipo **t1 -> ( t2 -> ( ... -> tn) ...)**

De maneira similar, a expressão na forma **f x1 x2 ... xn** é simplesmente uma abreviação para a expressão **(...((f x1) x2) ... xn)**.

Essas expressões de tipo podem ser escritas antes da definição de uma função, deixando claro os **tipos de argumentos** com que a função trabalha e o **tipo que resulta**.

Abaixo, seguem algumas funções e suas expressões de tipo.
```
f :: Int -> Int -> Int
f x y = (a + 1) * (a + 2)
        where a = (x + y) / 2

Areacirc :: Float -> Float
Areacirc r = const * r ^2
             where const = 3.14

igualPi :: Float -> Bool
igualPi x = (x == const)
            where const = 3.14

menor :: a -> a -> a
menor x y
 | x <= y = x
 | x > y = y
```
A função definida como menor é dita polimórfica. 

Considere a seguinte definição da função menor :

```
menor_1 x y
 | x <= y = x
 | x > y = y
```
Note que os argumentos da função menor_1 são escritos sem parenteses e sem virgula. Podemos colocar parenteses e escrever da seguinte forma :
```
menor_2 (x,y)
| x <= y = x
| x > y = y
```
As duas funções menor_1 e menor_2 são muito parecidas, mas há uma diferença: **elas tem tipos diferentes**.

A função menor_2 pega um argumento simples cujo valor consiste de um par de números; este tipo é da forma :
```
menor_2 :: (Int , Int) -> Int
```
A função menor_1, por outro lado, pega dois argumentos um de cada vez. Este tipo é dado por :
```
menor_1 :: Int -> Int -> Int
```

Em outras palavras, a função menor_1 pega um valor e retorna uma função que recebe um número como entrada e devolve outro número. Para cada valor **x** da expressão, devolve a função que pega o argumento **y** e retorna o minímo entre **x** e **y**.

Um outro exemplo é a função soma definida por :
```
soma x y = x + y
```
Tem a expressão de tipo Int -> Int -> Int. Para cada x, a função (soma x) "adiciona x para alguma coisa".

Esse simples dispositivo para substituir os argumentos como sequencia de argumentos é conhecido como "**currying**", em homenagem ao matemático americano
**Haskell Brooks Curry** (1900-1982), cujo trabalho na teoria da computação provê a base matemática para todas as linguagens de programação funcional.

Uma das vantagens do "**currying**" é que ele reduz o número de parenteses que usamos ao escrever as expressões.

#### [Caracteres e Strings]()<a name="CaracStr"></a>
Além dos tipos de **inteiros** (Int), **reais** (Float) e **booleanos** (Bool), as linguagens possuem o tipo **caractere** representados pelo tipo **Char**.

Os valores dos caracteres são escritos entre apóstrofos, como **'H', 'a', 's', 'k', 'e','l','l'**.

Todos os caracteres das linguagens de programação funcional seguem o padrão **ASCII** (American Standard Code for Information Interchange), possuindo inclusive caracteres especiais de controle.

Os caracteres, de acordo com o código ASCII, possuem um código que corresponde a um determinado número inteiro.

Existe uma função que faz este mapeamento denominada de **ord** de tipo: **Char -> Int**.

Existe também uma função que mapeia o código para o caractere correspondente.

A função é denominada de **chr** e é do tipo : **Int -> Chr**.

Em alguns ambientes, a utilização dessas funções faz necessário a importação do Módulo onde esta estão definidas antes da sua utiização:"**Import Data.Char**". Veja abaixo como se usa estas funções :
```
> ord 'a'
97

> chr 65
'A'

> ord '9'
57

> chr 9
'\t'
```
Observe que o número 9 é diferente do caractere '9'.

#### Strings

A *sequência de caracteres* é chamada de **string**. As strings são denotadas pelo uso de apas duplas.

A diferença entre **'a'** e **"a"** é que o primeiro é um elemento do tipo caractere e o último um elemento do tipo string, que pode ser visto como uma lista de caracteres de apenas um único caractere.

As strings são representadas pela expressão de tipo **String** ou por **[Char]**.

Existe uma função denominada **show** que exibe a String mesmo que ela possua caracteres especiais (caracteres de controle).

Alguns exemplos de string.
```
> "Isto eh um exemplo!"
Isto eh um exemplo

>show "Isto eh um exemplo!"
"Isto eh um exemplo!"
```

#### Tuplas

Como visto nas definições de tuplas de inteiros , tuplas de reais e tuplas booleanas, sabemos que elas são elementos polimórficos, ou seja, podem conter diferentes tipos na sua sua estrutura.

Os caracteres e as strings, também podem ser usados na formação de tuplas, na forma :
```
> ("HASKELL",2.0) 
("HASKELL",2.0)            

> ('a' , 97 , "codigo ASCII",True)
('a',97,"codigo ASCII",True)
```

#### [Listas]()<a name="Listas"></a>
Uma grande característica das linguagens de programação funcional é o uso de **listas**. 

As listas são um **conjunto ordenado de valores**. Temos o primeiro elemento da lista, o segundo elemento e assim por diante. 

As listas também são chamadas de **sequências**, um termo mais comum na linguagem matemática.

Para ilustrar, tomemos uma lista de compras de uma pessoa. A pessoa poderia não encontrar o que procura e voltar, a lista então teria sido vazia, ou poderia comprar frutas.

Porém, cabe salientar que a lista de que estamos falando trata sempre com elementos do mesmo tipo, portanto numa lista de frutas, não poderíamos ter nenhuma verdura.

Assim sendo, as listas são formadas por objetos do **mesmo tipo**. As listas são representadas pelos seus elementos (ou tipo), entre colchetes: **[Int], [Char], [Float]**.

#### Listas e Intervalos

Como visto em outros tópicos, a função **sum** trabalha com intervalos de números inteiros. Mas os intervalos podem ser vistos como listas, assim **[a..b]** denota um intervalo, ou uma lista,de inteiros que aumentam na direção de **a** para **b**, incrementado de **1**.

Por exemplo, a notação **[5..22]** especifica uma lista de números de **5** a **22** inclusive. A sequência aritmética de números é especificada de maneira similar; **[3,7..24]** especificando que a lista contém 3,7,11,15,19,23.

Se definirmos **[5..]**, denota uma lista infinita de números inteiros começando de 5, e se definirmos **[3,7..]** é uma sequência aritmética infinita começando com 3 e gerando todos os outros elementos adicionado de 4 mais o número anterior, uma progressão aritmética de razão 4, termo inicial 3.

#### Lista de Inteiros

Os números inteiros podem ser representados como elementos de uma lista. A palavra **[Int]**, denota uma lista de valores inteiros.

Alguns exemplos de listas e seus tipos :
```
[1,2,3] :: [Int]            -> lista de inteiros

[1..3] :: [Int]             -> lista de inteiros

[ [1, 2, 3] ] :: [[Int]]    -> lista de lista de inteiros

[ [1,2] , [3] ] :: [[Int]]  -> lista de lista de inteiros
```

#### Lista de Reais

Os números reais podem ser representados como elementos de uma lista. A palavra **[Float]**, denota uma lista de valores reais.

Alguns exemplos de listas e seus tipos :
```
[1.0,2.0,3.0] :: [Float]            -> lista de reais

[1.1..3.1] :: [Float]               -> lista de reais

[ [1.1,1.2,1.3] ] :: [[Float]]      -> lista de lista de reais

[ [1.1,2.1] , [3.1] ] :: [[Float]]  -> lista de lista de reais
```

#### Caracteres

Os caracteres podem ser representados como elementos de uma lista. A palavra **[Char]**, denota uma lista de valores de caracteres.

Alguns exemplos de listas e seus tipos :
```
['a','b','c'] :: [Char]             -> lista de caracteres

[ ['a','b','c'] ] :: [[Char]]       -> lista de lista de caracteres

[ ['a','b'] , ['c'] ] :: [[Char]]   -> lista de lista de caracteres
```

#### Strings

As strings podem ser vistas como uma lista de caracteres sem os colchetes, é um caso especial, tanto que para representar a string utilizamos a palavra **[Char]**, designando uma lista de caracteres.

As listas também podem utilizar as strings como elemento de formação. A palavra [[Char]], denota uma lista de strings.

Alguns exemplos de listas e seus tipos :
```
["gofer"] :: [[Char]]               
-> lista de string (lista de lista de caracter)

["gofer","toolbook"] :: [[Char]]    
-> lista de string (lista de lista de caracter)

[ ["gofer","toolbook"] ]:: [[[Char]]]   
-> lista de lista de string (lista de lista de lista de caracter)

[ ["gofer","toolbook"] , ["pascal"] ] :: [[[Char]]] 
-> lista de lista de string (lista de lista de lista de caracter)
```

#### Tuplas

As listas sempre devem possuir elementos do mesmo tipo, ao contrário das tuplas, a lista não é um elemento polimórfico .

As tuplas podem ser utilizadas como elementos na formação de uma lista. A sentença **[ (a,a) ]** denota uma lista de tuplas, sendo que a tupla pode possuir qualquer tipo.

Alguns exemplos de listas com tuplas e seus tipos :
```
[ (1,2), (3,4), (4,5) ] :: [(Int,Int)]
-> lista da tupla de inteiros

[ ( [1..9], "intervalo") ] :: [ ( [Int], [Char] ) ]
-> lista da tupla de lista de inteiros e string

[ ( [1.1..3.1] , True) ] :: [ ( [Int], [Bool] ) ]
-> lista da tupla de lista de inteiros e booleano

[ ( [True,False], ['a','b','c'] ) ] :: [ ( [Bool],[Char] ) ]
-> lista da tupla de lista de booleanos e lista de caracteres
```
#### [Lista por Compreensão]()<a name="ListCompr"></a>
Uma lista por compreensão é uma lista que possui uma descrição, na qual é definido como será a lista resultante.

Os *intervalos* podem ser vistos como uma lista por compreensão rudimentar. A técnica de construção faz uso da linguagem da teoria dos conjuntos.

A compreensão de conjuntos define como os elementos serão formados a partir de condições que devem ser satisfeitas para cada elemento do conjunto.

Por exemplo **{ x | x < 5, x >=0 }** especifica um conjunto contendo números entre 0 e 5, incluindo o 0.

A lista por compreensão é uma expressão que define os elementos da nova lista formada por definições previamente fornecidas,  as quais, todos os novos elementos devem satisfazer para pertencer a essa nova lista.

Observe a seguinte definição :
```
[ x | x <- [1..10] ]
```

Essa definição ilustra a notação **x <- [1..10]**, que significa que **x** deriva da lista **[1..10]**. Com isso a lista resultante é a mesma lista original do intervalo **[1..10]**. Que pode ser lido como, "**uma lista de elementos de x tal que x vem da lista [1..10]**". 

A lista seguinte gera uma lista de valores definidos por uma expressão **x*x**, onde **x** vem de uma lista **[1..10]** e **x** é deve satisfazer a propriedade de ser **par**.
```
>[x * x | x <- [1..10], even x]

[4,16,36,64,100]
```
#### Intervalo

A sintaxe definida para uma lista por compreensão consiste de uma **expressão** e um **qualificador** na seguinte forma :

[<expressão> | \<qualificador\>;...;\<qualificador\>]

Onde a **expressão** denota uma expressão arbitrária, e o **qualificador** pode ser uma expressão de valor **booleano** ou um **gerador**.

A forma para um gerador geralmente é :
```
<variável> <- [lista]

(<variavel>,<variável>) <- [(<lista>,<lista>)]
```
Observe os seguintes exemplos:
```
> [ (x,y) | x <- [2,3,4] , y <- [5,6] ]

[(2,5),(2,6),(3,5),(3,6),(4,5),(4,6)]
```
Que é [2,3,4] x [5,6] , ou seja, o produto cartesiano de [2,3,4] e [5,6]
```
> [ (i,j) | i <- [1..7], even i, j <- [i..7], odd j ]

[ (2,3) , (2,5) , (2,7) , (4,5) , (4,7) , (6,7) ]
```
Que é uma lista de duplas **(i,j)**, onde os **i** e **j** são gerados pela mesma lista, sendo que os **i's** são **pares** e os **j's** são **impares**.

#### [Manipulando Listas com Funções]()<a name="ManipListas"></a>

##### Função Null

Quando as listas não possuem nenhum elemento elas são vistas como listas vazias, ou nulas.

A função que verifica se uma lista é vazia é a função **null**, que devolve o valor booleano **True** se a lista for vazia.

Sua expressão de tipo é definida por :
```
null:: [a] -> Bool
```
Exemplos :
```
> null [] 
True

> null ['g','o','f','e','r']
False

> null [ [] ] 
True 

> null [ [], [1,2] ]
False
```

##### Função Head

Todas as listas não nulas possuem elementos ordenados, primeiro elemento, segundo elemento, terceiro elemento, e assim por diante.

O primeiro elemento da lista geralmente é chamado de "**cabeça**" da lista, e a função **head** seleciona o primeiro elemento da lista.

Sua expressão de tipo é definida por :
```
head :: [a] -> a
```
Exemplos :
```
> head [1] 
1 

> head [ 1 , 2 , 3 ]
1

> head "gofer" 
'g' 

> head [ [] , [ (2.0,2) ] ]
[]
```
Não existe "cabeça" de lista numa lista vazia.

##### Função Tail

As listas podem ser vistas como possuindo uma "**cabeça**" e um corpo, ou "**cauda**" da lista. A função **tail** seleciona todos os elementos da lista com excessão da "cabeça" da lista, ou seja, devolve a "cauda" da lista.

Sua expressão de tipo é definida por :
```
tail :: [a] -> [a]
```
Exemplos :
```
> tail [1] 
[] 

> tail [ 1 , 2 , 3 ] 
[2,3] 

> head (tail "gofer")
'o'

> tail [ [] , [ (2.0,2) ] ] 
[ [ (2.0,2) ] ] 

> tail (tail [1..9])
[3,4,5,6,7,8,9]
```
Não existe "cauda" de lista numa lista vazia.

##### Função Last

O último elemento da lista geralmente pode ser selecionado através da função **last**.

Sua expressão de tipo é definida por :
```
last :: [a] -> [a]
```
Exemplos :
```
> last [1] 
1 

> last [ 1 , 2 , 3 ]
3

> last "gofer" 
'r' 

> last [ [] , [ (2.0,2) ] ]
[ (2.0,2) ]
```
Não existe último elemento de lista numa lista vazia.

##### Função init

Podemos obter todos os elementos de uma lista não nula, exceto o último através de uma função chamada **init**.

Sua expressão de tipo é definida por :
```
init :: [a] -> [a]
```
Exemplos :
```
> init [1] 
[] 

> init [ 1 , 2 , 3 ]
[1,2]

> init "gofer" 
"gofe" 

> init [ [] , [ (2.0,2) ] ]
[ [] ]
```

##### Função Length

O tamanho de uma lista finita é o número de elementos que a lista possui. A função **length** denota o tamanho, ou comprimento de uma lista.

Sua expressão de tipo é definida por :
```
length :: [a] > Int
```
Veja os exemplos :
```
> length [] 
0 

> length [1,2,3]
3

> length "gofer" 
5

> length [ [] , [ (2.0,2) ] ]
2
```

##### Função Take

Podemos pegar os primeiros elementos de uma lista e exibi-los, bastando usar a função **take**.

A função **take** utiliza um número inteiro (que significa o número de elementos) e uma lista com elementos.

Sua expressão de tipo é definida por :
```
take :: Int > [a] > [a]
```
Veja os exemplos :
```
> take 3 [1..9] 
[1,2,3] 

> take 0 [ 1 , 2 , 3 ] 
[] 

> take 2 []
[]

> take 4 "gofer" 
"gofe" 

> take 2 [ [] , [ (2.0,2) ] ]
[ [] , [ (2.0,2) ] ]
```

##### Função Drop

Podemos gerar uma lista sem os primeiros elementos de uma lista e exibi-los, bastando usar a função **drop**.

A função **drop** utiliza um número inteiro (que significa o número de elementos) e uma lista com elementos.

Sua expressão de tipo é definida por :
```
drop :: Int -> [a] -> [a]
```
Veja os exemplos :
```
> drop 3 [1..9]                    
[4,5,6,7,8,9]  

> drop 0 [ 1 , 2 , 3 ]
[1,2,3]               

> drop 4 "gofer"
"r"                                                   

> drop 2 [ [] , [ (2.0,2) ] ]      
[]

> drop 2 []
[]                                              
```

##### Posição de um elemento na Lista

Os elementos de uma lista estão indexados a determinados valores começando de **0**, assim os valores de indexação variam de 0 até o tamanho da lista decrementado de **1**.

Observe o exemplo :
```
índices -> 0 1 2

lista -> [1, 2, 3]
```

Estes índices ajudam a localizar um elemento dentro da lista. O operador **!!** se utiliza dos índices para localizar um elemento na lista.

Sua sintaxe é 
```
<lista> !! <índice>.
```
Veja os exemplos :
```
> [1] !! 0 
1 

> [ 1 , 2 , 3 ] !! 2
3

> "gofer" !! 4 
'r' 

> [ [] , [ (2.0,2) ] ] !! 0
[]
```

#### [Funções em Lista com Tuplas]()<a name="FuncLisTup"></a>
Podemos gerar tuplas a partir de listas. A função **zip** utiliza os elementos de duas listas e gera pares com os elementos das listas, formando assim uma lista de tuplas.

A sintaxe do comando consiste de :
```
zip <lista> <lista>
```
Sua expressão de tipo é definida por :
```
zip :: [a] -> [b] -> [ (a,b) ]
```
Exemplos :
```
> zip [0..4] "gofer " 
[(0,'g') (1,'o')(2,'f'),(3,'e')(4,'r')] 

> zip [1,2] "oi"
[(1,'o')(2,'o')]

> zip [] [1..9] 
[] 

> zip [True,False] [1.0,2.0,3.0]
[(True,1.0)(False,2.0)]
```
Observe que se as listas não possuírem o mesmo tamanho, a lista de tuplas possuirá o mesmo tamanho da lista de menor tamanho.

Podemos gerar uma listas com o resultado da aplicação de uma operação definida sobre os elementos de outras duas listas. Os tipos devem ser compatíveis.

A função que trata deste tipo de operação é **zipWith**.

A sintaxe do comando consiste de :
```
zipWith <função/operador> <lista1> <lista2>
```
Sua expressão de tipo é definida por :
```
zipWith :: ( a -> b -> c ) -> [a] -> [b] -> [c]
```
Exemplos :
```
> zipWith (+) [1..3] [6..9]
[7,9,11]

> zipWith (*) [x | x <- [0..9], even x] [x | x <- [0..9], odd x]
[0,6,20,42,72]
```

Observe que se as listas não possuírem o mesmo tamanho, a lista resultante possuirá o mesmo tamanho da lista de menor tamanho.


#### [Descrevendo Listas a partir de Listas]()<a name="ListList"></a>

##### Operador ":"

Podemos adicionar um elemento a uma lista, desde que seja do mesmo tipo dos elementos da lista.

O operador que trata deste tipo de operação é **":"** (dois pontos).

A sintaxe do comando consiste de :
```
<elemento> <operador> <lista>
```
Sua expressão de tipo é definida por :
```
(:) :: a -> [a] -> [a]
```
Exemplos :
```
> [] : []
[ [] ]

> [] : [[1]]
[ [], [1] ]

> 0 : [1,2,3]
[0,1,2,3]

> (head [x | x <- [1..9], even x]) : [x | x <- [1..9], odd x]
[2,1,3,5,7,9]
```
##### Operador "++"

Podemos ligar duas listas através de uma operação de concatenação, desde que as listas possuam elementos do mesmo tipo. Os elementos da primeira lista são seguidos dos elementos da segunda lista.

A função que trata deste tipo de operação é "++" (dois sinais de adição).

A sintaxe da função consiste de :
```
<elemento> <operador> <lista>
```
Sua expressão de tipo é definida por :
```
(++) :: [a] -> [a] -> [a]
```
Exemplos :
```
> [] ++ []
[ ]

> [] ++ [1]
[1]

> [0] ++ [1,2,3]
[0,1,2,3]

> [x | x <- [1..9], even x] ++ [x | x <- [1..9], odd x]
[2,4,6,8,1,3,5,7,9]
```

##### Função Concat

Podemos ligar várias listas através de uma operação de concatenação, desde que as listas possuam elementos do mesmo tipo e estejam entre colchetes.

A função que trata deste tipo de operação é **concat**.

A sintaxe da função consiste de :
```
<concat> <lista de listas>
```
Sua expressão de tipo é definida por :
```
concat :: [[a]] -> [a]
```
Exemplos :
```
> concat[ [] , [] ]
[ ]

> concat [ [1], [2,3], [], [4,5,6] ]
[1,2,3,4,5,6]
```

#### [Operações Aplicativas em Listas]()<a name="ApListas"></a>

##### Função Map

As funções aplicativas são **funções de alta ordem** e estão initimamente relacionadas as listas por compreensão.

A função **map** aplica uma função a cada elemento da lista.

A sintaxe da função consiste de :
```
<map> <função> <lista>
```
Sua expressão de tipo é definida por :
```
map :: (a -> b) -> [a] -> [b]
```
Exemplos :
```
? map chr [65..70]
ABCDEF

? map sqrt [9.0,16.0,25.0]
[3.0,4.0,5.0]

? map (* 2) [ x | x <- [1..9],even x]
[4,8,12,16]
```
 
##### Função Filter

A função **filter** utiliza um predicado (condição) e uma lista e retorna uma sublista que satisfaz ao predicado (condição).

A sintaxe da função consiste de :
```
<filter> <predicado> <lista>
```
Sua expressão de tipo é definida por :
```
filter :: (a -> Bool) -> [a] -> [a]
```
Exemplos :
```
> filter even [0..9]
[0,2,4,6,8]

> (sum . filter even) [0..9]
20

> (filter even . map ord) "gofer"
[102,114]
```

Função TakeWhile

A função **takeWhile** é similar a função *take*, exceto que pega uma condição (predicado) como primeiro argumento ao invés de um número inteiro.

A sintaxe da função consiste de :
```
<takeWhile><predicado> <lista>
```
Sua expressão de tipo é definida por :
```
takeWhile :: (a -> Bool) -> [a] -> [a]
```
Exemplos :
```
> takeWhile even [2,4,6,1,5,6]
[2,4,6]

> takeWhile even [1..9]
[]

> takeWhile (== 'e') (tail "Beethoven")
ee
```

Enquanto a condição for satisfeita a sublista é gerada.

##### Função DropWhile

A função **dropWhile** é similar a função *drop*, exceto que pega uma condição (predicado) como primeiro argumento ao invés de um número inteiro.

A sintaxe da função consiste de :
```
<dropWhile> <predicado> <lista>
```
Sua expressão de tipo é definida por :
```
dropWhile :: (a -> Bool) -> [a] -> [a]
```
Exemplos :
```
> dropWhile even [2,4,6,1,5,6]
[1,5,6]

> dropWhile even [1..9]
[1,2,3,4,5,6,7,8,9]

> dropWhile (=='e') (tail "Beethoven")
"thoven"
```

Enquanto a condição for satisfeita são retirados os elementos e a sublista é gerada.

#### [Operações em Listas com funções Acumulativas]()<a name="ListAcum"></a>

##### Função Foldr

As funções acumulativas são aquelas que dada uma **função** ou **operador** e um **valor de acumulação** (normalmente o elemento neutro na operação), é capaz de gerar um elemento que acumula os valores indicados na definição.

Uma função que trata deste tipo de operação é **foldr**.

A sintaxe do comando consiste de :
```
foldr <função/operador> <elemento neutro> <lista>
```
Exemplos :
```
> foldr (+) 0 [1..9]
45

> foldr (*) 1 [1..5]
120

> foldr (++) " " ["gofer", "lisp"]
"goferlisp "
```

##### Função Foldl

Uma função que trata deste tipo de operação é **foldl**.

A sintaxe do comando consiste de :
```
foldl <função/operador> <elemento neutro> <lista>
```
Exemplos :
```
> foldl (+) 0 [1..9]
45

>foldl (*) 1 [1..5]
120

>foldl (++) " " ["gofer", "lisp"]
" goferlisp"
```

#### [Recursão]()<a name="Recursao"></a>
A recursão é uma técnica bastante poderosa na programação funcional que permite que uma função seja definida através dela mesma. A introdução deste conceito pode ser melhor compreendida por uma pequena história, a história de Martin e o Dragão.

Suponha que calculemos o fatorial de um número inteiro. Podemos dividir o problema em dois casos especiais:
```
* se n = 0 então o valor de n! é 1

* caso contrário , n! = 1 * 2 * ... * (n-1) * n = (n - 1)! * n
```

Podemos calcular o valor de **n!** calculando o valor de **(n-1)!** e então multiplicando esse valor pelo valor de **n!**

Em PF, essa definição pode ser escrita da forma :
```
fat n
 | n == 0 = 1
 | otherwise = n * fat (n - 1)
```
Observe que a própria função **fat** se encarrega de "*chamar*" a si mesma, ou seja, foi definida em termos dela mesma.

#### Recursão em Listas

As listas são estruturas recursivas por excelência.
Observe a função que verifica se algum elemento de uma lista é ímpar.
```
qqimpar (xs)
 | null (xs) = False
 | odd (head xs) = True
 | otherwise = qqimpar (tail xs)
```

Se a lista for **nula** (acabou os elementos) ela retorna **False**. Se o primeiro elemento da lista é **impar** retorna **True**. Caso contrário chama a sua própria definição para a cauda da lista.

Toda vez, que usarmos recursão em listas sempre utilizaremos a mesma técnica acima que consiste aplicar uma operação, da função definida, para um elemento da lista (geralmente o cabeça) e de acordo com as condições, aplicar a mesma definição da função para o restante da lista.

Imagine uma função que calcula o número de elementos em uma lista.
```
conta (xs)
 | null (xs) = 0
 | otherwise = 1 + conta (tail xs)
```
Observe que aqui incrementamos a função de **1** toda vez que a função é chamada por ela mesma.

#### As três regras da Recursão
```
Temos informalmente algumas regras para a recursão :

1) saber quando parar.

2) decidir como fazer a próxima ação.

3) quebrar uma jornada recursiva em um passo mais uma jornada recursiva menor.
```

A primeira regra avisa que qualquer função recursiva precisa ser verificada se sua jornada chegou ao fim antes de partir para outra jornada recursiva. Na função **qqimpar** a primeira clausula verifica se o parametro é uma lista vazia, e então encerra a função e retorna **False** desde que não haja mais elementos na lista.

A segunda regra sugere que quebremos o problema em peças menores que instantaneamente podem resolver o problema. Na função **qqimpar** verificamos se o primeiro elemento da lista é um número **ímpar**, retornando então True.

A terceira regra diz que podemos achar uma maneira para a função chamar ela mesma recursivamente em um problema ligeiramente menor que resulta da quebra do problema em pequenas peças. A função **qqimpar** chama ela mesma tendo como parametro a *cauda* da lista, uma lista menor que a original, para ver se há números ímpares na lista.

#### Usando Padrões
A declaração de uma função **f** usualmente pega a forma de um número de equações na forma:
```
f arg1 arg2 ... argn = corpo
```
Ou uma expressão equivalente, se **f** é escrita por um operador. Cada expressão **arg1, arg2,...,argn**, representa um argumento para a função **f** e é chamada de "padrão". O número desses argumentos na função **f** é chamado de "**aridade**" da função.

Quando a função é definida por mais de uma equação, é usualmente necessário avaliar um ou mais argumentos para a função para determinar onde a equação é aplicada. esse processo é chamado de "**casamento de padrões**". Podemos definir a maioria das funções usando padrões.

Há classes de problemas em que a linguagem das funções definidas para resolve-lo não está intimamente ligada a linguagem das definições matemáticas, por exemplo o fatorial:

```
fat 0 = 1

fat n = n * fat (n-1) para n > 0
```
A definição de função **fat** utilizando **guards**, resolve o problema, mas podemos também escrever a função usando **casamento de padrão** :
```
fat 0 = 1

fat n = n * fat (n-1)
```
Ou seja, a definição da função é comparada com o parametro de entrada, se "casar", a função é executada, senão vai para uma próxima definição da função e verifica o casamento de seus argumentos com o parametro de entrada.

