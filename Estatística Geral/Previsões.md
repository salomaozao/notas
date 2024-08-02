Vale lembrar, antes de começar, que todo modelo que foi ajustado `aov()` tem como classes:
```
	class(mod)
## "lm", "aov"
```

`methods("predict")` Tem como output todos os  métodos de um

Vamos iniciar nossa discussão mostrando como construir um intervalo de confiança de $100(1-\alpha)\%$ para a resposta média, dado um valor $x_0$, que denoratemos por $\mu_{y_{0}|x_{0}}$.

Dado que $\mu_{y_{0}|x_{0}} = E(y_{0}|x_{0}) = \beta_{0} + \beta_{1}x_{0}$, segue o estimador pontual para $\mu_{y_{0}|x_{0}}$, que é a média, que é o mesmo estimador para $\hat{y}$: $$\begin{eqnarray}
    \hat{\mu}_{y_{0}|x_{0}} = \hat{y}=\hat{\beta_{0}} + \hat{\beta_{1}}x_{0} \nonumber
\end{eqnarray}$$
Isso se dá por que estamos **modelando a média**, uma vez que $$y \sim N(\beta_{0} + \beta_{1}x_{0})$$
Logo, temos também as seguintes propriedades:
$$E(\hat{\mu}_{y_{0}|x_{0}}) = \beta_{0} + \beta_{1}x_{0}$$$$ V(\widehat{\mu}_{y_{0}|x_{0}}) = \sigma^2\left( \frac{1}{n} + \frac{(x_{0}-\bar{x})^2}{S_{xx}} \right)$$
Onde, uma vez que temos a média e variância:
$$\begin{eqnarray}
    \hat{\mu}_{y_{0}|x_{0}} \sim N\left(\beta_{0} + \beta_{1}x_{0};\sigma^2\left[ \frac{1}{n} + \frac{(x_{0}-\bar{x})^2}{S_{xx}}\right] \right).    \nonumber
\end{eqnarray}$$$$\begin{eqnarray}
        IC[\mu_{y_{0}|x_{0}};100(1-\alpha)\%] = \hat{\mu}_{y_{0}|x_{0}} \pm t_{(n-2; \frac{\alpha}{2})}\sqrt{QMRes\left(\frac{1}{n} + \frac{(x_{0}-\bar{x})^2}{S_{xx}} \right)}. \nonumber
    \end{eqnarray}$$
TODO: completar com execução em código