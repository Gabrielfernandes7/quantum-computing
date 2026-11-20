# Sistemas quânticos individuais

**Objetivo:** entender como representar, medir e transformar informações clássicas e quânticas utilizando vetores e matrizes.

Se conseguirmos pensar em um problema e abstraí-lo, podemos resolvê-lo utilizando informação quântica.

A informação quântica pode ser abordada de duas formas principais:

| Critério | Descrição simplificada | Descrição geral |
| :--- | :--- | :--- |
| **Representação de estados** | Utiliza vetores. | Utiliza matrizes de densidade. |
| **Operações e medições** | Operações representadas por matrizes unitárias. | Permite uma classe mais geral de operações e medições. |
| **Complexidade e alcance** | Mais simples de aprender. | Mais abrangente. |
| **Aplicação e escopo** | Suficiente para compreender a maioria dos algoritmos quânticos. | Inclui a descrição simplificada e a informação clássica como casos especiais. |

## Informação clássica

A informação clássica é representada por estados de um sistema físico e, quando existe incerteza sobre qual estado ele ocupa, por um vetor de probabilidades.

**Estado clássico:** considere um sistema $X$ que armazena um bit de informação. Ele pode assumir dois estados:

$$
\Sigma = \{0, 1\}
$$

Sendo:

- $\Sigma$: conjunto de estados possíveis.
- $X$: sistema que armazena a informação.

**Representação por um vetor de probabilidades:** considere 75% de chance de estar no estado 0 e 25% de chance de estar no estado 1.

$$
P(X=0) = \frac{3}{4}
$$

$$
P(X=1) = \frac{1}{4}
$$

Podemos representar essa distribuição por um vetor coluna:

$$
v =
\begin{bmatrix}
\frac{3}{4} \\
\frac{1}{4}
\end{bmatrix}
$$

Este $v$ é o nosso vetor de probabilidades e possui duas propriedades:

- Todos os seus elementos são números reais não negativos:

$$
\mathbb{R}_+ = \{x \in \mathbb{R} \mid x \ge 0\}
$$

- A soma dos elementos é igual a 1.

## Notação de Dirac

Também conhecida como notação bra-ket.

Os estados clássicos podem ser representados por vetores:

$$
|0\rangle =
\begin{bmatrix}
1 \\
0
\end{bmatrix}
\qquad
|1\rangle =
\begin{bmatrix}
0 \\
1
\end{bmatrix}
$$

**Ket — vetor coluna:**

$$
|0\rangle =
\begin{bmatrix}
1 \\
0
\end{bmatrix}
$$

**Bra — vetor linha:**

$$
\langle 0| =
\begin{bmatrix}
1 & 0
\end{bmatrix}
$$

Para o estado 1:

$$
|1\rangle =
\begin{bmatrix}
0 \\
1
\end{bmatrix}
$$

$$
\langle 1| =
\begin{bmatrix}
0 & 1
\end{bmatrix}
$$

### Multiplicação de bra por ket

> [!NOTE]
> Quando multiplicamos um vetor linha por um vetor coluna, obtemos um escalar, ou seja, um único número.

$$
\langle a|b\rangle =
\begin{cases}
1 & \text{se } a=b \\
0 & \text{se } a\neq b
\end{cases}
$$

**Exemplos:**

$$
\langle 0|0\rangle =
\begin{bmatrix}
1 & 0
\end{bmatrix}
\begin{bmatrix}
1 \\
0
\end{bmatrix}
= 1
$$

$$
\langle 0|1\rangle =
\begin{bmatrix}
1 & 0
\end{bmatrix}
\begin{bmatrix}
0 \\
1
\end{bmatrix}
= 0
$$

Isso representa uma propriedade chamada **ortogonalidade**: os vetores de estados diferentes da base padrão são ortogonais.

### Multiplicação de ket por bra

O resultado é uma matriz.

**Exemplo:**

$$
|0\rangle\langle 0| =
\begin{bmatrix}
1 \\
0
\end{bmatrix}
\begin{bmatrix}
1 & 0
\end{bmatrix}
$$

**Resultado:**

$$
|0\rangle\langle 0| =
\begin{bmatrix}
1 & 0 \\
0 & 0
\end{bmatrix}
$$

## Operações determinísticas

É uma transformação em que o resultado é sempre determinado pelo estado inicial.

$$
f:\Sigma\rightarrow\Sigma
$$

**Exemplo com bits clássicos:**

$$
\Sigma = \{0, 1\}
$$

Podemos definir uma função que inverte o bit:

$$
f(0)=1 \qquad f(1)=0
$$

Essa transformação pode ser representada pela matriz a seguir:

$$
M =
\begin{bmatrix}
0 & 1 \\
1 & 0
\end{bmatrix}
$$

Aplicamos a operação de inverter o bit multiplicando a matriz $M$ pelo vetor que representa o estado: $v\longrightarrow Mv$

Por exemplo, para o estado zero

$$
M|0 \rangle =
\begin{bmatrix}
0 & 1 \\
1 & 0
\end{bmatrix}
\begin{bmatrix}
1 \\
0
\end{bmatrix}
=
\begin{bmatrix}
0 \\
1
\end{bmatrix}
= |1\rangle
$$

Isso ocorre porque o estado 0 foi transformado no estado 1.

**Produto externo:**

Quando vimos sobre produtos de ket por bra vimo que o resultado é uma matriz:

$$
|0\rangle\langle0|=
\begin{bmatrix}
1&0\\
0&0
\end{bmatrix}
$$

$$
|0\rangle\langle1|=
\begin{bmatrix}
0&1\\
0&0
\end{bmatrix}
$$

$$
|1\rangle\langle0|=
\begin{bmatrix}
0&0\\
1&0
\end{bmatrix}
$$

$$
|1\rangle\langle1|=
\begin{bmatrix}
0&0\\
0&1
\end{bmatrix}
$$

A regra geral apresentada é:

$$
M =
|a\rangle\langle b|
$$

Perceba que, se assumimos que a é linha e b é coluna, conseguimos saber exatamente onde encontrar o nosso 1 na matriz. Exemplo: se $|0\rangle\langle 1|$ temos algo como: $M01$, ou seja, na posição 01 da matriz encontramos o nosso 1.

**Represntação matricial de operações determinísticas**

Retomando o conceito anterior, uma função determinística transforma um estado em outro:

$$
f:\Sigma\rightarrow\Sigma
$$

A matriz que representa essa expressão pode ser construída pela operação:

$$
M=\sum_{b\in\Sigma}|f(b)\rangle\langle b|
$$

- $M$: matriz que representa a operação.
- $\sum$: soma dos termos
- $b\in\Sigma$: percorremos todos os estados possíveis.
- $|f(b)\rangle$: estado resultante da transformação.
- $\langle b|$: identifica o estado de entrada.

Propriedade importante:

$$
M|a\rangle=|f(a)\rangle
$$

Ou seja, quando aplicamos a matriz ao vetor de um estado, obtemos exatamente o vetor do estado transformado.

**Operações probabilísticas**

São operações clássicas que introduzem incerteza ou aleatoriedade.

Exemplo: Se o estado for 0, faça nada, caso for 1, inverta o bit com probabilidade de 1/2 ou 50%.

$$
M=
\begin{bmatrix}
1&\frac{1}{2}\\
0&\frac{1}{2}
\end{bmatrix}
$$

Perceba que cada coluna representa a distribuição de probabilidades do resultado para um determinado estado inicial.

**Matrizes estatocásticas**

> [!NOTE]
> As matrizes estatocásticas possuem duas propriedades:
> Todas entradas são números reais não negativos
> A soma das entradas de cada coluna é igual a 1

**Composição de operações**

Considere $X$ e matrizes estatocásticas $M_1, M_2, \ldots, M_n$, que representam operações probabilísticas sobre esse sistema.

Quando aplicamos essas operações na ordem $M_1, M_2, \ldots, M_n$, a operação composta é representada pelo produto:

$$
M_n \cdots M_2 M_1
$$

> [!WARNING]
> A ordem da multiplicação é importante, pois a multiplicação de matrizes não é comutativa.

Isso significa que, em geral:

$$
M_2M_1 \neq M_1M_2
$$

## Informação quântica

Um estado quântico é representado por um vetor coluna cujo os índices correspondem aos estados clássicos de um sistema.

Existem duas propriedades fundamentais:

1. As entradas do vetor são números complexos
2. A soma dos quadrados das entradas do módulos das entradas deve ser igual a 1

Um estado quântico precisa ser um vetor unitário segunda a norma euclidiana.

**Norma euclidiana**

Para um vetor complexto:

$$
v =
\begin{bmatrix}
\alpha_1\\
\vdots\\
\alpha_n
\end{bmatrix}
$$

Sua norma é definida por:

$$
\|v\| =
\sqrt{\sum_{k=1}^{n}|\alpha_k|^2}
$$

Significado dos elementos:
- $v$: vetor que representa o estado.
- $\alpha_k$: entrada de índice $k$, que pode ser um número complexo.
- $|\alpha_k|$: módulo do número complexo.
- $|\alpha_k|^2$: módulo ao quadrado
- $n$: quantidade de entradas do vetor.
- $\|v\|$: norma do vetor.

$$
\sum_{k=1}^{n}|\alpha_k|^2=1
$$

$$
\|v\|=1
$$

Na informação quântica existe o conceito de superposição. Um qubit pode ser representado por uma combinação linear de estados:

$$
|\psi\rangle = \alpha|0\rangle + \beta|1\rangle
$$