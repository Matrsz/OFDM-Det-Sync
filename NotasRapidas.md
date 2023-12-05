# Sincronismo {#notasrapidas-sincronismo}

Señal recibida en banda base modificada por canal

$$
y[m] = e^{j2\pi\Delta f m T_s}\sum_\ell x[m-\ell]h_\ell
$$

Preambulo

$$
x(t) = 
\left\{
\begin{aligned}
&s(t) \quad &0<t<T\\
&s(t-T) \quad &T < t<2T\\
&\vdots
\end{aligned}
\right. 
\quad \longrightarrow\quad
x[m] = x(mT_s) = 
\left\{
\begin{aligned}
&s[m] \quad & 0<m<M\\
&s[m-M] \quad &M < m<2M\\
&\vdots
\end{aligned}
\right.
$$

## Banco de Correladores {#notasrapidas-banco-de-correladores}

Vos ya conocés el preámbulo, vamos probando varios $\Delta f_i$

$$
\begin{aligned}
r_i[k] &= \sum_{m=0}^{M-1} s^\star[m]e^{-jw\pi\Delta f_i m T_s} y[m+k]\\
&\vdots\\
r_i[k] &= h_o e^{jw\pi\Delta f kT_s}\sum_{m=0}^{M-1} e^{jw\pi(\Delta f-\Delta f_i) m T_s} x[m+k]s^\star[m]
\end{aligned}
$$

En $k=0$

$$
\begin{aligned}
r_i[0] &= h_o \sum_{m=0}^{M-1} e^{jw\pi(\Delta f-\Delta f_i) m T_s} x[m]s^\star[m]\\
r_i[0] &= h_o \sum_{m=0}^{M-1} e^{jw\pi(\Delta f-\Delta f_i) m T_s} \left\lvert s[m]\right\rvert^2
\end{aligned}
$$

Se puede calcular que $|r_i[0]|$ es máximo cuando $\Delta f_i = \Delta f$, el max es $r_i[0]_{MAX}=h_0E_s$

## Delay and correlate {#notasrapidas-delay-and-correlate}

No asume conocer el preámbulo, pero si su longitud, parte de correlacionar la señal con su réplica desplazada en tiempo

$$
\begin{aligned}
r[k] &= \sum_{m=0}^{M-1}=y^\star[m+k]y[m+k+M]\\
r[k] &= e^{j2\pi \Delta f MT_s} \sum_{m=0}^{M-1} \{x\ast h\}[m+k] \{x\ast h\}[m+k+m]\\
r[k] &= |h_o|^2e^{j2\pi \Delta f MT_s} \sum_{m=0}^{M-1} x^\star[m]x[m+M]\\
\end{aligned}
$$

En $k=0$

$$
\begin{aligned}
r[0] &= |h_o|^2 e^{i2\pi\Delta f MT_s}\sum_{M=0}^{M-1}x^\ast[m]x[m+M]\\
r[0] &= |h_o|^2 e^{i2\pi\Delta f MT_s}\sum_{M=0}^{M-1}\left\lvert s[m]\right\rvert^2\\
\end{aligned}
$$

Entonces el $\Delta f = \dfrac{\angle r[0]}{2\pi M T_s}$ ya que ese hace que la autocorrelaciones sean reales.

Objetivos: Simular, entender, pensar en fase
