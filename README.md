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

**JUPYTER** - que é um ambiente de execução para a linguagem de programação **Python 3**. Esse ambiente possue várias caracterísiticas incorporadas do estilo de programação Funcional.

Uma propriedade característica da P.F. é que uma expressão possui um valor bem definido, não importando a *ordem* da avaliação pelo computador. O significado de uma expressão é o seu *valor*, e a tarefa do computador é encontrá-lo. Por exemplo o valor da expressão 6 * 7 é 42:
```
6*7
42
```
Os scripts são na verdade uma lista de definições de funções, feitas pelo programador.

Exemplos de definições de funções:
```
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
quadrado (3 + 4)
49

menor (3, 4)
3

quadrado ( menor (3, 4) )
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
 
area()    
        
144

menor ((area() + 4), 150)
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

Quadrado ( 3 + 4)	=> Quadrado 7	(+)
=> 7 * 7	(Quadrado)
=> 49	(*)

Quadrado ( 3 + 4)	=> (3 + 4) * (3 + 4)	(Quadrado)
=> 7 * (3 + 4)	(+)
=> 7 * 7	(+)
=> 49	(*)
Nestes exemplos os símbolos entre parênteses indica a operação que foi utilizada para fazer a redução (ou a transformação). 

Quando uma expressão não pode mais ser reduzida então ela é impressa.

No primeiro exemplo a ordem de aplicação das reduções foram: (+), (Quadrado), (*). 

No segundo exemplo a ordem foi : (Quadrado), (+), (+), (*). Assim a primeira opção gastou um número menor de reduções que a segunda. 

É importante fazer a distinção entre um valor e sua representação através de expressões.  A forma equivalente mais simples não é o valor,  mas, a sua representação.

Existem muitas representações de um mesmo valor, por exemplo o valor: "quarenta e nove", pode  ter as seguintes representações:

decimal =
49
romano =
XLIX
Expressão =
7 * 7
binário 16 bits =
0000000000110001
Uma expressão está na forma canônica ou forma normal se ela não pode mais ser reduzida.

Alguns valores não possuem representação canônica e outros não possuem representação finita. Ex. O número PI não possui representação decimal finita.

Algumas expressões não podem ser reduzidas porque elas não denotam valores bem definidos no sentido matemático. 

                    Ex. Uma divisão de um número qualquer por zero, 1/0. 

Uma tentativa de avaliar esta expressão pode ocasionar um erro ou cair numa seqüência tão longa sem produzir resultados.

Para manter a condição de que toda expressão deve denotar um valor, é conveniente introduzir um símbolo para representar o valor indefinido: "NIL"