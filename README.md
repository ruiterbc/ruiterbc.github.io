## Programação Funcional

#### Indice

1. [Expressões e Valores](#Expressoes)
2. [Redução](#Reducao)
3. [Tipos](#Tipos)
4. [Funções e Definições](#FunDef)
5. [Numeros Inteiros](#NumInt)
6. [Definição de Funções Simples](#FunSimpl)
7. [Números Reais]("NumReal)
8. [Valores Relacionais e Lógicos](#ValReLog)

### Programação Funcional com Python
Como o nome sugere, a essência da **Programação Funcional (PF)** como método de programação é a construção de funções. A utilização da palavra "função" é mais no sentido matemático do que no sentido utilizado nas linguagens de programação convencionais. Na matemática, uma função é um objeto que fornece uma lista de todas as variáveis para as quais ele varia, juntamente com uma fórmula para indicar o valor correspondente. Assim, por exemplo, se escrevermos: y = x^2 dizemos que y é função de x pois, quando x varia, y também varia como seu quadrado.

A Programação Funcional envolve notação e conceitos de classes ou conjuntos que soam familiares a qualquer pessoa com pequena experiência matemática. O principal papel do programador é construir uma função para resolver um determinado problema. Essa função, que pode envolver outras funções, é expressa numa notação que obedece aos princípios matemáticos.

As funções definidas pelo programador são chamadas de **scripts**.

O papel do computador é agir como um avaliador ou executor de expressões e impressor dos resultados.

A expressão representa um valor a ser obtido, cuja tarefa o computador é capaz de realizar.

A forma básica de interação entre o programador e o computador é:
```
Lê -> Calcula -> Exibe
```
A seqüência de interação entre o programador e o computador é chamada de **seção**.

O ambiente de interação utilizado neste curso será o ambiente:
```
**Codebench** - que é um ambiente de aprendizagem para a linguagem de programação **Python 3**. 
Esse ambiente possue várias caracterísiticas incorporadas do estilo de programação Funcional.
```
Uma propriedade característica da P.F. é que uma expressão possui um valor bem definido, não importando a **ordem** da avaliação pelo computador. O significado de uma expressão é o seu **valor**, e a tarefa do computador é encontrá-lo. Por exemplo o valor da expressão 6 * 7 é 42: (obs. A entrada do usuário será apresentada pelo sinal ">")
```
> 6*7
42
```
Os scripts são na verdade uma lista de definições de funções, feitas pelo programador.

Exemplos de definições de funções:
```
Script 01:

def quadrado(n):
    return n*n

def menor (n,m):
    if (n <= m): 
        return n 
    else: 
        return m
```

O propósito de uma definição é fazer uma associação entre um nome e um valor.

Um conjunto de ligações é chamado de contexto ou ambiente. Um exemplo de uma seção:
```
> quadrado (3 + 4)
49

> menor (3, 4)
3

> quadrado ( menor (3, 4) )
9
```
O avaliador pode utilizar as ligações para fazer simplificações. Algumas expressões podem ser avaliadas sem que seja indicado o contexto: 3 + 4.

Isto só é possível porque algumas operações são consideradas primitivas e fazem parte do avaliador: Operações Aritméticas (+, *, -, /, etc.) e Fornecimento de Operações Pré-definidas (mod, div, even, odd, etc.).

Os scripts podem ser modificados a qualquer momento, submetidos ao avaliador e um novo contexto será iniciado.

Podemos anexar ao script 01, definido anteriormente as novas definições:
```
Script 02:

def lado(): 
    return 12

def area():
    return quadrado (lado())
 
> area()           
144

> menor ((area() + 4), 150)
148

```
### [Expressões e Valores]()<a name="Expressoes"></a>
**Expressão** é uma noção fundamental em P.F. Existem muitos tipos de expressões e nem todas podem ser descritas neste formalismo, mas todas possuem características comuns.

A característica mais importante da notação matemática é que uma **expressão** é usada somente para descrever (ou denotar) um **valor**.

O significado de uma expressão é o seu valor e mais nada. O valor de uma expressão depende somente dos valores dos seus constituintes e, essas subexpressões, podem ser substituídas pelos seus valores.

Uma expressão pode conter **"nomes"** para quantidades desconhecidas, embora seja comum na matemática entendermos que diferentes ocorrências do mesmo nome se refere ao mesmo valor, embora desconhecido.

Estes nomes são chamados **"variáveis"**, mas estas variáveis não variam como nas linguagens de programação, pois elas sempre denotam o mesmo valor. A esta propriedade chamamos de **Transparência Referencial**.

Entre os tipos de valores que uma variável pode denotar encontram-se: números, valores-verdade, caracteres, tuplas, funções e listas.

### [Redução]()<a name="Reducao"></a>
O computador avaliar as expressões pela redução da expressão para a sua **"forma equivalente mais simples"** e imprime o resultado.
**Avaliação**, **Redução** ou **Simplificação** são intercambiáveis. Utilizaremos o símbolo **"=>"** para indicar **"reduzido a"**.

Como exemplo vamos mostrar as possíveis reduções para a expressão: Quadrado ( 3 + 4), onde a definição de Quadrado x => x * x
Redução 01:
```
Quadrado ( 3 + 4)   => Quadrado 7   (+)
                    => 7 * 7        (Quadrado)
                    => 49           (*)
```
Redução 02:
```
Quadrado ( 3 + 4)   => (3 + 4) * (3 + 4)    (Quadrado)
                    => 7 * (3 + 4)          (+)
                    => 7 * 7                (+)
                    => 49                   (*)
```
Nestes exemplos os símbolos entre parênteses indica a operação que foi utilizada para fazer a redução (ou a transformação). Quando uma expressão não pode mais ser reduzida então ela é impressa.
No primeiro exemplo a ordem de aplicação das reduções foram: (+), (Quadrado), (\*). 
No segundo exemplo a ordem foi : (Quadrado), (+), (+), (\*). Assim a primeira opção gastou um número menor de reduções que a segunda. 
É importante fazer a distinção entre um valor e sua representação através de expressões.  A forma equivalente mais simples não é o valor,  mas, a sua representação.
Existem muitas representações de um mesmo valor, por exemplo o valor: "quarenta e nove", pode  ter as seguintes representações:

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
Uma tentativa de avaliar esta expressão pode ocasionar um erro ou cair numa seqüência tão longa sem produzir resultados.
Para manter a condição de que toda expressão deve denotar um valor, é conveniente introduzir um símbolo para representar o valor indefinido: **"NIL"**

### [Tipos]()<a name="Tipos"></a>
Na notação que iremos seguir, o universo de valores é particionado em coleções organizadas chamadas tipos. 
Os tipos podem ser:
- **Básicos**, cujos valores são chamados de primitivos. Os números (num), os valores booleanos (bool) e os caracteres (char).
- **Derivados**, cujos valores são construídos de outros tipos. O tipo par ou tupla (tipo 1, tipo 2 ), onde "tipo 1" e "tipo 2" são os tipos que formam o par; ou a o tipo lista, cujo definição é : [ tipo ], que pode ser uma sequência de qualquer tipo definido.

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
Script 03-a:

def ay x = ´A´           
```
Para qualquer x, a resposta será sempre 'A', sendo o tipo inferido CHAR.
```
Script 03-b:

def bee x = x + ay x   
```
Ao identificado o tipo da função bee, há uma tentativa de somar o resultado de ay, ocorrendo um erro de tipo. 

Existem dois estágios de avaliação para uma expressão : análise sintática e análise de tipo.

### [Funções e Definições]()<a name="FunDef"></a>

Uma **função** é uma regra de correspondência que associa cada elemento de um tipo A com um único elemento de um segundo tipo B. O tipo A é chamado tipo **fonte** e o tipo B de tipo **alvo**.
```
f :: A -> B
```
O tipo de f é A->B , caso A e B tenham tipo. A função f toma argumentos em A e retorna resultados em B. Se *x* é um elemento de A, *f(x)* ou *f x* denota a aplicação de f para x.

O valor resultante da aplicação da função é o **único elemento** em B associado com x pela aplicação da regra de correspondência f.

É importante separa a função da sua aplicação para um argumento. Em alguns textos matemáticos encontramos "a função f(x)" , quando o correto seria dizer a "função f" .Em tais textos função raramente são consideradas como argumentos para outras funções.

Em Programação Funcional, funções são **valores como outro qualquer**, e podem ser passados como **argumentos para outras funções**.

É importante manter em mente a distinção entre um valor da função e uma particular definição dela. Existem muitas definições possíveis para a mesma função:
```
Script 04:

def dobro1  x = x + x

def dobro2  x = 2 * x
```
Apesar dos procedimentos diferentes para obter a correspondência entre o argumento e o resultado, as funções **dobro1** e **dobro2** denotam a mesma função e podemos afirmar que, dobro1 = dobro2 é matematicamente verdade.

Dependendo do procedimento escolhido uma definição pode ser mais ou menos eficiente, no sentido de que uma redução pode ser mais rápida que a outra.

### [Números Inteiros]()<a name="NumInt"></a>

Em Programação Funcional, há dois tipos básicos de números: os números inteiros e os números reais. Os inteiros, são denominados **Int** .

#### Operadores
Os Operadores Aritméticos são os símbolos que representam certas transformações entre um número ou um grupo deles. 

Os símbolos dos operadores aritméticos utilizados na programação funcional para inteiros, são os mesmos utilizados na matemática. 

Abaixo é apresentada uma tabela com os principais operadores para inteiros e suas respectivas denominações:

|operador | denominação|
|----|----------|
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
As Expressões Aritméticas podem ser aplicadas como uma série de operações aritméticas, efetuadas para gerar um valor. 

Quando várias operações aparecem juntas na expressão, certas regras de precedência são providenciadas para resolver possíveis ambiguidades. 

A precedência das regras para operadores aritméticos, segue a seguinte ordem :

| operador | denominação|
|----------|------------|
| ^ | exponenciação |
|* , / , div , mod | operadores de multiplicação |
|+ , - | operadores de adição|

  

Quando os operadores surgem numa expressão com o mesmo nível de precedência, é aconselhável usar parenteses para evitar ambiguidades.

Na PF as expressões são escrita como na matemática elementar, ou seja:
```
((3 + 5) * 6) / (9 ^ 2)
```
Verifique a expressão acima sem os parenteses no ambiente de programação.


#### Intervalos
Os Intervalos podem ser vistos como uma série de números gerados a partir de uma definição matemática, ou seja, um conjunto de elementos enumerados.

Se quisermos os números inteiros de 1 a 10, basta escrevermos estes dois números entre colchetes e separados por dois pontos seguidos. Assim temos **[1..10]** indicando que queremos um conjunto de números inteiros. Os números gerados, podem ser vistos como uma lista de números inteiros.Os números 1 e 10 são chamados de **limitadores**. Podemos colocar quaisquer limitadores desde que sejam números inteiros.

A maneira de escrever intervalos é na forma **[a..b]**, onde a e b são números inteiros, indicando que haverá uma lista de números inteiros incrementados na ordem de a para b,aumentando de 1 em 1. 

Se *a > b*, então o resultado será uma lista sem números, ou seja, uma lista vazia.

Exemplos de intervalos em programação funcional :
```
>[1]
[1]

>[1..3]
[1,2,3]

>[1..9]
[1,2,3,4,5,6,7,8,9]

>[9..1]	
[]

>[1..]
[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,...]

Este exemplo é um intervalo infinito.
```
Uma outra maneira de escrever intervalos é na forma **[a,b..c]**, que indica uma progressão aritmética **a,a+d,a+2*d,...,** e assim por diante, onde **d = b - a**.

Teste outros exemplos no ambiente de programação.

#### Tuplas
As Tuplas são vistas como uma combinação de elementos com o objetivo de formar novos elementos, pelos pares de elementos formados.

Se quisermos ter dois números agrupados, formando um par, basta os colocar entre parenteses separados por virgula, ou seja, (1,2). 

Isto significa uma tupla, formada pelo par de números inteiros (Int,Int).

Como podemos observar as tuplas são definidas por elementos entre parenteses, com isso as tuplas podem possuir vários elementos, 

na forma **(x1,x2,...xn)** onde cada elemento pode ser uma expressão **x1,x2,...,xn** e possuindo os tipos **t1,t2,...,tn**, respectivamente. 

No exemplo acima, os tipos são inteiros.

Para formar os elementos da tupla podemos nos valer de expressões aritméticas como:
```
>(4+2,1) 
 (6,1) 

>([1..9], 3-2) 
([1,2,3,4,5,6,7,8,9],1)
```

### [Definição de Funções Simples]()<a name="FunSimpl"></a>
O ambiente da PF pode ser visto como uma calculadora bastante atraente que possui algumas funções e operadores embutidos. 

Porém, para resolver problemas mais sofisticados e que atenda a determinados requisitos, necessitamos definir novas funções para a resolução do problema. 

Essas funções seguem a definição matemática onde **f x -> y**.

Podemos definir uma função para somar dois números inteiros, escrevendo **soma x y = x + y**, onde x e y são parâmetros que recebem diferentes valores, para obter o resultado da função.

As linguagens possuem alguma funções pré-definidas como por exemplo, em Haskell a função **sum** que calcula o somatório e **product** que calcula o produtório. 

A sintaxe dessas funções é colocar a função na frente de um intervalo de números inteiros, ou seja, **sum [1..10]** gerando o valor 55.

Atributos Locais
As definições de funções podem incluir definições de valores com definição local. 

Nas descrições matemáticas frequentemente achamos expressões qualificadas pela palavra *"onde"* (where em inglês). 

Como exemplo observe a seguinte função :
```
              f(x,y) = (a+1) * (a+2),  onde a = (x+y)/2.
```

O mesmo dispositivo pode ser utilizado nas definições de atribuições locais para funções:
```
Script 05:

f x y    =  (a + 1) * (a + 2)
            where a = (x + y) / 2
```
A palavra **"where"** é usada para introduzir uma definição local. É importante notar que a palavra "where" é deslocada a direita para enfatizar seu uso como parte da expressão.

Cabe salientar que o uso de uma variável em PF, corresponde ao mesmo uso da notação matemática, ou seja, a notação matemática tem uma semântica estática, 

onde os nomes usados são definidos uma só vez, e seu valor depende somente do contexto da equação que os define.

#### Operadores e Funções
Os operadores e funções possuem diferenças, quanto ao seu posicionamento entre os parâmetros em PF. Os operadores sempre tratam com dois argumentos, ou seja, sua avaliação sempre requisitará somente dois elementos, sendo por este motivo também chamados de **operadores binários**.

A função, pode receber desde nenhum argumento, até um número conveniente para o problema a ser solucionado. Pode-se afirmar que a grande diferença entre operadores e funções, está na forma de escreve-los junto aos seus argumentos.

Quanto ao posicionamento entre os argumentos, os operadores são colocados entre os seus dois operandos e as funções são frequentemente colocadas antes dos seus parâmetros.

Para executar a adição entre dois números com o operador "+" temos, 2 + 2. Com a função definida como soma, temos soma 2 2.

### [Números Reais]()<a name="NumReal">
Os números reais são muitas vezes conhecidos por *fracionais* e também por *ponto flutuante*. Em PF são denominados pelo tipo **Float**.

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

É importante salientar que não é possível usar os operadores aritméticos com tipos diferentes, ou seja, não podemos somar 2 com 2.0. 

Experimente executar esta operação no ambiente de excução: 2 + 2.0

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

Na PF as expressões são escritas como na matemática elementar, ou seja, *((3.0 + 5.0) * 6.0) / (9.0 ^ 2)* e assim por diante. Teste a expressão acima sem os parenteses no ambiente de programação.


#### Intervalos
A definição de intervalos é a mesma de intervalos para números inteiros. Porém os limitadores e os elementos gerados, são números reais.

A maneira de escrever intervalos na forma [a..b], onde a e b são números reais, indicando que haverá uma lista de números reais incrementados na ordem de a para b, aumentando na mesma proporção do primeiro limitador até chegar no segundo limitador. Se a > b, então o resultado será uma lista sem números, uma lista vazia.

Teste os seguintes exemplos: 
```
>[1.1..3.1]

>[1.1..3.2]

>[1.1..9.3]

>[9.0..1.0]
```
A outra maneira de escrever intervalos na forma **[a,b..c]**, indica uma progressão aritmética **a,a+d,a+2*d,...,** e assim por diante, onde d = b - a.

Teste o seguinte exemplos: 
```
>[1.1,1.2..3.1]
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
Script 06:

def areacirc r =

                const * r ^ 2

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

### [Valores Relacionais e Lógicos]()<a name="ValReLog">
As palavras **verdadeiro** e **falso**, representam valores lógicos, significando se determinado valor de um determinado tipo (domínio), ao ser comparado a outro do mesmo tipo (domínio), é verdadeiro ou falso.

Esses valores são também chamados de **booleanos**, em homenagem ao matemático inglês Geoge Boole (1815-1864) que definiu uma álgebra a partir da lógica.

Nas linguegsn de programação os valores verdadeiro e falso, são representados pelo tipo Bool, e são escritos **True** para verdadeiro e **False** para falso. 

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
|A || B|A ou B|retorna True se A ou B tiver o valor True|
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
igualPi x =
        (x == const)
        where const = 3,14
```