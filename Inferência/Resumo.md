- **Equação do modelo:  $y_i = \beta_0 + \beta_1 x_i + \epsilon_i$**, onde $\epsilon \sim N(0, \sigma^2)$
 - $\hat{\sigma}^2 =  \frac{\sum_{i=1}^{n}(y_{i}-\hat{y}_{i})^2}{n-2} = \frac{SQRes}{n-2} = QMRes$

### **Distribuições e Intervalos de Confiança:** $\text{IC}(\beta, 100(1-\alpha)\%)=[\text{Estimador} \pm t_{n-2; 1-\alpha/2} * \text{EP}(\beta)]$
onde $\text{EP}(\beta) = \text{dp}(\beta) = \sqrt{\text{Var}(\beta)}$
- $\hat{\beta}_{0} \sim N\left(\beta_{0}; \sigma^2\left[\frac{1}{n}+\frac{\bar{x}^2}{S_{xx}}\right] \right)$, *logo*, $IC(\beta_{0};100(1-\alpha)\%) = [\hat{\beta_0} \pm t_{n-2; 1-\alpha/2} *\sqrt{\hat\sigma^2(\frac{1}{n} + \frac{x^2}{S_{XX}}})]$
-  $\hat{\beta}_{1} \sim N\left(\beta_{1};\frac{\sigma^{2}}{S_{xx}}\right)$, logo $IC(\beta_{1};100(1-\alpha)\%)=[\hat{\beta_1} \pm t_{n-2; 1-\alpha/2} *\sqrt{ \frac{\sigma^2}{S_{XX}} }]$
- $\hat{y}=\hat{\mu}_{y_{0}|x_{0}} \sim N\left(\beta_{0} + \beta_{1}x_{0};\sigma^2\left[ \frac{1}{n} + \frac{(x_{0}-\bar{x})^2}{S_{xx}}\right] \right) \Rightarrow IC[\mu_{y_{0}|x_{0}};100(1-\alpha)\%] = \hat{\mu}_{y_{0}|x_{0}} \pm t_{(n-2; \frac{\alpha}{2})}\sqrt{\hat{\sigma}^2\left(\frac{1}{n} + \frac{(x_{0}-\bar{x})^2}{S_{xx}} \right)}$ 

### **Testes de Hipótese:** $\frac{\hat{\beta} - \beta}{EP(\beta)}$

>$$\frac{\hat{\beta}_{0}-\beta_{0}}{\sqrt{\hat{\sigma}^{2}\left(\frac{1}{n}+\frac{\bar{x}^2}{S_{xx}}\right)}} \sim t_{n-2}  \Rightarrow\{\begin{array}{l}      H_{0}: \beta_{0} = 0 \\	      H_{1}: \beta_{0} \neq 0	      \end{array}$$  
	**Hipótese nula**: a variação de **Y** não possuí variação independente de **X**

>$$\frac{\hat{\beta_1}-\beta_1}{\sqrt{\frac{\sigma^2}{S_{XX}}}}  \sim t_{n-2} \Rightarrow  \{\begin{array}{l}      H_{0}: \beta_{1} = 0 \\	      H_{1}: \beta_{1} \neq 0	      \end{array}$$
	**Hipótese nula**: **Y** não possuí relação linear com **X**

- Diferença de saídas: Podemos obter `anova(mod)` que é a tabela da anova, o p valor é referente aos testes para $\beta_1$. O `summary(mod)` dá dois p valores, onde podemos inferir para ambos $\beta$.
### **Tabelas**

| **ANOVA** | Valor                                   | *g.l.* |
| --------- | --------------------------------------- | ------ |
| SQTotal   | SQReg+SQRes                             | n-1    |
| SQReg     | $\sum_{i=1}^{n}(\hat{y}_{i}-\bar{y})^2$ | 1      |
| SQRes     | $\sum_{i=1}^{n}(y_{i}-\hat{y}_{i})^2$   | n-2    |

| **Regressão** | Estimate        | Std. Error                                               | T value                                                                              |
| ------------- | --------------- | -------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| X             | $\hat{\beta_1}$ | $\frac{\hat{\sigma}^2}{S_{XX}}$                          | $\frac{\hat{\beta_1}-\beta_1}{\frac{\hat{\sigma}^2}{S_{XX}}}$                        |
| Y             | $\hat{\beta_0}$ | $\hat{\sigma^2}(\frac{1}{n}\frac{\overline{x}}{S_{XX}})$ | $\frac{\hat{\beta_0}-\beta_0}{\hat{\sigma}(\frac{1}{n}\frac{\overline{x}}{S_{XX}})}$ |
