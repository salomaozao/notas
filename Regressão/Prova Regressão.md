## O que vai cair:

1. Saber derivar a expressão do intervalo de confiança de, ou mais possívelmente do código, explicado em [[2. Inferências]]:
	Utilizando novamente o fato de que combinações lineares de variáveis aleatórias normalmente distribuidas também seguem uma distribuição normal, é possível mostrar que:
	  $$\hat{y}_{i} \sim N\left(\beta_{0}  + \beta_{i}x_{i};\left[\frac{1}{n}+ \frac{(x_{i}-\bar{x})^2}{Sxx}\right]\sigma^2\right)$$
	
	Se $\sigma^{2}$ for conhecido, temos como **intervalo de confiança** para $\beta_0$ e $\beta_1$ **com $\sigma$ conhecido**:
	
	$$\begin{eqnarray}
			IC(\beta_{0};100(1-\alpha)\%) = \hat{\beta}_{0} \pm z_{1-\alpha/2}\sqrt{\sigma^2\left(\frac{1}{n}+\frac{\bar{x}^2}{S_{xx}}\right)} \nonumber
		\end{eqnarray}$$
	e:
	$$
	\begin{eqnarray}
			IC(\beta_{1};100(1-\alpha)\%) = \hat{\beta}_{1} \pm z_{1-\alpha/2}\sqrt{\frac{\sigma^2}{S_{xx}}}. \nonumber
		\end{eqnarray}$$
		Além disso, podemos obter um estimador não viciado para $\sigma^{2}$:
	$$
	\begin{eqnarray}
	        \hat{\sigma}^2 =  \frac{\sum_{i=1}^{n}(y_{i}-\hat{y}_{i})^2}{n-2}    \nonumber
	    \end{eqnarray} 
	
	$$
	Então, temos que, **com $\sigma$ desconhecido**:
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
	   Onde seguimos as equações anteriories, mas utilizamos t para inferir já que a variância é desconhecida
	 de confiança e **usá-lo**   
2. . Método dos Mínimos Quadrados
	- As somas dos quadrados serão dadas.

3. Provar $\sum_{i=1}^{n}(y_{i}-\bar{y})^2 = \sum_{i=1}^{n}(\hat{y}_{i}-\bar{y})^2 + \sum_{i=1}^{n}(y_{i}-\hat{y}_{i})^2$ dadas as propriedades da reta ajustada, em [[Regressão Linear Simples]]


## Exercícios:
[[Exercício - Modelo de Regressão]]

![[Pasted image 20240810152354.png]]

