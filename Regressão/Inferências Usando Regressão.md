Então, temos as hipóteses:
$$
\begin{eqnarray}
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
  \end{eqnarray}
$$



**Pode cair na prova:** Provar $\sum_{i=1}^{n}(y_{i}-\bar{y})^2 = \sum_{i=1}^{n}(\hat{y}_{i}-\bar{y})^2 + \sum_{i=1}^{n}(y_{i}-\hat{y}_{i})^2$ dadas as propriedades da reta ajustada, em [[Regressão Linear Simples]]

Lembrando que $x_i$ é a covariável
Para que a regressão linear seja significativa, precisamos que beta 1 for diferente de 0, para que haja contriubuição de $x_i$, dado  $y_i =\beta_0+\beta_1 x_i + e$ se torne 
$y_i = \beta$

se beta 1 = 0 => y chapéu ~y barra
então a equação acima do 22 tem a variação em cima da segunda soma basicamente 

para testar a significância da regressão:
$$
\begin{eqnarray}
      {
                 \left\{\begin{array}{lcc}
      H_{0}: \beta_{1} = 0 \\
      H_{1}: \beta_{1} \neq 0
      \end{array}\right.
      }    \nonumber
  \end{eqnarray}
$$


```
# ajustando o modelo:
mod <- lm(pureza ~ percentual, data = pureza)

# verificando a classe do objeto mod:
class(mod)
```

```
[1] "lm"
```
***
```
# extraíndo um sumário do modelo ajustado:
summary(mod)
```

```
Call:
lm(formula = pureza ~ percentual, data = pureza)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.83029 -0.73334  0.04497  0.69969  1.96809 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)   74.283      1.593   46.62  < 2e-16 ***
percentual    14.947      1.317   11.35 1.23e-09 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 1.087 on 18 degrees of freedom
Multiple R-squared:  0.8774,    Adjusted R-squared:  0.8706 
F-statistic: 128.9 on 1 and 18 DF,  p-value: 1.227e-09
```
***
```
anova(mod)
```

```
Analysis of Variance Table

Response: pureza
           Df Sum Sq Mean Sq F value    Pr(>F)    
percentual  1 152.13 152.127  128.86 1.227e-09 ***
Residuals  18  21.25   1.181                      
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```
***
```
tab_anova(mod)
```

```
Analysis of Variance Table 

      Df   Sum Sq  Mean Sq  F value    Pr(>F)    
Model  1 152.1271 152.1271 128.8617 1.227e-09 ***
Error 18  21.2498   1.1805                       
Total 19 173.3769                                
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

$\beta_0$ é o intercepto
VAi cair na prova construir o intervalo de confiança com base na saida do R