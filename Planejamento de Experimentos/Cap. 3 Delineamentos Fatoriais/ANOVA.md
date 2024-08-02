um delineamento completamente aleatorizado com um fator fixo temos o interesse em determinar se existem diferenças entre um número arbitrário $a$ de médias, $μ_1,⋯,μ_a.$

Podemos descrever as ==observações== de um delineamento completamente aleatorizado com um fator fixo utilizando seguinte modelo: $$Y_{ij} = \mu_{i} + \epsilon_{ij}$$
Que é o **modelo de médias**, que pode ser reparametrizado como o **modelo de efeitos**: $$Y_{ij} = \mu + \tau_{i}+ \epsilon_{ij}$$
para $j=1⋯,n_i$ e $i=1,⋯,a$.
Sumarizando, temos:
- $a$ é o **número de níveis** do fator de interesse;
- $n_i$ corresponde ao **número de replicações** (ou corridas) do experimento no nível i, i=1,⋯,a- ;
- $μ$ é a **média geral**, comum a todos os tratamentos;
- $τ_i$ representa o **[[Efeito]]** do i-ésimo tratamento;
- $μ_i=μ+τ_i$ é a **média** do í-ésimo tratamento;
- $ϵ_{ij}$é um componente estocástico associado à **variabilidade não explicada** inerente ao processo (erro aleatório).

1. Dizemos que um **delineamento é balanceado** se possuir o mesmo número de corridas para todos os níveis do fator de interesse, isto é, $n_1=n_2,⋯,n_a=n$ . Caso contrário, dizemos que o delineamento é desbalanceado.
    
2. Os modelos apresentados acima, assim como os demais modelos que estudaremos no nosso curso, pertencem à classe dos chamados modelos lineares. O método dos mínimos quadrados é, em geral, empregado para a estimação dos parâmetros de um modelo linear.


## Hipóteses de Interesse:
- Para um delineamento com o **modelo de médias**:
'

- Para um delineamento com o **modelo de efeitos**:
$$    {
               \left\{\begin{array}{lcc}
    H_{0}: \tau_{1}=\tau_{2}=\dots=\tau_{a}=0 \\
    H_{1}: \tau_{i}\neq 0 \mbox{ para pelo menos um i}
    \end{array}\right.
    }
    $$
Para fazermos [[Testes de Hipótese]], é necessário assumir que os erros $\epsilon_{ij} \overset{\text{i.i.d.}}{\sim} N(0;\sigma^2)$ sejam independentes
> [!NOTE] Note que:
> Se $H_0$ é verdade, então $y_{ij} \sim N(\mu;\sigma^{2})$


![[Pasted image 20240709191210.png]]
![[Pasted image 20240709191249.png]]

A soma de quadrados total ($SQ$) corrigida, dada por: $$    \sum_{i=1}^{a}\sum_{j=1}^{n}(y_{ij}-\bar{y})^2 = n\sum_{i=1}^{a}(\bar{y}_{i.}-\bar{y})^2 + \sum_{i=1}^{a}\sum_{j=1}^{n}(y_{ij}-\bar{y}_{i.})^2$$ $$SQTotal =  SQTrat + SQRes.$$
$SQTotal$: A **soma de quadrados total** ($\sum_{i=1}^{a}\sum_{j=1}^{n}(y_{ij}-\bar{y}_{..})^2$) mede a ==variabilidade total presente nos dados== em relação à média geral $\bar{y}_{..}$
***Grau de Liberdade: $an-1$***
- $y_{ij}$ é o valor observado no i-ésimo nível do fator e j-ésima repetição.
- $\bar{y}​$ é a média geral de todos os dados.
- $a$ é o número de níveis do fator.
- $n$ é o número de observações em cada nível do fator.


$SQTrat$: A **soma de quadrados do tratamento** ($n\sum_{i=1}^{a}(\bar{y}_{i.}-\bar{y}_{..})^2$) mede a ==variabilidade entre as médias== dos diferentes níveis do fator em relação à média geral. 
***Grau de Liberdade: $a-1$***
- $y^{ˉ​i}$.​ é a média das observações no i-ésimo nível do fator.
- $\bar{y}_{..}$​ é a média geral de todos os dados.
- $n$ é o número de observações em cada nível do fator.
	**Quadrado médio: **$QMTrat = \frac{SQTrat}{a-1} \rightarrow    E(QMTrat)=\sigma^2+\frac{n\sum_{i=1}^{a}\tau_{i}^{2}}{(a-1)}$
	- Supondo que $H_{0}: \tau_{i}=0, ~\forall ~ i=1, \cdots, a$, temos que $\frac{SQTrat}{\sigma^2} \sim \chi_{a-1}^2$

$SQRes$: A **soma de quadrados dos resíduos** $\sum_{i=1}^{a}\sum_{j=1}^{n}(y_{ij}-\bar{y}_{i.})^2$ mede a ==variabilidade dentro dos níveis== do fator, ou seja, a variabilidade das observações individuais em relação à média do seu nível específico. 
***Grau de Liberdade: $a(n-1)$***
- $y_{ij}$​ é o valor observado no i-ésimo nível do fator e j-ésima repetição.
- $\bar{y}_{i.}$​ é a média das observações no i-ésimo nível do fator.
	**Quadrado médio: **$QMRes = \frac{SQRes}{a(n-1)} \rightarrow E(QMRes)=\sigma^2.$
	- Temos também que $\frac{SQRes}{\sigma^2} \sim \chi_{a(n-1)}^2,$ isto é, segue uma distribuição qui-quadrado com $a(n−1)$ graus de liberdade

## Conclusão
podemos concluir que $QMRes$ corresponde a um estimador não viciado para $σ_2$. Além disso, sob $H_0:τ_1=τ_2=⋯=τ_a=0$, segue que $QMTrat$ também será um estimador não viciado para $σ_2$. Entretanto, o ==$QMRes$ sempre será um estimador não viciado para $σ_2$, indenpendente da veracidade de $H_0$==, o mesmo não sendo verdade para os demais quadrados médios envolvidos em uma análise de variâncias.

Agora, dado que a diferença entre os valores esperados $QMRes$ e $QMTrat$ é igual a $\displaystyle \frac{n\sum_{i=1}^{a}\tau_{i}^{2}}{(a-1)}$, dado que a hipótese nula ($H_0:τ_1=τ_2=⋯=τ_a=0$) for verdadeira, a diferença é nula, logo, temos que a **estatística de teste** é: $$F_{0} = \frac{QMTrat}{QMRes} = \frac{SQTrat/(a-1)}{SQRes/a(n-1)} \sim F_{a-1; a(n-1)}$$Assim, se não houver diferença significativa entre nenhum par de médias, esperamos que o valor observado $f_0$ seja próximo de 1, caso contrário o valor será significativamente maior que 1. Além disso temos: $$RC = \{f_{0}: f_{0}>f_{(1-\alpha; ~a-1, ~a(n-1))} \}.$$Onde rejeitamos $H_0$ se $f_{0}>f_{(1-\alpha;~a-1;~a(n-1))}$. E, por final, o **P-valor**: $$    \alpha^{*}=P\left(_{(1-\alpha;~a-1;~a(n-1))}>f_{0}\right).$$

## Explicação em código (3.2 - Saquinhos de papel)
```
library(planex)
library(tidyverse)

data(saquinhos)  # carregando os dados

saquinhos        # imprimindo na tela os dados
# >   resistencia concentracao
# > 1 	7		 	 5
# > 2 	8		 	 5
# > 3 	15	    	 5
  

#  Neste caso, o fator de interesse são os saquinhos
# verificando a classe os objetos do data.frame saquinhos:

sapply(saquinhos, class)
# >resistencia concentracao
# >"integer" "factor"
  

saquinhos <- saquinhos %>%
  mutate(concentracao = as.factor(concentracao)  # transformando [concentracao] em fator para bom ajuste do modelo)


ggplot(saquinhos, aes(x = concentracao, y = resistencia)) +
  geom_boxplot()

ggplot(saquinhos, aes(x = resistencia, y = concentracao)) +
  geom_density_ridges(aes(fill = concentracao))

  

# obtendo a média e o desvio padrão para cada nível de concentração:

saquinhos %>%
  group_by(concentracao) %>%
  summarise(
    media = mean(resistencia),
    dp = sd(resistencia)
  )
  

#  Para ajustar o modelo e obter ANOVA
# "analysis of variance (AOV) da resistência dado o fator concentração (resistencia ~ concentracao)"

mod <- aov(resistencia ~ concentracao, data = saquinhos)
summary(mod)
# >             Df  Sum    Sq      {Mean Sq}   {F value} Pr(>F)
# > concentracao 3  382.8  127.60      19.61     3.59e-06 ***
# > Residuals   20  130.2  6.51
# > Signif. codes: 0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

#  ISSO É ANOVA!!

valor_critico <- qf(0.05, 3, 20, lower.tail = FALSE)

```

O que podemos entender desta saida de código:
- soma dos quadrados da concentração : $SQTrat=382.8 \rightarrow QMTrat = \frac{SQTrat}{a-1[Df]} = \frac{382.8}{3}=127.6[Sq]$
- $SQRes = 130.2 \rightarrow QMRes = \frac{SQRes}{a(n-1)[Df]} = \frac{130.2}{20} = 6.51[Sq]$
- $F_{0} = \frac{QMTrat}{QMRes} =\frac{127.66}{6.51}=19.6 [mean Sq]$
- $F_{0.05, 3, 20} = 3.1$
Assim, como $F_0$ maior que $F_{0.05, 3, 20}$, rejeitamos $H_0$

Resolvendo por **p-valor** temos:
```pvalor <- pf(f0, 3, 20, lower.tail = FALSE)```
