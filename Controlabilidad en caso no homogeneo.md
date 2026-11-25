## Caso con trayectoria variable: perfil $\bar K(s)$ y pendiente

Linealizamos a lo largo de una trayectoria con pendiente y energía cinética variable, en lugar de una de crucero.

**Trayectoria de referencia.** Sea $P\in C^1([0,S])$ arbitrario (por ejemplo, un "lomo de burro" cerca de las estaciones) y sea

$$
\bar K(s) = K_{\min} + (K_c - K_{\min})\sin^2\left(\frac{\pi s}{S}\right), \qquad K_{\min}=2,\quad K_c=60,\quad S=1000,
$$

que es de clase $C^\infty$ y cumple $\bar K(s)\ge K_{\min}>0$.

**Sistema linealizado.** Con $x=(E,t,J)^\top$ obtenemos las matrices

$$
A(s)=\left(\begin{array}{ccc}
-\lambda(s) & 0 & 0 \\
-\kappa(s) & 0 & 0 \\
0 & 0 & 0
\end{array}\right), \qquad
B=\left(\begin{array}{cc}
1 & -1 \\
0 & 0 \\
1 & -\alpha
\end{array}\right)
$$

con

$$
\lambda(s)=w'(\bar K(s))=\frac{b}{2\sqrt{\bar K(s)}}+c, \qquad \kappa(s)=\bigl(2\bar K(s)\bigr)^{-3/2}>0.
$$

Ahora $A$ depende de $s$ y $B$ es constante. Con los valores anteriores.

**Criterio de controlabilidad.** Como $A$ no es constante, el criterio de Kalman del caso autónomo no aplica.

Para $\dot y = A(s)y + Bv$, el sistema es controlable en $[0,S]$ si y solo si el Gramiano

$$
W=\int_0^S \Phi(S,\sigma)\,BB^\top\,\Phi(S,\sigma)^\top\,d\sigma
$$

es definido positivo, donde $\Phi(s,\sigma)$ es la resolvente de $\dot y=A(s)y$.

Haciendo los cálculos obtenemos

$$
\Phi(S,\sigma)=\left(\begin{array}{ccc}
g_1(\sigma) & 0 & 0 \\
g_2(\sigma) & 1 & 0 \\
0 & 0 & 1
\end{array}\right)
$$

$$
g_1(\sigma)=e^{-\int_\sigma^S\lambda(r)\,dr}, \qquad g_2(\sigma)=-\int_\sigma^S\kappa(r)\,e^{-\int_\sigma^r\lambda}\,dr
$$

con $g_1>0$, $g_1'=\lambda g_1$ y $g_2'=\kappa+\lambda g_2$. Las columnas de $\Phi B$ son $\pm(g_1,g_2,1)^\top$ y $\pm(g_1,g_2,\alpha)^\top$, de modo que

$$
W=\int_0^S\bigl(v_1v_1^\top+v_2v_2^\top\bigr)\,d\sigma, \qquad v_1=(g_1,g_2,1)^\top,\quad v_2=(g_1,g_2,\alpha)^\top.
$$

Sea $\bar K\in C^0([0,S])$ con $\bar K>0$. Si $\alpha\neq1$, $W$ es definido positivo y el linealizado es controlable en $[0,S]$. Si $\alpha=1$, es controlable si y solo si $1,g_1,g_2$ son linealmente independientes en $[0,S]$.

**Interpretación física.** Para el subsistema $(E,t)$ con perturbación de fuerza neta $a=v_{\mathrm{tr}}-v_{\mathrm b}$, se tiene $y_1(S)=\int_0^S g_1 a\,d\sigma$ (energía final) e $y_2(S)=\int_0^S g_2 a\,d\sigma$ (tiempo de llegada), de modo que $g_1(\sigma)$ y $g_2(\sigma)$ miden la influencia de aplicar fuerza en la posición $\sigma$ sobre cada una. Que sean linealmente independientes significa que la posición donde se aplica la fuerza afecta de forma distinta a la energía y al tiempo (la fuerza tardía modifica la energía y casi no el tiempo, la temprana modifica más el tiempo), por lo que ambos se pueden corregir por separado. Como $(g_2/g_1)'=\kappa/g_1>0$, esta "tasa de cambio" varía estrictamente con $\sigma$ y nunca son proporcionales.
**Interpretación física.** Para el subsistema $(E,t)$ con perturbación de fuerza neta $a=v_{\mathrm{tr}}-v_{\mathrm b}$, se tiene $y_1(S)=\int_0^S g_1 a\,d\sigma$ (energía final) e $y_2(S)=\int_0^S g_2 a\,d\sigma$ (tiempo de llegada), de modo que $g_1(\sigma)$ y $g_2(\sigma)$ miden la influencia de aplicar fuerza en la posición $\sigma$ sobre cada una. Que sean linealmente independientes significa que la posición donde se aplica la fuerza afecta de forma distinta a la energía y al tiempo (la fuerza tardía modifica la energía y casi no el tiempo, la temprana modifica más el tiempo), por lo que ambos se pueden corregir por separado. Como $(g_2/g_1)'=\kappa/g_1>0$, esta "tasa de cambio" varía estrictamente con $\sigma$ y nunca son proporcionales.
