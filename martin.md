#### Martin e o Dragão

A muito tempo atrás, antes dos computadores serem inventados, os alquimistas estudavam as propriedades místicas dos números. À falta de computadores, eles tinham que confiar aos dragões os trabalhos que deveriam ser feitos por eles próprios. Os dragões eram animais inteligentes, mas ao mesmo tempo preguiçosos e mau-humorados. Um dos piores poderia, algumas vezes, queimar o seu dono com um simples arroto abrasador. Mais a maioria dos dragões não eram cooperativos, devido ao fato da violência exigir muita energia. Esta é a história de como Martin, um aprendiz de alquimista, descobriu a recursão ludibriando um dragão preguiçoso. 

Um dia o alquimista deu a Martin uma lista de números e mandou-o ao calabouço para perguntar ao dragão se algum número da lista era ímpar. Martin nunca tinha estado no calabouço antes. Ele levou uma vela, e mais adiante, no canto mais escuro, encontrou o velho dragão, cuja aparência não era muito amigável. Timidamente, ele se manteve afastado. Ele não queria ser queimado com uma chama do dragão. 

" O que você quer ? ," resmungou o dragão enquanto olhava desconfiado para Martin. 

"Por favor, dragão, eu tenho uma lista de números e preciso saber se alguns deles são ímpares." Martin começou. "Aqui está," ele escreveu a lista na poeira com seu dedo : 

( 3142 5798 6550 8914 ) 

O dragão estava de mau humor naquele dia. Se tratando de um dragão, era sempre assim. "Desculpe, garoto," disse o dragão. "Eu estou disposto a lhe dizer se o primeiro número da lista é ímpar, é o melhor que posso fazer. Qualquer coisa, além disto, seria muito complicado; provavelmente não valeria o meu esforço". 

" Mas eu preciso saber se algum número da lista é ímpar, não apenas o primeiro número," explicou Martin. 

" Isto é muito ruim para você !, " disse o dragão. "Eu só irei verificar o primeiro número da lista. Mas eu verificarei em todas as listas que você quiser, se você entregá-las a mim alguma hora." 

Martin pensou por um momento. Deve haver alguma coisa por traz do que o dragão disse. "O que você pode dizer sobre esta primeira lista, então ?," ele perguntou apontando para a primeira lista que desenhou na poeira : 

( 3142 5798 6550 8914 ) 

"O primeiro número da lista não é ímpar," disse o dragão. 

Então, Martin cobriu o primeiro número da lista com a sua mão e desenhou um novo parêntesis a esquerda, deixando a seguinte lista: 

( 5798 6550 8914 ) 

e disse " E esta lista ? " 

"O primeiro número desta lista não é ímpar," o dragão respondeu. 

Martin cobriu um pouco mais da lista. "E esta lista , então ? " 

( 6550 8914 ) 

" O primeiro número desta lista também não é ímpar," disse o dragão. Ele pareceu aborrecido, mas pelo menos ele está cooperando. 

" E esta aqui ?, " perguntou Martin. 

( 8914 ) 

" Não é ímpar. " 

" E esta aqui? " 

( ) 

" Isto é uma lista vazia !, " o dragão bufou. "Não pode haver um número ímpar lá, pois não existe nada lá ." 

" Bem," disse Martin, "Eu sei que nenhum dos números da lista que o alquimista me deu é ímpar. Todos são pares. " 

" Eu nunca disse isto !!!, " bramou o dragão. Martin cheirou a fumaça. " Eu somente falei sobre o primeiro número de cada lista que você me mostrou. " 

" Isto é verdade, dragão. Eu poderia escrever todas as listas que você viu? " 

" Se você quer, " o dragão respondeu. Martin, então, escreveu na sujeira : 

( 3142 5798 6550 8914 ) 

( 5798 6550 8914 ) 

( 6550 8914 ) 

( 8914 ) 

( ) 

" Você não vê ?, " Martin perguntou. "Dizendo-me que o primeiro elemento de cada uma destas listas não é ímpar, você me disse que nenhum dos elementos da minha lista original era ímpar ." 

" Isto é bastante complicado, " disse o dragão testando. "Parece-me que você descobriu a recursão. Mas não me pergunte o que isto significa, você mesmo tem que descobrir." 

E com isto ele fechou os seus olhos e recusou-se a proferir qualquer outra palavra.

#### Martin Visita o Dragão Novamente
" Oi , dragão ! "

" Hmmmmmph ! Você de novo."

" Eu preciso descobrir qual é o fatorial de cinco, " disse Martin. " O que significa fatorial ? "

Aborrecido o dragão disse, "Eu não irei lhe dizer. Procure em algum livro. "

"Tudo bem," disse Martin. " Diga-me somente qual é o fatorial de cinco e lhe deixarei sozinho. "

" Você não sabe o que significa fatorial, mas você quer que eu lhe diga qual é o fatorial de cinco ???  Tudo bem, eu lhe direi. O fatorial de cinco é cinco vezes o fatorial de quatro. 

Eu espero que você esteja satisfeito. Não se esqueça de trancar a porta quando você sair."

" Mas qual é o fatorial de quatro ? " perguntou Martin.

" Fatorial de quatro ? Porque ? é quatro vezes o fatorial de três, é claro. "

" E eu suponho que irá dizer-me que o fatorial de três é três vezes o fatorial de dois, " disse Martin.

" Que garoto inteligente você é ! " disse o dragão. " Agora vá!"

" Ainda não, " Martin respondeu. " O fatorial de dois é dois vezes o fatorial de um. O fatorial de um é um vezes o fatorial de zero. E agora ? "

" Fatorial de zero é um, " disse o dragão. " Isto é realmente tudo que você sempre precisará para lembrar-se sobre fatoriais. "

"Hmmm, "disse Martin. "Existe um padrão para esta função fatorial. Talvez eu deva escrever os passos que tenho seguido. " 

Aqui está o que ele escreveu :

Fatorial (5) = 5 x Fatorial (4)

= 5 x 4 x Fatorial ( 3 )

= 5 x 4 x 3 x Fatorial ( 2 )

= 5 x 4 x 3 x 2 x Fatorial ( 1 )

= 5 x 4 x 3 x 2 x 1 x Fatorial ( 0 )

= 5 x 4 x 3 x 2 x 1 x 1

"Bem, " disse o dragão, "você tem usado recursão até chegar ao fatorial de zero que é um. Agora, porque você não tenta trabalhar sua maneira de voltar ao ... ops! "

Quando ele percebeu o que estava fazendo, o dragão parou no meio da fala. Dragões não são prestativos.

Martin começou a escrever novamente :

1 x 1 = 1

2 x 1 x 1= 2

3 x 2 x 1 x 1 = 6

4 x 3 x 2 x 1 x 1 = 24

5 x 4 x 3 x 2 x 1 x 1 = 120

" Hey ! " Martin gritou. " Fatorial de 5 é 120. Esta é a resposta ! Obrigado !! "

" Eu não lhe disse a resposta, " disse o dragão. "Eu lhe disse somente que o fatorial de zero é um, e que o fatorial de n é n vezes o fatorial de n - 1. Você mesmo fez o resto, recursivamente, eu devo complementar. "

" Isto é verdade," disse Martin. " Agora sei o que RECURSIVAMENTE realmente significa. "

As palavras do dragão deram uma definição muito precisa do Fatorial de n :

o fatorial de n é n vezes o fatorial de n - 1, e o fatorial de zero é um.

Sabendo disso construa uma função chamada FAT que computa fatoriais recursivamente!

#### O Sonho do Dragão
Um dia, quando Martin retornou ao calabouço, ele achou o dragão esfregando seus olhos, como se ele tivesse acordado de um longo sono.

" Eu tive um sonho muito curioso, " disse o dragão. "Era um sonho recursivo de fato. Você gostaria de ouvi-lo ? "

Martin estava aturdido, procurando encontrar algo no dragão que justificasse o seu bom humor. Ele esqueceu tudo a respeito do último problema que o alquimista lhe deu. "Sim, por favor conte-me a respeito do seu sonho, "disse ele.

" Muito bem, " começou o dragão. " na noite passada eu estava olhando para um grande pão de forma, e eu imaginei em quantos fatias eu poderia dividir deste pão de forma. Para responder à minha pergunta eu cortei uma fatia do pão de forma. Eu tinha, agora, uma fatia e um pedaço de pão de forma insignificante menor, mas nenhuma resposta. Eu tentei entender o problema até adormecer ".

" E foi isto que aconteceu quando você teve este sonho ? " Martin perguntou.

" Sim, um sonho muito curioso. Eu sonhei com um outro dragão que tinha um pedaço de pão de forma como eu também tinha, exceto que o dele era menor que o meu. E ele também queria saber quantos pedaços seu pão de forma poderia ter, mas ele teve o mesmo problema que eu. Ele cortou uma fatia, como eu, e ficou com o resto do pão, como eu, e então adormeceu como eu adormeci também. "

" Então nenhum de vocês encontrou a resposta," Martin disse desapontado. " Você não sabe qual é o tamanho do seu pão de forma, e você não sabe qual é o tamanho do pão de forma do outro dragão, exceto que é uma fatia menor que o seu. "

" Mas eu ainda não terminei, " disse o dragão. "Quando o dragão do meu sonho adormeceu, ele teve um sonho. Ele sonhou sobre - se você pode imaginar isto - um dragão cujo pão de forma era uma fatia menor que o seu próprio pão. E este dragão também queria saber quantas fatias seu pão de forma poderia ter, e ele tentou achar a resposta cortando uma fatia, mas isto não deu a resposta, então ele adormeceu pensando nisto. "

" Sonhos dentro de sonhos !! " exclamou Martin. "Você está fazendo minha cabeça nadar. O último dragão também teve um sonho ? "

" Sim, e ele não foi o último. Cada dragão sonhou com um dragão que possuia um pão de forma uma fatia menor que o seu. Eu estava empilhando uma bela e profunda pilha de sonhos. "

" Como você fez para acordar ? " perguntou Martin.

" Bem ," disse o dragão, " eventualmente um dos dragões sonhou com um dragão cujo pão de forma era tão pequeno que não estava mais lá em si. Você deve chamar isto de 'o pão de forma vazio' . O dragão pôde ver seu pão de forma contendo nenhuma fatia, então ele soube que a resposta para a sua questão era zero; ele não adormeceu."

" Quando o dragão, que sonhou com o dragão que não adormeceu, finalmente acordou, ele soube que, desde que o seu pão de forma tinha uma fatia maior, ele só poderia ser dividido em um pedaço. Então ele acordou sabendo a resposta da sua pergunta. "

" E , quando o dragão que sonhou com o dragão que acordou, também acordou ele soube que seu pão de forma poderia ser dividido em duas fatias, desde que ele tinha uma fatia a mais que o dragão do seu sonho. E quando o dragão que sonhou com este acordar ... "

" Eu entendo ! " disse Martin. " Ele adicionará um a quantidade de fatias do pão de forma do dragão com o qual ele sonhou, e isto responderá a sua própria pergunta. E quando você finalmente acorda, você tem a resposta sobre quantas fatias o seu pão poderá ser dividido. Quantas fatias o seu pão de forma pode ter ? "

" Vinte e sete, " disse o dragão. "Foi um sonho muito longo. "

Para verificar se o processo de descoberta da quantidade de pedaços de pão é verdadeiro, construa uma função recursiva para contar pedaços de pão

#### As Três Regras da Recursão
O dragão, fingindo repugnância pelas perguntas de Martin, na realidade divertiu-se ensinando-o sobre recursão. Um dia ele decidiu explicar formalmente o significado de recursão. 

O dragão disse a Martin para abordar todo problema recursivo como se eles fossem uma jornada. 

Se ele seguisse três regras para a resolução de problemas recursivamente, ele sempre iria completar a jornada com sucesso. 

O dragão explicou as regras desta maneira :

Saber quando parar.
Decidir como aplicar o primeiro passo.
Analisar a jornada de forma que a mesma posa ser dividida em jornadas menores.
A primeira regra, " saber quando parar " , adverte-nos que qualquer função recursiva deve fazer uma checagem para verificar se a jornada foi completada antes da nova chamada recursiva.

A segunda regra, " decidir como fazer o primeiro passo " , nos diz como quebrar um problemas em subproblemas que possam ser resolvidos instantaneamente.

A terceira regra, " analisar a jornada de forma que a mesma posa ser dividida em jornadas menores ", significa achar uma maneira da função chamar a si mesma recursivamente e cujo parâmetro é um problema menor resultante da segunda regra.

#### Padrões de Recursão usando HASKELL
Recursão de Cauda com Teste Duplo.

O teste duplo indica que a função possui duas condições de parada. Caso uma das condições seja satisfeita então um valor é retornado.

Caso os testes falhem então a função executa uma redução na sua entrada e chama a si mesma.

Esta recursão é chamada Recursão de Cauda porque a função não faz bada após a chamada recursiva.

Template:

Função X | Teste-Final-1 = Valor-Final-1

| Teste-Final-2 = Valor-Final-2

| otherwise = Função Redução-X

Exemplo:

Função: AnyOddP

Teste-Final-1: X==[ ]

Valor-Final-1: False

Teste-Final-2: OddP(Head X)

Valor-Final-2: True

Redução-X : Tail X

 

Recursão de Cauda com Teste Simples.

Template:

Função X | Teste-Final = Valor-Final

| otherwise = Função Redução-X

Exemplo:

Função: Find-First-Atom

Teste-Final: AtomP X

Valor-Final: X

Redução-X : Head X

Usamos RCTS quando sabemos que iremos encontrar o que procuramos.

Usamos RCTD quando existe a possibilidade de não encontrarmos o que procuramos.

 

Recursão com Incremento.

Ao invés de dividir o problema num passo mais uma pequena jornada, dividimos o problema numa pequena jornada mais um passo final.

O passo final consiste em escolher uma função de incremento que será aplicada ao resultado da chamada recursiva.

Template:

Função X | Teste-Final = Valor-Final

| Função-Incremento Valor-Incremento Função Redução-X

Exemplo:

Função: Conta-Pedaços

Teste-Final: X == [ ]

Valor-Final: 0

Função-Incremento: +

Valor-Incremento: 1

Redução-X : Tail X

Recursão com Construção de Listas.

É um caso especial de recursão com incremento, onde a função de incremento é " : " em GOFER. Com o retorno de cada chamada recursiva nós criamos uma nova lista, assim a profundidade da recursão é igual ao tamanho da lista criada mais um, por que a última chamada retorna vazio.

Template:

Função X | Teste-Final = [ ]

| Novo-Elemento : Função Redução-X

Exemplo:

Função: Riso

Teste-Final: X == 0

Valor-Final: [ ]

Novo-Elemento: ´HA´

Redução-X : X-1

Recursão simultânea em mais de uma variável.

É uma extensão de qualquer padrão anterior. Ao invés de Ter uma única entrada, a função pode Ter várias, e destas uma ou mais pode ser reduzida por alguma função.

Template:

Função N X | Teste-Final = Valor-Final

| Otherwise : Função Redução-N Redução-X

Exemplo:

Função: Enésimo

Teste-Final: N==0

Valor-Final: First X ou Head X

Redução-N : N-1

Redução-X : Tail X

 

#### Avaliação Gulosa versus Avaliação Preguiçosa
Na avaliação gulosa , os argumentos para a função são sempre avaliados antes de serem chamados. Como resultado, a avaliação de uma expressão pode não terminar apropriadamente, por causa de erros de execução ou repetições infinitas.

Na avaliação preguiçosa, os argumentos para a função não são avaliados até esses valores serem requisitados e nenhuma expressão partilhada é avaliada mais que uma vez. Se a expressão é sempre avaliada então o resultado é partilhado em todos os lugares em que ela é utilizada.

A avaliação preguiçosa é uma característica importante das linguagens de programação funcional. Isso traz muitas vantagens , inclusive a habilidade de representar potencialmente estruturas de dados infinitas como o conjunto dos números inteiros.

