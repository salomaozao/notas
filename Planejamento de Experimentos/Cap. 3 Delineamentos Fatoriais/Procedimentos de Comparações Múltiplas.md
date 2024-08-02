#estatística #estatística_geral #material_p2_geral #planex
caso $H_0:τ_1=⋯=τ_a$ seja rejetida na ANOVA, o próximo passo consiste em verificarmos ==quais níveis do fator de interesse apresentam diferenças estatisticamente significativas==

![Untitled](Untitled%201.png)

# métodos de comparações múltiplas

##  da mínina diferença significativa de Fisher (*LSD ou MDS*):

- **Se $MDS = 0$, as variâncias não são iguais** evocê não pode fazer teste de variância
$E_i \approx^{i.i.d} N(u, sd²)$
- é fixo para todos os pares de média

O teste da mínima diferença significativa de Fisher **controla apenas a probabilidade de se cometer o erro do tipo I por comparação de pares de média**, que cresce junto com o número de pares de médias sendo comparados

![Untitled](Untitled%202.png)

Dada a estatística de tese para teste de hipóteses entre duas médias, temos que s² está senndo estimado por QMRES

![Untitled](Untitled%203.png)

![Untitled](Untitled%204.png)

```r
library(agricolae)

# saída 1:
lsd1 <- LSD.test(mod, "concentracao", group=TRUE)
print(lsd1)
```

```r
## $statistics
##    MSerror Df     Mean       CV  t.value      LSD
##   6.508333 20 15.95833 15.98628 2.085963 3.072423
## 
## $parameters
##         test p.ajusted       name.t ntr alpha
##   Fisher-LSD      none concentracao   4  0.05
## 
## $means
##    resistencia      std r     se       LCL      UCL Min Max   Q25  Q50   Q75
## 10    15.66667 2.804758 6 1.0415 13.494136 17.83920  12  19 13.50 16.0 17.75
## 15    17.00000 1.788854 6 1.0415 14.827469 19.17253  14  19 16.25 17.5 18.00
## 20    21.16667 2.639444 6 1.0415 18.994136 23.33920  18  25 19.25 21.0 22.75
## 5     10.00000 2.828427 6 1.0415  7.827469 12.17253   7  15  8.25  9.5 10.75
## 
## $comparison
## NULL
## 
## $groups
##    resistencia groups
## 20    21.16667      a
## 15    17.00000      b
## 10    15.66667      b
## 5     10.00000      c
## 
## attr(,"class")
## [1] "group"
```

Não existe diferença significativa entre os pares de médias do mesmo grupo

Este output será possívelmente dado na prova!

## Teste com Correção de Bonferroni

O teste com correção de Bonferroni controla tanto a probabilidade de cometermos um erro do tipo I por comparação quanto a probabilidade de erro global, isto é a probabilidade de cometermos pelo menos um erro do ipo I. ==Esse procedimento de comparações múltiplas corresponde ao procedimento mais conservador== existente

![P(Erro 1) ≤ alpha’ que é menor que alpha, assim sendo um teste bem conservador, que é afirmar que a diferença é significativa](Untitled%205.png)

P(Erro 1) ≤ alpha’ que é menor que alpha, assim sendo um teste bem conservador, que é afirmar que a diferença é significativa

É fácil perceber a similaridade entre o teste da mínima diferença significativa de Fisher e o teste com correção de Bonferroni. Ambos os testes utilizam exatamente a mesma distribuição de referência, entrentando o teste da mínima diferença significativa de Fisher utiliza α no cálculo de MDS, enquanto o teste com correção de Bonferroni utiliza α′.

A probabilidade de cometer um erro do tipo 1 é alpha’ que é menor do que alpha - aumentando a conservação 

a eq. 3.8 é uma aproximação que assume independência

## Teste de Tukey

![Untitled](Untitled%206.png)

Trabalha com a dist. da diferença entre $Y_{max}$ e $Y_{min}$ 
é o mais usado
$q = \frac{|\bar{Y_i} - \bar{Y_j}|}{\sqrt{\frac{MS_{within}}{n}}}$
$q = \frac{|\bar{Y_i} - \bar{Y_j}|}{\sqrt{\frac{MS_{within}}{n}}}$




```r

# saída 1:
hsd1 <- HSD.test(mod, "concentracao", group=TRUE)
print(hsd1)

## RETORNO:
## $statistics
##    MSerror Df     Mean       CV      MSD
##   6.508333 20 15.95833 15.98628 4.122563
## 
## $parameters
##    test       name.t ntr StudentizedRange alpha
##   Tukey concentracao   4         3.958293  0.05
## 
## $means
##    resistencia      std r     se Min Max   Q25  Q50   Q75
## 10    15.66667 2.804758 6 1.0415  12  19 13.50 16.0 17.75
## 15    17.00000 1.788854 6 1.0415  14  19 16.25 17.5 18.00
## 20    21.16667 2.639444 6 1.0415  18  25 19.25 21.0 22.75
## 5     10.00000 2.828427 6 1.0415   7  15  8.25  9.5 10.75
## 
## $comparison
## NULL
## 
## $groups
##    resistencia groups
## 20    21.16667      a
## 15    17.00000      b
## 10    15.66667      b
## 5     10.00000      c
## 
## attr(,"class")
## [1] "group"
```

![Isso mostra que o LSD é mais conservador, o bonferroni é menos e o Tukey é um meio termo - O Bonferroni tem maior probabilidade de cometer erro tipo 1](Untitled%207.png)

Isso mostra que o LSD é mais conservador, o bonferroni é menos e o Tukey é um meio termo - O Bonferroni tem maior probabilidade de cometer erro tipo 1

## Teste de Dunnet

*para quando você tem grupo controle*

Em muitos experimentos, um dos tratamentos (o nível do fator de interesse) corresponde a um grupo de controle $a$, e o analista está interessado em comparar cada um dos demais $a−1$ tratamentos apenas com esse grupo de controle.

Suponha que o tratamento a é o controle e desejamos testar *$H_0:μ_i=μ_a$* versus $H_1:μ_i≠μ_a$, para $i=1,...,a−1$, sendo $μ_a$ a média da variável controle . O teste de Dunnett consiste em uma modificação do teste t usual. A hipótese $H_0:μ_i=μ_a$ é rejeitada se :

![Untitled](Untitled%208.png)

em que $d_α(a−1,ν)$ é um valor tabelado, a é o número de tratamentos, ν é o número de graus dos resíduos, e α é a probabilidade de erro global associada aos a−1 testes.

```r
library(multcomp)

# especificando concentração 20% como nível de referência:
saquinhos <- saquinhos %>%
  mutate(
    concentracao = relevel(concentracao, ref = "20")
  )

# conferindo:
levels(saquinhos$concentracao)
## [1] "20" "5"  "10" "15"

mod <- aov(resistencia ~ concentracao, data = saquinhos)
comp <- glht(mod, linfct = mcp(concentracao = "Dunnet"))
summary(comp)
## 
##   Simultaneous Tests for General Linear Hypotheses
## 
## Multiple Comparisons of Means: Dunnett Contrasts
## 
## 
## Fit: aov(formula = resistencia ~ concentracao, data = saquinhos)
## 
## Linear Hypotheses:
##              Estimate Std. Error t value Pr(>|t|)    
## 5 - 20 == 0   -11.167      1.473  -7.581  < 0.001 ***
## 10 - 20 == 0   -5.500      1.473  -3.734  0.00364 ** 
## 15 - 20 == 0   -4.167      1.473  -2.829  0.02703 *  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## (Adjusted p values reported -- single-step method)
```

- O pacote *agricolae* não possui testes de dunnet, então usamos este pacote.
- A variável tem que ser em fator.
- glht - significado
- - A função mcp  define a variável e o procedimento de comparações múltiplas
- `aov(resistencia ~ concentracao, data = saquinhos)` (var. resposta) ~ (var. pergunta)

