# 1. ==ANOVA== - Análise de Variância
```
algodao = mutate(algodao, percentual = as.factor(percentual))


algodao %>%
  group_by(percentual) %>%
  summarise(
    media = mean(resistencia),
    dp = sd(resistencia)
  )

model = aov(resistencia ~ percentual, data=algodao)
summary(model)

OUTPUT:
            Df Sum Sq Mean Sq F value   Pr(>F)    
percentual   4  475.8  118.94   14.76 9.13e-06 ***
Residuals   20  161.2    8.06                     
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

```

$$    {
               \left\{\begin{array}{lcc}
    H_{0}: \mu_{1}=\mu_{2}=\dots=\mu_{a} \\
    H_{1}: \mu_{i}\neq \mu_{i'} \mbox{ para pelo menos um par (i,i')}
    \end{array}\right.
    }
$$
$$
F_{0} = \frac{QMTrat}{QMRes} = \frac{SQTrat/(a-1)}{SQRes/a(n-1)} \sim F_{a-1; a(n-1)}
$$
Rejeitamos se $Pr(>F)$, que é o p-valor, for menor que $\alpha$
$QMTrat$: **Média dos quadrados do tratamento** - mede a variabilidade entre as médias
$QMRes$: **Média dos quadrados dos resíduos** - mede a variabilidade entre os níveis
$SQTotal$: Variabilidade total presente nos dados

# ==2. Análise de Resíduos==
Por definição, um resíduo é a diferença entre a observação $y_{ij}$ e o seu valor estimado (ou ajustado) $y_{ij}$, obtido a partir do modelo estatístico sendo estudado, isto é,
$$
      e_{ij}=y_{ij}-\hat{y}_{ij}
$$
As conclusões obtidas na ANOVA partem da suposição que $\epsilon_{ij} \overset{\text{i.i.d.}}{\sim} N(0, \sigma^2)$, o que implica de **erros independentes** e **normalmente distribuidos**, e variância comum entre todos os níveis, o que pode ser indentificado por testes ou análise gráfica
1. **Análise Gráfica:**
```
mod <- aov(resistencia ~ concentracao, data = saquinhos)
plotResiduals(mod) # Explorando os resíduos graficamente:
```
![[Etapas para Delineamentos fatoriais-20240721182034155.webp|500]]![[Etapas para Delineamentos fatoriais-20240721182155600.webp|500]]![[Etapas para Delineamentos fatoriais-20240721182242835.webp|500]]
Usando os gráficos retornados pelo código, podemos ver se os dados estão uniformemente distribuidos, se não tem muitos outliers e etc.
2. **Análise "Formal":**
```
# testando formalmente as suposições sobre os erros:
testResiduals(mod)
```

```
## 
##  Shapiro-Wilk normality test
## 
## data:  resid
## W = 0.96624, p-value = 0.5757
## 
## ------------------------------------------ 
## Bartlett test of Homogeneity of Variances: 
##              Bartlett's K-squared df   p.value
## concentracao             1.135246  3 0.7685731
## 
## ----------------------------------------------- 
## Durbin-Watson Test for Autocorrelated Errors: 
##  lag Autocorrelation D-W Statistic p-value
##    1      -0.1303884      2.181178   0.874
##  Alternative hypothesis: rho != 0
```
- **Shapiro-Wilk:** Testar a hipótese nula de que os resíduos seguem uma distribuição normal
- **Bartlett test:** Testar a hipótese nula de que as variâncias dos grupos são iguais.
- **Teste de Durbin-Watson:** Testar a hipótese nula de que não há autocorrelação nos resíduos

Dada a hipótese dos testes, usar o p-valor para conferir normalidade
# ==Comparação Múltipla:==
***Fazer apenas se rejeitar $H_0$ da ANOVA!***
Se for **fator aleatório**, após rejeitar H0, fazemos um estimador para $\sigma_{\tao}^2$
Se a ANOVA testa se todas as médias são iguais, ou pelo menos uma é diferente, os testes de comparação múltipla servem apenas para saber se as médias entre um nível e outro, de um fator, tem a mesma média. Seguem as hipóteses.
$$
    {
               \left\{\begin{array}{lcc}
    H_0​:μ_i​=μ_j \\
    H_0​:μ_i​\neq μ_j 
    \end{array}\right.
    }
$$
- **Se $MDS = 0$, as variâncias não são iguais** você não pode fazer teste de variância $E_i \approx^{i.i.d} N(u, sd²)$
![Isso mostra que o LSD é mais conservador, o bonferroni é menos e o Tukey é um meio termo - O Bonferroni tem maior probabilidade de cometer erro tipo 1](Untitled%207.png)
## Testes que fazem parte do pacote Agricolae
```
LSD.test(model, "percentual", group = FALSE)  # LSD
LSD.test(model, "percentual", p.adj="bonferroni", group=FALSE)  # Bonferroni
HSD.test(model, "percentual", group=TRUE)  # Tukey
```

```
$statistics
  MSerror Df  Mean       CV  t.value      LSD
     8.06 20 15.04 18.87642 2.085963 3.745452

$parameters
        test p.ajusted     name.t ntr alpha
  Fisher-LSD      none percentual   5  0.05

$means
   resistencia      std r       se       LCL      UCL Min Max Q25 Q50 Q75
15         9.8 3.346640 5 1.269646  7.151566 12.44843   7  15   7   9  11
20        15.4 3.130495 5 1.269646 12.751566 18.04843  12  18  12  17  18
25        17.6 2.073644 5 1.269646 14.951566 20.24843  14  19  18  18  19
30        21.6 2.607681 5 1.269646 18.951566 24.24843  19  25  19  22  23
35        10.8 2.863564 5 1.269646  8.151566 13.44843   7  15  10  11  11

$comparison
        difference pvalue signif.         LCL        UCL
15 - 20       -5.6 0.0054      **  -9.3454518 -1.8545482
15 - 25       -7.8 0.0003     *** -11.5454518 -4.0545482
15 - 30      -11.8 0.0000     *** -15.5454518 -8.0545482
15 - 35       -1.0 0.5838          -4.7454518  2.7454518
20 - 25       -2.2 0.2347          -5.9454518  1.5454518
20 - 30       -6.2 0.0025      **  -9.9454518 -2.4545482
20 - 35        4.6 0.0186       *   0.8545482  8.3454518
25 - 30       -4.0 0.0375       *  -7.7454518 -0.2545482
25 - 35        6.8 0.0012      **   3.0545482 10.5454518
30 - 35       10.8 0.0000     ***   7.0545482 14.5454518
```
`Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1`
Conseguimos **agrupar** os níveis de fatores, pelo nível de confiança. Uma vez que estamos medindo se uma média e outra são iguais, podemos inferir o seguinte, apenas com a seção `$comparison`, comparando os p-valores:
- Os fatores 20 e 25 tem uma diferença muito pouco significativa, assim como os fatores 15 e 35.
- Os fatores com diferença mais significativa são 30 e 35 e 15 e 30.

## Teste de Dunnet:
```
comp <- glht(model, linfct = mcp(percentual = "Dunnet"))
summary(comp)
```

```
 Simultaneous Tests for General Linear Hypotheses

Multiple Comparisons of Means: Dunnett Contrasts


Fit: aov(formula = resistencia ~ percentual, data = algodao)

Linear Hypotheses:
             Estimate Std. Error t value Pr(>|t|)    
20 - 15 == 0    5.600      1.796   3.119  0.01841 *  
25 - 15 == 0    7.800      1.796   4.344  0.00112 ** 
30 - 15 == 0   11.800      1.796   6.572  < 0.001 ***
35 - 15 == 0    1.000      1.796   0.557  0.94691    
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
(Adjusted p values reported -- single-step method)====
```