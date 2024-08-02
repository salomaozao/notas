***Cap. 2 de [[Regressão]]***

Quando ajustamos um modelo de regressão linear simples, estamos basicamente interessados em verificar se a variação da variável resposta $y$ pode ser parcialmente explicada pela [[Covariável]] $x$, e fazer previsões, isto é, determinar o valor de uma nova observação $y_0$, dada uma covariável $x_0$.

``` 
library(reglin)
library(tidyverse)
library(ggpubr)

ggplot(pureza, aes(x=percentual, y=pureza)) +
  geom_point() +
  geom_smooth(method = "lm", se = FALSE)  
```
![[Pasted image 20240711081238.png]]

- Modelo teórico: $y_i = \beta_0 + \beta_1x_i + \epsilon_i$
- Modelo ajustado: $y_i = \beta + \beta_1x_i$ tudo sobre chapéu

se $E[\epsilon_i] = 0$ e $V(\epsilon_i) = dp²$
 dado que x é variável explicativa, e não VA, então: $$\begin{eqnarray}
        E(y_{i}|x_{i}) &=& E(\beta_{0}+\beta_{1}x_{i} + \epsilon_{i}) \nonumber \\
                       &=& \beta_{0}+\beta_{1}x_{i} + E(\epsilon_{i}) \nonumber \\
                       &=& \beta_{0}+\beta_{1}x_{i} \nonumber
    \end{eqnarray}$$
em que o intercepto $\beta_0$ e o coeficiente de inclinação da reta $\beta_1$ acima são chamados coeficientes da regressão. Temos também: $$\begin{eqnarray}
        V(y_{i}|x_{i}) &=& V(\beta_{0}+\beta_{1}x_{i} + \epsilon_{i}) \nonumber \\
                       &=& V(\epsilon_{i})  \nonumber \\
                       &=& \sigma^{2}.
    \end{eqnarray}$$
    segue então que $y_{i} \overset{\text{indep}}{\sim} N(\beta_{0}+\beta_{1}x_{i};\sigma^2)$, então, **para cada ponto x, há uma curva da normal no gráfico, tendo a mesma dispersão pra cima e pra baixo na reta oara cada ponto x**
(Ver [[Probabilidade Condicional]])
## 2.1 [Estimação de parâmetros](https://www.est.ufmg.br/~fndemarqui/bookReg/RegSimples.html#estimação-de-parâmetros)
### Equação da reta: $$\hat{y} = \hat{\beta}_{0} +\hat{\beta}_{1}x + e_i$$
- $\hat{\beta}_{0}$: variável do intercepto (?)
- $\hat{\beta}_{1}$: coef. angular
- $e_i$: erro padrão, presente apenas na reta não ajustada
### Como determinar $\beta_0$ e $\beta_1$?
Uma possível maneira de se responder essa pergunta consiste em encontrarmos uma reta ajustada $\hat{y} = \hat{\beta}_{0} +\hat{\beta}_{1}x$ tal que a distância entre cada ponto $(x_{i},y_{i})$ e a reta ajustada $\hat{y}$ seja mínima.
![[Pasted image 20240711082830.png]]

Usando o **Método dos Mínimos Quadrados**: $$\begin{eqnarray}
        S(\beta_{0},\beta_{1}) = \sum_{i=1}^{n}\epsilon^{2} = \sum_{i=1}^{n}(y_{i} - \beta_{0} - \beta_{1}x_{i})^2. \nonumber
    \end{eqnarray}$$
    É fácil provar assim, que: $$\begin{eqnarray}
  \hat{\beta_{0}} = \bar{y} - \hat{\beta_{1}}\bar{x} \nonumber
\end{eqnarray}$$
    e: $$\begin{eqnarray}
  \hat{\beta_{1}} &=& \frac{ \sum_{i=1}^{n}x_{i}y_{i} - \frac{ \left(\sum_{i=1}^{n}x_{i}\right)\left(\sum_{i=1}^{n}y_{i}\right) }{n} }
        {\sum_{i=1}^{n}x_{i}^{2} - \frac{\left(\sum_{i=1}^{n}x_{i}\right)^2}{n} }  \\ \nonumber
        &=& \frac{\sum_{i=1}^{n}(x_{i}-\bar{x})y_{i}}{\sum_{i=1}^{n}(x_{i}-\bar{x})^2} \\ \nonumber
        &=& \frac{S_{xy}}{S_{xx}}.
\end{eqnarray}$$
	Dependendo do caso, podemos usar equações diferentes expressadas acima.
Algumas propriedades importantes dos estimadores de mínimos quadrados $\hat{\beta}_{0}$ e $\hat{\beta}_{1}$ são apresentadas a seguir:
-  $\hat{\beta}_{0}$ e $\hat{\beta}_{1}$ são combinações lineares dos $y_{i}'s$
-  $\hat{\beta}_{0}$ e $\hat{\beta}_{1}$ são estimadores não viciados para  $\hat{\beta}_{0}$ e $\hat{\beta}_{1}$ , isto é, $E(\hat{\beta}_{0}) = \beta_{0} ~ \mbox{ e } ~ E(\hat{\beta}_{1}) = \beta_{1}$
- $Var(\hat{\beta}_{1}) = Var(\sum{w_iy_i}) = \frac{\sigma^2}{S_{XX}}$
- Retomando, $E(z,w) = E[(Z-\mu_Z)(W-\mu_W)]$, temos, então: $COV(\hat{\beta}_{0}, \hat{\beta}_{1}) = \frac{-\bar{x}\sigma^{2}}{S_{xx}}$
- $$\begin{eqnarray}
  \hat{\beta}_{0} \sim N\left(\beta_{0}; \sigma^2\left[\frac{1}{n}+\frac{\bar{x}^2}{S_{xx}}\right] \right) ~ \mbox{ e } ~ \hat{\beta}_{1} \sim N\left(\beta_{1};\frac{\sigma^{2}}{S_{xx}}\right). \nonumber
\end{eqnarray}$$
A reta ajustada goza as seguintes propriedades:
- $\hat{y}_i$ é combinação linear dos $y^{'} _i$'s
- $\displaystyle \sum_{i=1}^{n}e_{i} = \sum_{i=1}^{n}(y_{i}-\hat{y}_{i})=0 \rightarrow \displaystyle \sum_{i=1}^{n}x_{i}e_{i} = \sum_{i=1}^{n}x_{i}(y_{i}-\hat{y}_{i})=0$
- $\displaystyle \sum_{i=1}^{n}y_{i} = \displaystyle \sum_{i=1}^{n}\hat{y}_{i}$
- $\displaystyle \sum_{i=1}^{n}\hat{y}_{i}e_{i} = \sum_{i=1}^{n}\hat{y}_{i}(y_{i}-\hat{y}_{i})=0$
- A reta ajustada sempre passa pelo ponto $(\bar{x}, \bar{y})$
- Utilizando novamente o fato de que combinações lineares de variáveis aleatórias normalmente distribuidas também seguem uma distribuição normal, é possível mostrar que:
  $$\hat{y}_{i} \sim N\left(\beta_{0}  + \beta_{i}x_{i};\left[\frac{1}{n}+ \frac{(x_{i}-\bar{x})^2}{Sxx}\right]\sigma^2\right)$$

Se $\sigma^{2}$ for conhecido, temos como **intervalo de confiança** para $\beta_0$ e $\beta_1$:

$$\begin{eqnarray}
            IC(\beta_{0};100(1-\alpha)\%) = \hat{\beta}_{0} \pm z_{1-\alpha/2}\sqrt{\sigma^2\left(\frac{1}{n}+\frac{\bar{x}^2}{S_{xx}}\right)} \nonumber
        \end{eqnarray}$$
	e
$$
	\begin{eqnarray}
            IC(\beta_{1};100(1-\alpha)\%) = \hat{\beta}_{1} \pm z_{1-\alpha/2}\sqrt{\frac{\sigma^2}{S_{xx}}}. \nonumber
        \end{eqnarray}
$$Além disso, podemos obter um estimador não viciado para $\sigma^{2}$:
$$
\begin{eqnarray}
        \hat{\sigma}^2 =  \frac{\sum_{i=1}^{n}(y_{i}-\hat{y}_{i})^2}{n-2}    \nonumber
    \end{eqnarray} 

$$
Então, temos que:
$$
\begin{eqnarray}
        \frac{\hat{\beta}_{0}-\beta_{0}}{\sqrt{\hat{\sigma}^{2}\left(\frac{1}{n}+\frac{\bar{x}^2}{S_{xx}}\right)}} \sim t_{n-2}  \nonumber
    \end{eqnarray}     
    \rightarrow 
    

            IC(\beta_{0};100(1-\alpha)\%) = \hat{\beta}_{0} \pm t_{n-2; 1-\alpha/2}\sqrt{\hat{\sigma}^{2}\left(\frac{1}{n}+\frac{\bar{x}^2}{S_{xx}}\right)} 

$$
e
$$
\begin{eqnarray}
        \frac{\hat{\beta}_{1}-\beta_{1}}{\sqrt{\frac{\hat{\sigma}^{2}}{S_{xx}}}} \sim t_{n-2}.  \nonumber
    \end{eqnarray}
    \rightarrow

            IC(\beta_{1};100(1-\alpha)\%) = \hat{\beta}_{1} \pm t_{n-2; 1-\alpha/2}\sqrt{\frac{\hat{\sigma}^{2}}{S_{xx}}}

$$