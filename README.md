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

No R um *vetor* é uma estrutura de dados que armazena uma coleção de objetos em que todos são de uma mesma classe.

parei na página 19.

---
**Exercícios - Capítulo 1: Classes e Objetos**

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
4. Crie as matrizes A e B e use o operador *%*%* que fornece a multiplicação entre duas matrizes.
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
