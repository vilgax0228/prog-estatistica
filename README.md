# Capítulo 4: Algoritmos para cálculos estatísticos
Serão apresentados e discutidos alguns pseudocódigos.  
A maioria das funções que serão implementadas nesta seção já estão prontas no R; mas não vamos usar estas, e sim criar as nossas próprias funções.

## Máximo
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

## Mínimo
```R

```

## Média amostral
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

## Mediana
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

## Quartis
Entrada: v = vetor com os dados
Saída: um vetor com os 3 quartis dos valores de v

1. Defina n como o tamanho do vetor v;
2. Defina v_o como o vetor v ordenado;
3. Sendo n par, defina k = n/2 e j = k+1;
4. Sendo n ímpar, defina k = (n-1)/2 e j = k+2;
5. Defina v_1 como um vetor com os elementos de v_o das posições de 1 até k;
6. Defina v_2 como um vetor com os elementos de v_o das posições de j até n;
7. q_1 = mediana de v_1;
8. q_2 = mediana de v;
9. q_3 = mediana de v_2;
10. Retorna o vetor (q_1,q_2,q_3).

## Variância amostral
Queremos escrever um pseudocódigo que recebe como entrada um vetor de dados e retorna a sua variância amostral.

Para isso, primeiro será encontrada a média amostral. Em seguida o vetor de entrada será percorrido e assim será calculada a variância amostral

Entrada: v = vetor com os dados
Saída: variância amostral dos valores de v

1. Defina n como o tamanho do vetor v;
2. Defina m como a média amostral do vetor v;
3. Inicie soma = 0;
4. Inicie i=1;
5. Incremente a variável soma: soma = soma + (v[i] - m)^2;
6. Incremente i: i=i+1;
7. Se i <= n, volta para a linha 5;
8. Faça s2 = soma/(n-1);
9. Retorne s2.

## Covariância amostral






---
# Capítulo 5: Algoritmos para cálculos matriciais

## Multiplicação de vetor por escalar
Queremos escrever um pseudocódigo que recebe como entrada um vetor v e um escalar a retorna o vetor definido por w = av. Para isso basta percorrer o vetor v multiplicando cada posição pelo escalar a.

Entrada: v = vetor que guarda as coordenadas de um vetor, a = número real.  
Saída: vetor definido pelo produto a com v.

1. Defina n como o tamanho do vetor v;
2. Inicie o vetor w como nulo;
3. Inicie i=1;
4. Faça w[i] = a*v[i];
5. Incremente i: i=i+1;
6. Se i <= n, volte para a linha 4;
7. Retorne w.

## Soma de vetores
Queremos escrever um pseudocódigo que recebe como entrada dois vetores v e u e retorna o vetor definido pela soma deles.

Veja que, para essa operação ser realizada, é preciso que ambos os vetores tenham mesma dimensão. Para encontrar a soma dos dois vetores de mesma dimensão, basta somar cada posição uma a uma.

Entrada: v = vetor que guarda as coordenadas de um vetor; u = vetor que guarda as coordenadas de outro vetor.  
Saída: vetor com os elementos do vetor definido pela soma de v com u.

1. Defina n como o tamanho do vetor v;
2. Defina k como o tamanho do vetor u;
3. Se n e k forem diferentes, retorne uma mensagem de erro e fim;
4. Inicie o vetor w como nulo;
5. Inicie i=1;
6. Faça w[i] = v[i] + u[i];
7. Incremente i: i=i+1;
8. Se i <= n, volte para a linha 6;
9. Retorne w.

## Subtração de vetores

6. Faça w[i] = v[i] - u[i];

## Produto interno
Queremos escrever o pseudocódigo que recebe como entrada dois vetores v e u e retorna o produto interno entre eles. Veja que essa operação só é possível se ambos os vetores tiverem mesma dimensão.

A ideia é percorrer as posições dos vetores, multiplicando posição a posição e guardando a soma em uma variável local.

Entrada: v = vetor que guarda as coordenadas de um vetor; u = vetor que guarda as coordenadas de outro vetor.  
Saída: o valor numérico do produto interno entre u e v.

1. Defina n como o tamanho do vetor v;
2. Defina k como o tamanho do vetor u;
3. Se n e k forem diferentes, retorne uma mensagem de erro e fim;
4. Inicie p=0;
5. Inicie i=1;
6. Incremente p: p = p + v[i]*u[i];
7. Incremente i: i=i+1;
8. Se i <= n, volte para a linha 6;
9. Retorne p.

## Multiplicação de matriz por escalar
Queremos escrever um pseudocódigo que recebe como entrada uma matriz A e um escalar a e retorna a matriz definida por M = aA.

Para isso basta percorrer a matriz A multiplicando cada posição pelo escalar a. Mas lembre-se de que para percorrer uma matriz é preciso usar dois laços, um dentro do outro.

Entrada: A = matriz de números reais; a = número real.  
Saída: uma matriz definida pelo produto de a com A.

1. Defina n número de linhas da matriz A;
2. Definida m número de colunas da matriz A;
3. Inicie uma matriz M de dimensão n x m;
4. Inicie i=1;
5. Inicie j=1;
6. Faça M[i,j] = a*A[i,j];
7. Incremente j: j=j+1;
8. Se j <= m volte para a linha 6;
9. Incremente i: i=i+1;
10. Se i <= n volte para a linha 5;
11. Retorne M.

## Soma de matrizes
Queremos escrever o pseudocódigo que recebe como entrada duas matrizes A e B e retorna a matriz definida pela soma delas.

Novamente como teremos que percorrer as linhas e colunas das matrizes, será preciso usar dois laços, um dentro de outro.

Entrada: A = matriz de números reais; B = matriz de números reais.  
Saída: uma matriz definida pela soma de A com B.

1. Defina n número de linhas da matriz A;
2. Defina m número de colunas da matriz A;
3. Defina l número de linhas da matriz B;
4. Defina c número de colunas da matriz B;
5. Se n é diferente de l, retorne uma mensagem de erro e fim;
6. Se m é diferente de c, retorne uma mensagem de erro e fim;
7. Inicie uma matriz M de dimensão n x m;
8. Inicie i=1;
9. Inicie j=1;
10. Faça M[i,j] = A[i,j] + B[i,j];
11. Incremente j: j=j+1;
12. Se j <= m volte para a linha 10;
13. Incremente i: i=i+1;
14. Se i <= n volte para a linha 9;
15. Retorne M

## Subtração de matrizes
10. Faça M[i,j] = A[i,j] - B[i,j]

## Transposição de matrizes
Queremos escrever um pseudocódigo que recebe como entrada uma matriz A e retorna a sua transposta.

Veja que só precisamos percorrer 

## Multiplicação entre matriz e vetor

## Multiplicação de matrizes




# Parte II: Recursão

# Capítulo 6: Algoritmos recursivos simples
















# Capítulo 7: Algoritmos de ordenação















