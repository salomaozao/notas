***Faz parte de [[Regressão]]***
$$\begin{eqnarray}
          \left\{\begin{array}{l}
      H_{0}: \beta_{0} = \beta_{00} \\
      H_{1}: \beta_{0} \neq \beta_{00}
      \end{array}\right.
      ~~ \mbox{   e   } ~~
      \left\{\begin{array}{l}
      H_{0}: \beta_{1} = \beta_{10} \\
      H_{1}: \beta_{1} \neq \beta_{10}
      \end{array}\right.
       \nonumber,
  \end{eqnarray}$$
  Geralmente, $\beta_{00}$ e $\beta_{10}$ são valores arbitrários, geralmente equivalentes à 0, logo, para inferência, temos os seguintes valores de teste:
  $$\begin{eqnarray}
      \frac{\hat{\beta}_{0}-\beta_{00}}{\sqrt{\hat{\sigma}^{2}\left(\frac{1}{n}+\frac{\bar{x}^2}{S_{xx}}\right)}} \sim t_{n-2}
      ~~ \mbox{   e   } ~~
      \frac{\hat{\beta}_{1}-\beta_{10}}{\sqrt{\frac{\hat{\sigma}^{2}}{S_{xx}}}} \sim t_{n-2}.   \nonumber
  \end{eqnarray}$$
```
  lm(vResposta ~ Fator, data = data)
```

Pergunta de prova: calcular intervalo de confiançã dado a saída de código

$\hat{\beta_0}$ é o intercepto
