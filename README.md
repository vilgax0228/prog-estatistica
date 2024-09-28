## Capítulo 1: Objetos e Classes

Uma função muito usada com objetos da classe "character" é a função **paste()**.

Ela recebe como argumento de entrada objetos do tipo "character" e retorna um *único* objeto, também do tipo "character", que é definido pela *concatenação* dos objetos passados como entrada.

Quando chamamos o comando paste() podemos indicar como os objetos serão separados na concatenação usando o argumento de entrada *sep*. Se este argumento não for definido, ele será considerado como espaço.
```R
> paste("a", "b", "c")
[1] "a b c"
> paste("a", "b", "c", sep=",")
[1] "a,b,c"
> paste("a", "b", "c", sep="")
[1] "abc"
```

Operadores lógicos **&**(E) e **|**(OU):
```R
> A <- TRUE
> B <- FALSE
> A&B
[1] FALSE
> A|B
[1] TRUE
```
Também podemos realizar a negação desses objetos usando o comando **!**.
```R
> negA <- !A
> negA
[1] FALSE
> negB <- !B
> negB
[1] TRUE
```
Se quisermos testar se dois objetos são iguais ou diferentes, podemos usar os operadores **==** ou **!=**.
```R
> a <- 1
> b <- 1
> c <- 2
> d <- "2"
> a==b
[1] TRUE
> a!=b
[1] FALSE
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
> V_1 <- TRUE
> V_2 <- TRUE
> F_1 <- FALSE
> F_2 <- FALSE
> V_1 + V_2
[1] 2
> V_1 - V_2
[1] 0
> F_1 * V_2
[1] 0
> V_1 * V_2
[1] 1
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

**Vetores**

No R um **vetor** é uma *estrutura de dados* que armazena uma coleção de objetos em que todos são de uma mesma classe.

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
[1] TRUE  TRUE FALSE FALSE
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
Para acessarmos a posição (index) de um vetor usamos os colchetes [].
```R
> a[1]
[1] 1
> b[2]
[1] "b"
> c[3]
[1] FALSE
```
Se tentamos acessar uma posição que não tenha sido definida, a resposta será *NA* (not available).
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
No exemplo anterior o objeto d foi iniciado como um vetor de tamanho 1 da classe "numeric".

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
[1] 0 1 2 3 4 2 4

> b <- c("a", "b")
> b
[1] "a" "b"
> c(a, b)  # concatenando dois vetores de classes diferentes, uma delas é transformada por coerção
[1] "0" "1" "2" "3" "4" "a" "b"
```
**obs:** aqui nesse caso, é mais fácil de se transformar números em strings que strings de texto em números.

Temos ainda outras maneiras de criar um vetor:
```R
> 1:10
[1] 1 2 3 4 5 6 7 8 9 10
> seq(1, 20, by=2)
[1] 1  3  5  7  9 11 13 15 17 19
> rep(0, times=0)
[1] 0 0 0 0
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
[1] 1 2 3 4 5 6 7 8 9 10
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

**Matrizes**





---
**Exercícios versão livro - Capítulo 1: Classes e Objetos**

---
**Exercícios versão professor - Capítulo 1: Classes e Objetos**

1. uso da função *rbind()* para criar a matriz A. Depois use as funções *rownames()* e *colnames()* e dê os seguintes nomes as linhas: linha1 (para a primeira linha), e linha2(para a segunda linha), faça o mesmo para as colunas usando os nomes: col1, col2, etc.
```R
> A = rbind(c(14, 1, 8, 2, 17), c(20, 6, 1, 10, 6))
> A
      [,1] [,2] [,3] [,4] [,5]
[1,]    14    1    8    2   17
[2,]    20    6    1   10    6

> rownames(A) <- c("linha1", "linha2")
> colnames(A) <- c("col1", "col2", "col3", "col4", "col5")
> A
       col1 col2 col3 col4 col5
linha1   14    1    8    2   17
linha2   20    6    1   10    6
```
2. Use a função *cbind()* para criar a matriz A do exercício anterior.
```R
> A = cbind(c(14, 20), c(1, 6), c(8, 1), c(2, 10), c(17, 6))
> A
     [,1] [,2] [,3] [,4] [,5]
[1,]   14    1    8    2   17
[2,]   20    6    1   10    6
```
3. Usando o comando *:* e a função *matrix()* crie a matriz.
```R
> m <- matrix(1:36, nrow=6, ncol=6)
> m
     [,1] [,2] [,3] [,4] [,5] [,6]
[1,]    1    7   13   19   25   31
[2,]    2    8   14   20   26   32
[3,]    3    9   15   21   27   33
[4,]    4   10   16   22   28   34
[5,]    5   11   17   23   29   35
[6,]    6   12   18   24   30   36
```
4. Crie as matrizes A e B e use o operador %*% que fornece a multiplicação entre duas matrizes.
```R
> A <- c(3, -1, 0, -3, -5, 4)
> dim(A) <- c(2, 3)
> A
     [,1] [,2] [,3]
[1,]    3    0   -5
[2,]   -1   -3    4

> B <- matrix(c(-5, 5, 2, 1, -2, 0), nrow=3, ncol=2)
> B
     [,1] [,2]
[1,]   -5    1
[2,]    5   -2
[3,]    2    0

> A%*%B
     [,1] [,2]
[1,]  -25    3
[2,]   -2    5
```
5. A função *dim()* retorna a dimensão de uma matriz. Usando as matrizes A e B do exercício anterior, obtenha a dimensão de A, de B, de AB e de BA.
```R
> dim(A)
[1] 2 3
> dim(B)
[1] 3 2
> dim(A%*%B)
[1] 2 2
> dim(B%*%A)
[1] 3 3
```
