**Se $a$ níveis do fator de interesse $a$ são selecionados aleatoriamente de um grupo maior, então dizemos que o fator é um fator aleatório**

Temos que para delineamentos com um fator aleatório, seguimos o mesmo modelo linear:   
$$
Y_{ij}=\mu+\tau_{i}+\epsilon_{ij}
$$

Aqui, os efeitos dos tratamentos $τ_i$ e os erros $ϵ_{ij}$ são variáveis aleatórias independentes onde, $\tau_{i} \overset{\text{i.i.d.}}\sim N(0;\sigma_{\tau}^2)$ e $\epsilon_{ij} \overset{\text{i.i.d.}}\sim N(0;\sigma^2)$

as variâncias $\sigma_{\tau}^2$ e $\sigma^2$ são chamadas de componentes de variância.
Note que, ao assumirmos $\tau_{i} \overset{\text{i.i.d.}}{\sim} N(0;\sigma_{\tau}^2)$, a suposição usual de $\displaystyle \sum_{i=1}^{a}\tau_{i}=0$ dos modelos de efeitos fixos não se aplica ao modelo de efeitos aleatórios.

### Teste de hipóteses para delineamentos com fatores aleatórios:
$$
\begin{eqnarray}
    {
               \left\{\begin{array}{lcc}
    H_{0}: \sigma_{\tau}^{2}=0 \\
    H_{1}: \sigma_{\tau}^{2}>0
    \end{array}\right.
    }  .  \nonumber
\end{eqnarray}
$$
Onde $\sigma_{\tau}^{2}$ é a variância do fator aleatório, segue que: 
$$
    F_{0}=\frac{QMTrat}{QMRes} \sim F_{a-1;a(n-1)},  \nonumber
$$
Se rejeitarmos a hipótese nula de que a variância do fator aleatório é zero, concluímos que o fator aleatório tem um efeito significativo na variabilidade dos dados. A diferença é que, após rejeitar $H_0$, não fazemos testes de comparação múltipla, pois com a ANOVA temos como objetivo entender a variabilidade introduzida pelo fator aleatório. Em vez disso, temos como objetivo estimar $\sigma_{\tau}^{2}$
$$
    \hat{\sigma}_{\tau}^2=\frac{QMTrat-QMRes}{n}
$$
### Código de exemplo: 
# Etapas para delineamentos com fator aleatório

**Uma companhia têxtil tece um tecido em um grande número de teares. A companhia está interessada na variabilidade da resistência à tensão que ocorre entre os teares. Para investigar tal variabilidade, um engenheiro seleciona, aleatoriamente, 4 teares e faz 4 determinações de resistências nas amostras de tecido, escolhidas ao acaso, provenientes de cada tear.**

```{r}
library(planex)
library(tidyverse)

data(teares)

sapply(teares, class)
```
```{r}
# explorando graficamente:
ggplot(teares, aes(x = tear, y = resistencia)) +
  geom_boxplot()

# obtendo a média e o desvio padrão para cada tear selecionado:
teares %>%
  group_by(tear) %>%
  summarise(
    media = mean(resistencia),
    dp = sd(resistencia)
  )
```

Pela análise gráfica e olhando as médias e variâncias, podemos observar que as médias tem uma diferença significativa entre elas. Agora, vamos fazer a análise de variância (ANOVA)
```{r}
mod <- aov(resistencia~tear, data=teares)
summary(mod)
```
Podemos observar que o p-valor é menor $10^{-4}$, então, rejeitamos $H_0$.

# Exemplo:

```{r}
library(planex)
df = moinho
View(teares)
```

1.  Primeiro, como sempre, fazemos a ANOVA

```{r}
moinho = moinho %>% mutate(tear = as.factor(tear))

model = aov(producao~tear, data = moinho)
tab = summary(model)
tab
```

```
            Df Sum Sq Mean Sq F value  Pr(>F)   
tear         4 0.3416  0.0854    5.77 0.00296 **
Residuals   20 0.2960  0.0148                   
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```



Dado o pvalor, podemos rejeitar $H_0$. Agora, estimaremos $\hat{\sigma}_{\tau}^2$, que é a variância do fator aleatório, expressado por $$\hat{\sigma}_{\tau}^2=\frac{QMTrat-QMRes}{n}$$

```{r}
QMTrat = tab[[1]]$"Mean Sq"[1]
QMRes = tab[[1]]$"Mean Sq"[2]
n=5
var = (QMTrat-QMRes)/n
var
```

```
[1] 6.958333
```
