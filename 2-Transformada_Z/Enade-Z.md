## Solução de exercícios de enades anteriores

Enade 2023-29

![](./Images/enade2023_29.png)

A equação de diferenças do sistema é dada por: 

$$6y[n]-y[n-1]-y[n-2]=18x[n]+x[n-1]$$

Aplicando a Transformada Z em ambos os lados, temos: 

$$(6-z^{-1}-z^{-2})Y(z)=(18+z^{-1})X(z)$$

A função de transferência é dada por: 

$$H(z)=\frac{Y(z)}{X(z)}=\frac{18+z^{-1}}{6-z^{-1}-z^{-2}}=\frac{18z^{2}+z}{6z^{2}-z-1}=\frac{3z^2+\frac{1}{6}z}{(z+\frac{1}{3})(z-\frac{1}{2})}=\frac{z(3z+\frac{1}{6})}{(z+\frac{1}{3})(z-\frac{1}{2})}$$

Para encontrarmos os polos, resolvemos a equação característica: 

$$6z^{2}-z-1=0$$

$$(3z+1)(2z-1)=0$$

$$z_{1}=-1/3$$

$$z_{2}=1/2$$

Já para encontrarmos os zeros, resolvemos a equação característica: 
$$z(3z+\frac{1}{6})=0$$
$$z_{1}=0$$
$$z_{2}=-\frac{1}{18} $$

Expandindo em frações parciais tem-se:

$$\frac{H(z)}{z}=\frac{A}{z+\frac{1}{3}}+\frac{B}{z-\frac{1}{2}}$$




