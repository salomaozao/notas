 ![[Pasted image 20240810152114.png]]
1.  **Escreva a equação do modelo de regressão linear simples estimado para o problema. Quais os pressupostos são necessários para a realização de inferências sobre o modelo.**
	$y_i = \beta_0 + \beta_1 x_i + \epsilon_i$; Para que possamos realizar inferências sobre os dados, precisamos que: 
	- $E[\epsilon_i]=0$, ou seja, os dados não sãoww
2.  **Interprete os valores estimados dos coeficientes do modelo.**
	Dada a saida do código, temos:
	- $\hat{\beta_0}=-8.17 \rightarrow Var(\hat{\beta_0})=1.05$
	- $\hat{\beta_1}=0.73 \rightarrow Var(\hat{\beta_1}) = 0.05$
3.  **Construa um intervalo de 95% de confiança para $\beta_1$ e interprete-o no contexto do problema.**
	Para construir IC com dp desconhecido:
	*Dados:*
	```
	dilatacao = c(5,3,10,8,6,7,9,6,5)
	data = data.frame(temp, dilatacao)
	mod = lm(temp ~ dilatacao, data = data)
	anova(mod)
	```
	
	```
			Df Sum Sq Mean Sq F value Pr(>F)
	dilatacao 1 66.575 66.575 201.4 2.048e-06 ***
	Residuals 7 2.314 0.331
	```
		$t_{7, 1-0.005} = 3,499$
	- para calcular o erro padrão:
	$$
			\begin{eqnarray}
		        \hat{\sigma}^2 =  \frac{\sum_{i=1}^{n}(y_{i}-\hat{y}_{i})^2}{n-2} = \frac{SQRes}{n-2} = QMRes = \frac{0.331}{7}=0.04728   \nonumber
		    \end{eqnarray} 
	$$
	$$
	S_{xx} = (?)
	$$
	
	Ou, pegamos do enunciado onde Std. Error é o erro padrão
)
	$$
			\begin{eqnarray}
	            IC(\beta_{1};100(1-\alpha)\%) = \hat{\beta}_{1} \pm t_{n-2; 1-\alpha/2}\sqrt{\frac{\hat{\sigma}^{2}}{S_{xx}}} = \hat{\beta}_{1} \pm t_{n-2; 1-\alpha/2}\text{EP(}\hat{\beta_0})
			\end{eqnarray}
	$$
	$$
	\text{Intervalo: }[ 0.7323 \pm 2,365 *0.0516 = [0.685893, 0.778707]
	$$
	Como o intervalo está contido após o $0$, concluimos que há uma relação linear positiva entre a temperatura e a dilatação linear do metal
4.  **Quais são as hipóteses e conclusões obtidas afd partir da estatística de teste e p-valor apresentados. Considere  $\alpha=1\%$**
	Estamos testando para as seguintes hipóteses:
	$$
		\begin{eqnarray}
	          \left\{\begin{array}{l}
	      H_{0}: \beta_{0} = 0 \\
	      H_{1}: \beta_{0} \neq 0
	      \end{array}\right.
	      ~~ \mbox{   e   } ~~
	      \left\{\begin{array}{l}
	      H_{0}: \beta_{1} = 0 \\
	      H_{1}: \beta_{1} \neq 0
	      \end{array}\right.
	       \nonumber,
	  \end{eqnarray}
	$$
	Dados os p-valores dados e assumindo $\alpha=1\%$ , podemos concluir o seguinte:
	- Rejeitamos H0H_0H0​ para $\beta_1$​, indicando que a temperatura tem um efeito significativo na dilatação linear do metal. Em termos práticos, isso significa que **a dilatação do metal é afetada pela temperatura**
	- Rejeitamos $H_0$ para $\beta_0$​, indicando que o valor da dilatação linear quando a temperatura é zero é significativamente diferente de zero. Isso sugere uma **dilatação de base independente da temperatura**.