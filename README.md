## Programação Funcional

### Programação Funcional com Python
Como o nome sugere, a essência da Programação Funcional (PF) como método de programação é a construção de funções. A utilização da palavra "função" é mais no sentido matemático do que no sentido utilizado nas linguagens de programação convencionais. Na matemática, uma função é um objeto que fornece uma lista de todas as variáveis para as quais ele varia, juntamente com uma fórmula para indicar o valor correspondente. Assim, por exemplo, se escrevermos: y = x^2 dizemos que y é função de x pois, quando x varia, y também varia como seu quadrado.

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


You can use the [editor on GitHub](https://github.com/ruiterbc/ruiterbc.github.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ruiterbc/ruiterbc.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
