### EXERCÍCIO E3.11
Determine e trace a resposta de entrada nula para os sistemas descritos pelas seguintes equações:

![](/1-Sinais_Sistemas_Tempo_Discreto/1-Figuras/Exercicio3_11.png)

### EXERCÍCIO E3.12


![](/1-Sinais_Sistemas_Tempo_Discreto/1-Figuras/Exercicio3_12.png)

## RESPOSTA $h[n]$ AO IMPULSO UNITÁRIO

### EXEMPLO 3.11 (Determinação iterativa e interativa de $h[n]$)


Determine $h[n]$, a resposta ao impulso unitário de um sistema descrito pela equação

$$
y[n] - 0,6y[n-1] - 0,16y[n-2] = 5x[n]
$$

sujeita ao estado inicial nulo, ou seja, $h[−1] = h[−2] = 0$.
Fazendo $n = 0$ nesta equação
$h[0] = 5$ e, fazendo $n = 1$ nesta equação
$h[1] = 3$

## A SOLUÇÃO FECHADA DE h[n]

### EXEMPLO 3.12

Determine a resposta h[n] ao impulso para o sistema do Exemplo 3.11 especificado pela equação:

$$
y[n] - 0,6y[n-1] - 0,16y[n-2] = 5x[n]
$$

**Solução**
Reescrevendo a equação na forma de avanço ([Equação 1](#eq1)) :

<a id="eq1"></a>
$$
y[n+2] - 0,6y[n+1] - 0,16y[n] = 5x[n+2] 
\tag{1}
$$

Define-se **Resposta ao Impulso** $y[n] = h[n]$  quando $x[n]=\delta[n]$

Então:
$$
h[n+2] - 0,6h[n+1] - 0,16h[n] = 5\delta[n+2]
$$

$a_N= - 0,16$ e $b_N= 0$, sendo estes coeficientes da $n-ésima$ amostra de $h[n]$ e $x[n]$, respectivamente.

Como, $A_0=\frac{b_N}{a_N}=0$, então $h[n]=A_0\delta[n] + y_c[n]u[n]$.

Portanto, $h[n]$ concinde com a solução característica $y_c[n]$ (homogênea) da equação [Equação 1](#eq1). 

![](/1-Sinais_Sistemas_Tempo_Discreto/1-Figuras/Exemplo3_12.jpeg)


EXERCÍCIO E3.14


RESPOSTA DO SISTEMA À ENTRADA EXTERNA: A RESPOSTA DE ESTADO NULO


CONVOLUÇÃO
