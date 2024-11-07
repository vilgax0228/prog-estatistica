## Capítulo 1: Objetos e Classes

Uma função muito usada com objetos da classe *character* é a função **paste()**.

Ela recebe como argumento de entrada objetos do tipo character e retorna um *único* objeto, também do tipo character, que é definido pela *concatenação* dos objetos passados como entrada.

Quando chamamos o comando paste() podemos indicar como os objetos serão separados na concatenação usando o argumento de entrada *sep*. Se este argumento não for definido, ele será considerado como espaço.
```R
> paste("a", "b", "c")
[1] "a b c"
> paste("a", "b", "c", sep=",")
[1] "a,b,c"
> paste("a", "b", "c", sep="")
[1] "abc"
```

Operadores lógicos & (e) e | (ou):
```R
> A <- TRUE
> B <- FALSE
> A&B
[1] FALSE
> A|B
[1] TRUE
```
Também podemos realizar a negação desses objetos usando o comando !.
```R
> negA <- !A
> negA
[1] FALSE
```
Se quisermos testar se dois objetos são iguais ou diferentes, podemos usar os operadores == ou !=.
```R
> a <- 1
> b <- 1
> c <- 2
> d <- "2"
> a==b
[1] TRUE
> a!=c
[1] TRUE
> a==d
[1] FALSE
> c==d
[1] TRUE
```
Repare que no último comando ele respondeu "TRUE" , mesmo os objetos sendo de classes diferentes.

O programa provavelmente converte todos para a mesma classe (por coerção) antes de testar se são iguais.

É possível também testar se um objeto é maior(**>**) ou menor(**<**) que e maior ou igual(**>=**) e menor ou igual(**<=**) que.
```R
> a <- 1
> b <- 1
> c <- 2
> a>b
[1] FALSE
> b<=c
[1] TRUE
```
Podemos ainda usar os operadores (**+, -, *, /**) entre objetos do tipo *logical*.

Nesse caso, os objetos iguais a TRUE serão interpretados como o número 1 e os iguais a FALSE como 0.
```R
> V_1 <- TRUE; V_2 <- TRUE
> F_1 <- FALSE; F_2 <- FALSE
> V_1 + V_2
[1] 2
> V_1 - V_2
[1] 0
> F_1 * V_2
[1] 0
> F_1 / V_2
[1] 0
> V_1 / F_1
[1] Inf
> F_1 / F_2
[1] NaN
```

*Outras operações mais complexas:*
```R
> a <- 4
> b <- 12
> sqrt(a)  # square root
[1] 2
> sqrt(b)
[1] 3.464102
> exp(1)   # e^1
[1] 2.718282
> log(1)   # by default natural log
[1] 0
> abs(-b)  # absolute value
[1] 12
```

### Vetores

No R um *vetor* é uma *estrutura de dados* que armazena uma coleção de objetos em que todos são de uma mesma classe.

A maneira mais simples de se criar um vetor é usando a função **c()**, que combina objetos formando um vetor.
```R
> a <- c(1, 2, 3)
> a
[1] 1 2 3
> b <- c("a", "b")
> b
[1] "a" "b"
> c <- c(T, T, F, F)
> c
[1]  TRUE  TRUE FALSE FALSE
```
O R trata qualquer objeto como um vetor.

A função **length()** retorna o tamanho de um vetor.
```R
> length(a)
[1] 3
> length(b)
[1] 2
> length(c)
[1] 4
```
Para acessarmos a posição (*index*) de um vetor usamos os colchetes [].
```R
> a[1]
[1] 1
> b[2]
[1] "b"
> c[3]
[1] FALSE
```
Se tentamos acessar uma posição que não tenha sido definida, a resposta será NA (*not available*).
```R
> a[5]
[1] NA
```
Existem outras maneiras de se criar um vetor.  
Uma delas é usando o colchetes [] para alocarmos uma posição específica.
```R
> d <- 1
> d
[1] 1
> d[2] <- 3
> d[4] <- 5
> d
[1] 1 3 NA 5
> d[4] <- 7
> d[3] <- 5
> d
[1] 1 3 5 7
```
No exemplo anterior o objeto *d* foi iniciado como um vetor de tamanho 1 da classe *numeric*.

Temos também a possibilidade de iniciar um objeto como vazio ou nulo.
```R
> e <- NULL
> e
NULL
> e[2] <- 4
> e
[1] NA 4
> e[1] <- 2
> e
[1] 2 4
```

A função c() serve não só para concatenar objetos em um vetor, como também para concatenar um vetor com um novo objeto ou concatenar dois objetos, cada um já construído como um vetor.
```R
> a <- c(1, 2, 3)
> a
[1] 1 2 3
> c(a, 4)  # colocando um elemento no final do vetor
[1] 1 2 3 4
> c(0, a)  # colocando um elemento no início do vetor
[1] 0 1 2 3
> c(0, a, 4)
[1] 0 1 2 3 4

> e <- c(2, 4)
> e
[1] 2 4
> c(a, e)  # concatenando dois vetores
[1] 1 2 3 2 4

> b <- c("a", "b")
> b
[1] "a" "b"
> c(a, b)  # concatenando dois vetores de classes diferentes, uma delas é transformada por coerção
[1] "1" "2" "3" "a" "b"
```
**obs:** aqui nesse caso, é mais fácil de se transformar números em strings que strings de texto em números.

Temos ainda outras maneiras de criar um vetor:
```R
> 1:10
[1]  1  2  3  4  5  6  7  8  9 10
> seq(1, 20, by=2)
[1]  1  3  5  7  9 11 13 15 17 19
> rep(0, times=2)
[1] 0 0
```

Uma última maneira de se iniciar um vetor quando já se sabe o tipo, mas ainda não sabemos os elementos:
```R
> v1 <- numeric(2)
> v1
[1] 0 0
> v2 <- character(5)
> v2
[1] "" "" "" "" ""
> v3 <- logical(4)
> v3
[1] FALSE FALSE FALSE FALSE
```

É possível usar os operadores e funções das classes em um vetor de tamanho maior que 1.

Os operadores e funções são aplicados a cada posição do vetor e retornam um vetor como resposta.
```R
> a <- seq(1:10)
> b <- rep(2, 10)
> a
[1]  1  2  3  4  5  6  7  8  9 10
> b
[1] 2 2 2 2 2 2 2 2 2 2
> a+b
[1]  3  4  5  6  7  8  9 10 11 12
> a-b
[1] -1  0  1  2  3  4  5  6  7  8
> a*b
[1]  2  4  6  8 10 12 14 16 18 20
> a/b
[1] 0.5 1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0
> exp(a)
[1]     2.718282     7.389056    20.085537
[4]    54.598150   148.413159   403.428793
[7]  1096.633158  2980.957987  8103.083928
[10] 22026.465795
```
Outros exemplos:
```R
> a <- c("a", "aa", "aaa")
> b <- c("b", "bb", "bbb")
> paste(a, b)
[1] "a b"     "aa bb"   "aaa bbb"
> a1 <- c("a", "a", "a")
> a==a1
[1]  TRUE FALSE FALSE
```

### Matrizes

Dentro do R existe uma classe chamada *matrix*, que guarda objetos do mesmo tipo em forma de matriz, ou seja, guarda os objetos por linhas e colunas.

Mesmo sendo uma estrutura de dados em que cada objeto pode ser identificado por um par de índices, como no caso do vetor, diferentemente do vetor as matrizes são uma classe no R.

Para criar um novo objeto do tipo matrix podemos usar a função matrix(data=, nrow=, ncol=, byrow=, dimnames=).

| Nome | Descrição |
|-------------|-------------|
| data | vetor com os objetos que serão alocados dentro da matrix |
| ncol | número de colunas da matriz |
| nrow | número de linhas da matriz |
| byrow | TRUE ou FALSE, que indica se os objetos serão alocados por linha ou por coluna |
| dimnames | uma lista com os nomes para as linhas e colunas da matriz |

Se alguma das informações não for preenchida, será considerado o valor padrão para cada entrada.

Alguns exemplos de como criar matrizes:
```R
> m1 <- matrix(c(1, 2, 3, 11, 12, 13), nrow=2, ncol=3, byrow=TRUE)
> m1
     [,1] [,2] [,3]
[1,]    1    2    3
[2,]   11   12   13
> class(m1)
[1] "matrix" "array"

> m2 <- matrix(c(1, 2, 3, 11, 12, 13), nrow=3, ncol=2, byrow=TRUE)
> m2
     [,1] [,2]
[1,]    1    2
[2,]    3   11
[3,]   12   13

> m3 <- matrix(c(1, 2, 3, 11, 12, 13), nrow=3, ncol=2)
> m3
     [,1] [,2]
[1,]    1   11
[2,]    2   12
[3,]    3   13
```

Os elementos de uma matriz também são acessados usando os colchetes [], mas diferentemente do vetor, aqui temos que informar o índice da linha e da coluna que queremos acessar, separados por vírgula.
```R
> m3[2,1]
[1] 2
```
Podemos usar os colchetes ainda para acessar uma linha inteira ou coluna inteira da matriz. Nesse caso, o objeto retornado será um vetor dos objetos da linha ou coluna da matriz.
```R
> m3[1,]
[1]  1 11
> m3[,2]
[1] 11 12 13
```
Se quisermos o número de linhas de uma matriz , podemos usar a função *nrow()*, e se quisermos o número de colunas usamos a função *ncol()*.
```R
> nrow(m3)
[1] 3
> ncol(m3)
[1] 2
```

### Listas

Um objeto da classe *list* se diferencia de um vetor pelo fato de poder guardar objetos de tipos diferentes. Além disso, as listas definem uma classe, e um vetor não.

Para criarmos uma lista vamos usar a função **list()**:
```R
> l1 <- list()
> l1
list()
```
O objeto *l1* criado representa uma lista vazia.

Se dentro dos parênteses colocarmos uma sequência de objetos, a lista criada será composta por tais objetos.
```R
> l2 <- list(1, "a", TRUE)
> l2
[[1]]
[1] 1

[[2]]
[1] "a"

[[3]]
[1] TRUE

> class(l2)
[1] "list"

> l3 <- list(c(1, 2, 3), c(1, 1, 1, 1), TRUE, c("A", "a"))
> l3
[[1]]
[1] 1 2 3

[[2]]
[1] 1 1 1 1

[[3]]
[1] TRUE

[[4]]
[1] "A" "a"
```

Podemos também criar uma lista de listas:
```R
> l4 <- list(l1, l2, l3)
> l4
[[1]]
list()

[[2]]
[[2]][[1]]
[1] 1

[[2]][[2]]
[1] "a"

[[2]][[3]]
[1] TRUE


[[3]]
[[3]][[1]]
[1] 1 2 3

[[3]][[2]]
[1] 1 1 1 1

[[3]][[3]]
[1] TRUE

[[3]][[4]]
[1] "A" "a"
```

Enquanto usamos colchetes simples [] para acessar a posição de um vetor, para acessar as posições de uma lista usaremos colchetes duplo [[]].
```R
> l3[[2]]
[1] 1 1 1 1
> l3[[1]][2]
[1] 2
```

Para saber o tamanho de uma lista, também podemos usar o comando *length()*.
```R
> length(l1)
[1] 0
> length(l2)
[1] 3
> length(l3[[2]])  # tamanho do segundo objeto da lista 3
[1] 4
> length(l4)
[1] 3
```

Da mesma forma que em um vetor, novas posições de uma lista podem ser alocadas após a criação do objeto. No caso das listas, usaremos o colchete duplo para isso.

Além de alocar novas posições, ele também serve para modificar posições já existentes.
```R
> l2[[4]] <- c(1, 4, 8)
> l2
[[1]]
[1] 1

[[2]]
[1] "a"

[[3]]
[1] TRUE

[[4]]
[1] 1 4 8
```

### Data frame

Trata-se de um objeto que guarda dados em forma bidimensional, como uma tabela.

Cada valor guardado em objetos desse tipo pode ser acessado pelos índices de linha e coluna em que ele está alocado.

Para criar um novo objeto do tipo *data.frame* podemos usar a função **data.frame()**, e dentro dos parênteses indicamos as colunas do objeto em forma de um vetor.

**obs:** cada vetor que define uma coluna tem que ter a mesma dimensão, que será o número de linhas do objeto data.frame criado.
```R
> dados <- data.frame(c("Maria", "Fiona", "Carmen", "Laura"), c(4, 5, 1, 3), c(F, F, F, T), stringsAsFactors=FALSE)
> class(dados)
[1] "data.frame"
> dados
  c..Maria....Fiona....Carmen....Laura.. c.4..5..1..3. c.F..F..F..T.
1                                    Maria             4         FALSE
2                                    Fiona             5         FALSE
3                                   Carmen             1         FALSE
4                                    Laura             3          TRUE
```
Foi criado o objeto dados do tipo data.frame.

O comando *stringsAsFactors=FALSE* faz com que os objetos do tipo character não sejam convertidos para o tipo *factor*.

Para nomear as colunas, ou editar seus nomes, e assim facilitar a manipulação dos dados, você pode usar a função *names()*.

Essa função serve tanto para retornar os nomes das colunas de um objeto data.frame quanto para editá-los.
```R
> names(dados)
[1] "c..Maria....Fiona....Carmen....Laura.."
[2] "c.4..5..1..3."                           
[3] "c.F..F..F..T."

> names(dados) <- c("nome", "periodo", "res.niteroi")
> names(dados)
[1] "nome"        "periodo"     "res.niteroi"

> dados
     nome periodo res.niteroi
1   Maria       4       FALSE
2   Fiona       5       FALSE
3  Carmen       1       FALSE
4   Laura       3        TRUE
```

Uma alternativa seria criar o objeto data.frame já com os nomes das colunas desejados.

Para isso, basta criar cada vetor coluna com o nome escolhido.
```R
> nome <- c("Maria", "Fiona", "Carmen", "Laura")
> periodo <- c(1, 2, 1, 0)
> res.niteroi <- c(F, T, F, T)
> dados <- data.frame(nome, periodo, res.niteroi, stringsAsFactors=FALSE)
> dados
     nome periodo res.niteroi
1   Maria       1       FALSE
2   Fiona       2        TRUE
3  Carmen       1       FALSE
4   Laura       0        TRUE

> names(dados)
[1] "nome"        "periodo"     "res.niteroi"
```
Outra forma ainda de fazer a mesma coisa:
```R
> dados <- data.frame(nome=c("Maria", "Fiona", "Carmen", "Laura"), periodo=c(1, 2, 1, 0), res.niteroi=c(F, T, F, T), stringsAsFactors=FALSE)
> dados
     nome periodo res.niteroi
1   Maria       1       FALSE
2   Fiona       2        TRUE
3  Carmen       1       FALSE
4   Laura       0        TRUE

> names(dados)
[1] "nome"        "periodo"     "res.niteroi"
```

Cada elemento de um objeto data.frame pode ser acessado usando o comando colchetes [,] e indicando antes da vírgula o índice da linha e depois da vírgula o índice da coluna.
```R
> dados[1,1]
[1] "Maria"
> dados[3,2]
[1] 1
```
Com o comando [,] também é possível acessar uma linha ou coluna inteira, nesse caso você deve indicar somente o índice da linha, para acessar uma linha, ou somente o índice da coluna, para acessar uma coluna.
```R
> dados[2,]
2 Fiona       2        TRUE
> dados[,3]
[1] FALSE  TRUE FALSE  TRUE
```

Também é possível acessar cada coluna usando o comando $ seguido pelo nome da coluna.
```R
> dados$nome
[1] "Maria"  "Fiona"  "Carmen" "Laura"
> dados$periodo
[1] 1 2 1 0
```

As funções nrow() e ncol() também podem ser usadas para retornar o número de linhas e colunas de um objeto do tipo data.frame.
```R
> ncol(dados)
[1] 3
> nrow(dados)
[1] 4
```

Vejamos agora como incluir novos dados em um objeto do tipo data.frame já criado. Com o comando $ é possível adicionar uma nova coluna.
```R
> dados$curso = c("estatistica", "engenharia", "matematica", "engenharia")
> dados
    nome periodo res.niteroi       curso
1  Maria       1       FALSE estatistica
2  Fiona       2        TRUE  engenharia
3 Carmen       1       FALSE  matematica
4  Laura       0        TRUE  engenharia
```

Para adicionar uma nova linha






---
## Capítulo 2: Controle de fluxo

### If/else

*Sintaxe:*
```R
if (condicao){
  # comandos caso condicao seja verdadeira
} else {
  # comandos caso condicao seja falsa
}
```
ou
```R
if (condicao){
  # comandos caso condicao seja verdadeira
}
```
Dentro do par de parênteses seguidos do **if** tem que ter um objeto do tipo *logical*.

Os comandos dentro do primeiro par de chaves serão executados caso o objeto condicao seja TRUE.

Caso contrário, os comandos de dentro do par de chaves depois do **else** serão executados.

O comando else é opcional, e no caso de o else não aparecer, nada será executado caso o objeto condicao seja FALSE.

Vejamos um primeiro exemplo em que um texto é impresso na tela, o que será impresso depende do valor guardado na variável x.
```R
> x <- 2
> if(x < 5){
  print(paste(x, "e menor que", 5))
} else{
  print(paste(x, "e maior ou igual a", 5))
}
[1] "2 e menor que 5"
```
A função *print()* é responsável por imprimir na tela, e a função paste() por concatenar textos e criar um único objeto do tipo character.

Se a variável x receber um valor maior que 5 o texto impresso é outro.
```R
> x <- 8
> if(x < 5){
  print(paste(x, "e menor que", 5))
} else{
  print(paste(x, "e maior ou igual a", 5))
}
[1] "8 e maior ou igual a 5"
```

Outro exemplo simples:
```R
> x <- 3
> if(x > 2){
  y <- 2*x
} else{
  y <- 3*x
}
> print(y)
[1] 6
```
O controle de fluxo if/else será usado na maioria das vezes dentro de funções, como veremos no próximo capítulo (3).

### for

*Sintaxe:*
```R
> for(i in valores){
  # comandos que em geral dependem do valor de i
}
```
Dentro do par de parênteses valores, é um vetor de objetos, que pode ser de qualquer tipo.

Os comandos de dentro do par de chaves serão executados, repetidamente, e em cada iteração o objeto **i** vai assumir um valor diferente, valores esses guardados no vetor valores.

O **for** é o primeiro exemplo de um controle de fluxo que executa uma estrutura de repetição, conhecida como laço (*loop*).
```R
> y <- 0
> for(i in 1:10){
  y <- y+1
}
> print(y)
[1] 10
```
Veja que y começa com o valor 0.

Quando i = 1, y é incrementado de 1 unidade e passa a guardar o valor 0 + 1 = 1, e assim por diante até que temos i = 10, quando y recebe seu último incremento e passa a guardar o valor 10.

Outro exemplo:
```R
> x <- 3
> for(var in 2:5){
  x <- x+var
}
> print(x)
[1] 17
```
Veja que x começa guardando o valor 3.

Na primeira iteração do for, a variável *var* assume o valor 2 e dessa forma o valor de x é atualizado para 3 + 2 = 5.

Na segunda iteração, var assume o valor 3 e assim o valor de x é atualizado para 5 + 3 = 8 e assim por diante até que x passa a assumir o valor final 17.

O exemplo a seguir apresenta valores não numéricos para a variável de dentro do for.
```R
> alfabeto <- NULL
> for (a in LETTERS){
    alfabeto = paste(alfabeto, a)
}
> print(alfabeto)
[1] " A B C D E F G H I J K L M N O P Q R S T U V W X Y Z"
```

Para terminar os exemplos sobre o comando de fluxo for, vamos apresentar alguns exemplos em que dois for são combinados, um dentro do outro.

Suponha que temos uma matrix 5x5 cheia de zeros e queremos preencher cada posição dessa matriz com o número 1:
```R
M <- matrix(0, nrow=5, ncol=5)
for(i in 1:5){
  for(j in 1:5){
    M[i,j] <- 1
  }
}
> M
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    1    1    1    1
[2,]    1    1    1    1    1
[3,]    1    1    1    1    1
[4,]    1    1    1    1    1
[5,]    1    1    1    1    1
```
E se quiséssemos preencher cada posição de uma matriz com o número que indica a sua linha?
```R
M <- matrix(0, nrow=5, ncol=5)
for(i in 1:5){
  for(j in 1:5){
    M[i, j] <- i
  }
}
> M
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    1    1    1    1
[2,]    2    2    2    2    2
[3,]    3    3    3    3    3
[4,]    4    4    4    4    4
[5,]    5    5    5    5    5
```

### while

Sintaxe:
```R
while (condicao) {
  # comandos
}
```

Dentro do par de parentêses seguidos do while, tem que ter um objeto do tipo logical. Os comandos dentro do primeiro par de chaves serão executados repretidamente enquanto a condição for verdadeira.

É importante garantir que em algum momento a condição seja falsa, se não teremos um loop infinito.

A sequência de comandos a seguir usa o controle de fluxo while para criar um vetor com os números de 1 até 100:
```R
vetor <- 1
while(length(vetor) < 100){
  i <- length(vetor)
  vetor[i+1] <- i+1
}
> vetor
  [1]   1   2   3   4   5   6   7
  [8]   8   9  10  11  12  13  14
 [92]  92  93  94  95  96  97  98
 [99]  99 100
```

Podemos usar o while para criar um vetor com os números pares entre 1 e 100:
```R
vetor <- NULL
i = 1
while(i<50){
  vetor <- c(vetor, 2*i)
  i <- i+1
}
> vetor
 [1]  2  4  6  8 10 12 14 16 18 20
[11] 22 24 26 28 30 32 34 36 38 40
[21] 42 44 46 48 50 52 54 56 58 60
[31] 62 64 66 68 70 72 74 76 78 80
[41] 82 84 86 88 90 92 94 96 98
```

### Repeat/break

Sintaxe:
```R
> repeate{
  # comandos
  if (condicao)
    break
}
```










---
## Capítulo 3: Funções e o conceito de variável local














---
## Capítulo 4: Algoritmos para cálculos estatísticos

Serão apresentados e discutidos alguns pseudocódigos.  
A maioria das funções que serão implementadas nesta seção já estão prontas no R; mas não vamos usar estas, e sim criar as nossas próprias funções.

### Máximo
Queremos escrever um pseudocódigo que recebe como entrada um vetor de dados e retorna o seu máximo.

A ideia principal do algoritmo apresentado a seguir é percorrer um vetor guardando o maior elemento encontrado até o momento. O algoritmo termina quando o vetor já foi percorrido por completo.

Entrada: v = vetor com os dados
Saída: valor máximo em v

1. Defina n como o tamanho do vetor v;
2. Faça max = v[1];
3. Inicie i=2;
4. Se v[i]>max, max=v[i];
5. Incremente i: i=i+1;
6. Se i<=n, volta para a linha 4;
7. Retorne max.

Na linha 2, a variável max guarda o primeiro elemento do vetor, pois no início do algoritmo esse é o único valor observado, logo é o máximo até o momento.

Na linha 4, acontece a troca do valor guardado em max, caso o novo valor observado seja maior que o máximo até o momento.

```R
encontrar_maximo<-function(v){
  n<-length(v)
  max<-v[1]
  i<-2
  while(i<=n){
     if(v[i]>max){
       max<-v[i]
     }
     i<-i+1
  }
  return(max)
}
encontrar_maximo(c(1,8,2,7))
[1] 8
```

### Mínimo
A mesma coisa do anterior, só que retorna o valor mínimo.

```R

```

### Média amostral
Queremos agora escrever um pseudocódigo que recebe como entrada um vetor de dados e retorna a sua média.

A ideia principal será percorrer o vetor v somando os seus elementos um a um. Quando v já estiver sido percorrido por completo, basta dividir a soma final pelo número total de elementos que encontraremos a média.

Entrada: v = vetor com os dados
Saída: a média amostral dos valores de v

1. Defina n como o tamanho do vetor v;
2. Inicie soma=0;
3. Inicie i=1;
4. Incremente a variável soma: soma=soma+v[i];
5. Incremente a variável i: i=i+1;
6. Se i<=n, volte para o passo 4;
7. Faça média=soma/n;
8. Retorne média.

```R
media_amostral<-function(v){
  n<-length(v)
  soma<-0
  media<-0
  i<-1
  while(i<=n){
     soma<-soma+v[i]
     i<-i+1
  }
  media<-soma/n
  return(media)
}
media_amostral(c(2,6,7))     # 2+6+7=15, 15/3=5, 3=n
[1] 5
```

### Mediana
Queremos agora escrever um pseudocódigo que recebe como entrada um vetor de dados e retorna a sua mediana.

Entrada: v = vetor com os dados
Saída: a mediana dos valores de v

1. Defina n como o tamanho do vetor v;
2. Defina v_o como o vetor v ordenado;
3. Se n é ímpar, faça mediana = v_o=[(n+1)/2];
4. Se n é par, faça mediana = (v_o=[n/2] + v_o=[(n/2)+1])/2;
5. Retorne mediana.

Veja que nesse algoritmo não temos a existência de laços.

Na linha 2 o vetor v é ordenado. Ainda não aprendemos como ordenar vetores e por isso usaremos a função *sort* para isso.

### Quartis






---
## Capítulo 5:














