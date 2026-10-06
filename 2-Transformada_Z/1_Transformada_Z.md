## Introdução
A utilização da Transformada Z no estudo de sinais e sistemas converte operações complexas de equações de diferenças em equações algébricas simples, facilitando a análise de sistemas discretos.

### Principais Benefícios
• Simplificação Matemática: Transforma operações de convolução no tempo em multiplicações simples e equações de diferenças em equações algébricas lineares.

• Análise de Estabilidade: Permite determinar se um sistema linear invariante no tempo (SLIT) é estável verificando se os polos da função de transferência estão dentro do círculo unitário no plano complexo.

• Estudo da Causalidade: Facilmente identifica se um sistema é causal com base na Região de Convergência (ROC) da transformada.

• Alcance Amplo: Possui convergência para vários sinais que não possuem uma Transformada de Fourier de Tempo Discreto convergente.

• Projeto de Filtros Digitais: É a base matemática para projetar, otimizar e implementar filtros digitais e sistemas de controle digital.

A Transformada Z é uma ferramenta matemática que converte um sinal discreto no tempo (uma sequência de números) em uma representação no domínio da frequência complexa. Ela funciona como o equivalente em tempo discreto da Transformada de Laplace (usada para sinais contínuos). 

Matematicamente, a Transformada Z unilateral de uma sequência $x[n]$ é definida pela fórmula: 

$$X(z)=\mathcal{Z}\{x[n]\}=\sum _{n=0}^{\infty }x[n]z^{-n}$$

Onde $z$ é uma variável complexa ($z = r e^{j\omega}$). O conjunto de valores de $z$ para os quais a soma converge é chamado de Região de Convergência (ROC). 

#### Exemplos Práticos de Cálculo
Abaixo estão três exemplos clássicos de cálculo da Transformada Z. 
1. Impulso Unitário: $\delta[n]$ 

O impulso unitário vale $1$ apenas em $n=0$ e $0$ para todos os outros valores. 

Cálculo: $X(z) = \sum_{n=0}^{\infty} \delta[n] z^{-n} = 1 \cdot z^{0} = 1$

Resultado: $X(z) = 1$

ROC: Todo o plano $z$. 

2. Degrau Unitário: $u[n]$ 

O degrau unitário vale $1$ para todo $n \geq 0$. 

Cálculo: $X(z) = \sum_{n=0}^{\infty} 1 \cdot z^{-n} = \sum_{n=0}^{\infty} (z^{-1})^n$

Esta é uma série geométrica infinita. Ela converge se $\vert{}z^{-1}\vert{} < 1$, ou seja, $\vert{}z\vert{} > 1$.

Resultado: $X(z) = \frac{1}{1 - z^{-1}} = \frac{z}{z - 1}$

ROC: $\vert{}z\vert{} > 1$ 

3. Sinal Exponencial: $x[n] = a^n u[n]$ Sinal muito comum para modelar decaimentos ou crescimentos. 

Cálculo: $X(z) = \sum_{n=0}^{\infty} a^n z^{-n} = \sum_{n=0}^{\infty} (az^{-1})^n$

Converge se $\vert{}az^{-1}\vert{} < 1$, o que significa 

$\vert{}z\vert{} > \vert{}a\vert{}$.

Resultado: $X(z) = \frac{1}{1 - az^{-1}} = \frac{z}{z - a}$

ROC: $\vert{}z\vert{} > \vert{}a\vert{}$ 

### Principais Propriedades da Transformada Z

As propriedades evitam que você precise calcular somatórios complexos todas as vezes. 

#### Linearidade 
Se o sinal é uma combinação linear de duas sequências, sua transformada Z também será.
 $\mathcal{Z}\{\alpha x_{1}[n]+\beta x_{2}[n]\}=\alpha X_{1}(z)+\beta X_{2}(z)$

#### Deslocamento no Tempo (Atraso) 
Atrasar um sinal no tempo equivale a multiplicá-lo por potências inversas de $z$. Muito útil para resolver equações de diferenças de sistemas digitais. 
$\mathcal{Z}\{x[n-k]\}=z^{-k}X(z)$

#### Convolução no Tempo 
A convolução entre dois sinais no tempo discreto (operação complexa) vira uma multiplicação simples no domínio Z.
$\mathcal{Z}\{x[n]*h[n]\}=X(z)\cdot H(z)$

Nota: É por isso que a função de transferência de um sistema é $H(z) = \frac{Y(z)}{X(z)}$. 

#### Multiplicação por Exponencial (Escalonamento no domínio Z) 
Multiplicar o sinal por uma base exponencial altera a escala da variável $z$. 
$\mathcal{Z}\{a^{n}x[n]\}=X\left$frac{z}{a}\right)$

### Exemplo Prático com Propriedades
Imagine que necessite calcular a transformada Z do sinal 
$y[n] = 2\delta[n] + 3 u[n-1]$. 

Pela propriedade da Linearidade, pode separar os termos:
$Y(z) = 2\mathcal{Z}\{\delta[n]\} + 3\mathcal{Z}\{u[n-1]\}$

Sabe-se do Exemplo 1 que $\mathcal{Z}\{\delta[n]\} = 1$.

Para o segundo termo, utiliza-se a propriedade do Deslocamento no Tempo sobre o degrau unitário (Exemplo 2):

$\mathcal{Z}\{u[n-1]\} = z^{-1} \cdot \mathcal{Z}\{u[n]\} = z^{-1} \left$frac{z}{z-1}\right) = \frac{1}{z-1}$

Juntando tudo: 
$Y(z)=2+\frac{3}{z-1}=\frac{2(z-1)+3}{z-1}=\frac{2z+1}{z-1}$


Para resolver uma equação de diferenças utilizando a Transformada Z, transforma-se o problema do domínio do tempo discreto para o domínio algébrico $z$, isola-se a saída e aplica-se a transformada inversa. 

Seja o seguinte problema prático de um sistema de primeira ordem com condições iniciais nulas (sistema inicialmente em repouso): 

Dada a equação de diferenças: $y[n]-0.5y[n-1]=x[n]$
Onde a entrada é um degrau unitário: $x[n] = u[n]$. Deseja-se encontrar a resposta do sistema $y[n]$ para $n \geq 0$. 

Passo 1: Aplicar a Transformada Z em ambos os lados

Utiliza-se a propriedade da linearidade e do deslocamento no tempo (atraso): 
$\mathcal{Z}\{y[n]\}-0.5\mathcal{Z}\{y[n-1]\}=\mathcal{Z}\{x[n]\}$
Como $\mathcal{Z}\{y[n-1]\} = z^{-1}Y(z)$, tem-se: $Y(z)-0.5z^{-1}Y(z)=X(z)$

Passo 2: Isolar $Y(z)$ para encontrar a Função de Transferência

Colocando $Y(z)$ em evidência no lado esquerdo: 
$Y(z)(1-0.5z^{-1})=X(z)$

$H(z)=\frac{Y(z)}{X(z)}=\frac{1}{1-0.5z^{-1}}=\frac{z}{z-0.5}$

Passo 3: Substituir a Transformada da Entrada $X(z)$Sabemos que a transformada Z do degrau unitário 
$x[n] = u[n]$ é $X(z) = \frac{1}{1 - z^{-1}} = \frac{z}{z-1}$. Substituindo na equação: 

$Y(z)=X(z)\cdot H(z)=\left$frac{z}{z-1}\right)\left$frac{z}{z-0.5}\right)$

Para facilitar a expansão em frações parciais, costuma-se trabalhar com $\frac{Y(z)}{z}$: $\frac{Y(z)}{z}=\frac{z}{(z-1)(z-0.5)}$

Para entender os Polos e Zeros, pense na Transformada Z de um sistema como uma função racional (uma divisão de dois polinômios) que descreve o comportamento desse sistema no plano complexo: 
$H(z)=\frac{N(z)}{D(z)}$

Zeros são os valores de $z$ que zeram o numerador ($N(z) = 0$). Nesses pontos, a resposta do sistema vai para zero.

Polos são os valores de $z$ que zeram o denominador ($D(z) = 0$). Nesses pontos, o sistema tende ao infinito, ou seja, são os pontos de instabilidade/ressonância. O Gráfico de Polos e Zeros (Plano Z)No plano complexo (Plano Z), o eixo horizontal representa a parte Real e o eixo vertical representa a parte Imaginária. Os Zeros são representados graficamente por uma circunferência pequena (O).Os Polos são representados por um "X" (X).

A fronteira mais importante desse plano é o Círculo Unitário (um círculo com raio igual a 1). Ele define a fronteira de estabilidade para sistemas de tempo discreto. O que os Polos dizem sobre o Sistema?

A posição dos polos dita o comportamento natural do sistema (se ele vai oscilar, decair ou explodir): 

Polos dentro do círculo unitário ($\vert{}z\vert{} < 1$): O sistema é estável. A resposta ao impulso decai até zero com o tempo.

Polos sobre o círculo unitário ($\vert{}z\vert{} = 1$): O sistema está no limite da estabilidade. Ele pode apresentar uma oscilação constante (senoide pura) ou um degrau eterno.

Polos fora do círculo unitário ($\vert{}z\vert{} > 1$): O sistema é instável. A resposta cresce exponencialmente até o infinito. 

Exemplo Prático de AnáliseConsidere a seguinte função de transferência de um sistema discreto: 

$H(z)=\frac{z-0.5}{z^{2}-0.25}=\frac{z-0.5}{(z-0.5)(z+0.5)}=\frac{1}{z+0.5}$

Encontrando os Zeros: Olhando para o numerador original, $z - 0.5 = 0 \implies z = 0.5$.Encontrando os Polos: Olhando para o denominador original, $z^2 - 0.25 = 0 \implies z = 0.5$ e $z = -0.5$.

Cancelamento Polo-Zero: Note que o zero em $0.5$ cancela o polo em $0.5$. O sistema simplificado final possui apenas um polo em $z = -0.5$. 

Análise de Estabilidade: Como o módulo do polo restante é $0.5$ (que é menor que 1), este polo está dentro do círculo unitário. Portanto, o sistema é estável. Visualmente, o comportamento desse polo e a região de convergência se comportam da seguinte forma: 







No gráfico acima, verifica-se o polo localizado na metade esquerda do plano, bem protegido dentro do círculo unitário, garantindo que o sistema não "exploda" na prática. 


### Exercício Usando TZ

1. Aplicando a Transformada Z na equação Aplicando a propriedade do deslocamento no tempo 
$y[n-k] \Leftrightarrow z^{-k}Y(z)$: $Y(z)-0,5z^{-1}Y(z)+0,06z^{-2}Y(z)=X(z)$

Isolando $Y(z)$ para obter a função de transferência 

$H(z) = \frac{Y(z)}{X(z)}$: 

$Y(z)(1-0,5z^{-1}+0,06z^{-2})=X(z)$

$H(z)=\frac{1}{1-0,5z^{-1}+0,06z^{-2}}$

2. Fatorando o denominador 

As raízes da equação polinomial equivalente do denominador são $0,3$ e $0,2$ (pois $0,3 \times 0,2 = 0,06$ e $0,3 + 0,2 = 0,5$). 

Reescrevendo a função como: 

$H(z)=\frac{1}{(1-0,3z^{-1})(1-0,2z^{-1})}$

3. Expansão em Frações Parciais 

Divide-se a fração em duas partes com constantes $A$ e $B$: 

$H(z)=\frac{A}{1-0,3z^{-1}}+\frac{B}{1-0,2z^{-1}}$

Para encontrar $A$ multiplica-se $H(z)$ por $(1 - 0,3z^{-1})$ com $z = 0,3$:

$A=3$

Para encontrar $B$ multiplica-se $H(z)$ por $(1 - 0,2z^{-1})$ com $z = 0,2$:

$B =-2$

4. Transformada Z Inversa Sabendo que a transformada inversa de $\frac{1}{1-az^{-1}}$ é $a^n u[n]$ (onde $u[n]$ é a função degrau unitário), tem-se a resposta final: 

$h[n]=3\cdot (0,3)^{n}u[n]-2\cdot (0,2)^{n}u[n]$

## $y[n]=? \     se \ x[n]=u[n]$

No tempo y[n] é a convolução de $h[n]$ com $x[n]$:

$y[n]=x[n]*h[n]$

No domínio Z, y[n] é o produto de $H(z)$ com $X(z)$:

$Y(z)=X(z)H(z)$ 

$Y(z)=\frac{1}{1-z^{-1}} \cdot \frac{1}{1-0,5z^{-1}+0,06z^{-2}}$

Pode-se trabalhar com potências positivas de z, multiplicando por $\frac{z^3}{z^3}$

$Y(z)=\frac{z^3}{z-1} \cdot \frac{1}{z^2-0,5z+0,06}$

