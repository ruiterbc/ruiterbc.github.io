## Programação Funcional

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
### Expressões e Valores
**Expressão** é uma noção fundamental em P.F. Existem muitos tipos de expressões e nem todas podem ser descritas neste formalismo, mas todas possuem características comuns.

A característica mais importante da notação matemática é que uma **expressão** é usada somente para descrever (ou denotar) um **valor**.

O significado de uma expressão é o seu valor e mais nada. O valor de uma expressão depende somente dos valores dos seus constituintes e, essas subexpressões, podem ser substituídas pelos seus valores.

Uma expressão pode conter **"nomes"** para quantidades desconhecidas, embora seja comum na matemática entendermos que diferentes ocorrências do mesmo nome se refere ao mesmo valor, embora desconhecido.

Estes nomes são chamados **"variáveis"**, mas estas variáveis não variam como nas linguagens de programação, pois elas sempre denotam o mesmo valor. A esta propriedade chamamos de **Transparência Referencial**.

Entre os tipos de valores que uma variável pode denotar encontram-se: números, valores-verdade, caracteres, tuplas, funções e listas.

### Redução
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

### Tipos
Na notação que iremos seguir, o universo de valores é particionado em coleções organizadas chamadas tipos. 
Os tipos podem ser:
- **Básicos, cujos valores são chamados de primitivos. Os números (num), os valores booleanos (bool) e os caracteres (char).**
- **Derivados, cujos valores são construídos de outros tipos. O tipo par ou tupla (tipo 1, tipo 2 ), onde "tipo 1" e "tipo 2" são os tipos que formam o par; ou a o tipo lista, cujo definição é : [ tipo ], que pode ser uma sequência de qualquer tipo definido.**

Uma operação é efetuada na forma tradicional:
```
<operando>  <operador> <operando>
1 + 1
2 * 3
5 div 6
```
Uma expressão bem formada possui o seu tipo deduzido a partir dos tipos dos seus constituintes. A este princípio chamamos **"Tipagem Forte"**. 

A maior conseqüência da disciplina imposta pelo conceito de tipagem forte é que uma expressão que não possa ter o seu tipo identificada não é bem formada e será rejeitada antes de ser avaliada.

Ex:
```
Script 03.a

def ay x = ´A´           
```
Para qualquer x, a resposta será sempre 'A', sendo o tipo inferido CHAR.
```
Script 03.b

def bee x = x + ay x   
```
Ao identificado o tipo da função bee, há uma tentativa de somar o resultado de ay, ocorrendo um erro de tipo. 

Existem dois estágios de avaliação para uma expressão : análise sintática e análise de tipo.

### Funções e Definições

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
Script 04

def dobro1  x = x + x
def dobro2  x = 2 * x
```
Apesar dos procedimentos diferentes para obter a correspondência entre o argumento e o resultado, as funções **dobro1** e **dobro2** denotam a mesma função e podemos afirmar que, dobro1 = dobro2 é matematicamente verdade.

Dependendo do procedimento escolhido uma definição pode ser mais ou menos eficiente, no sentido de que uma redução pode ser mais rápida que a outra.

### Números Inteiros

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
((3 + 5) * 6) / (9 ^ 2) e assim por diante.
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