# Exemplo: [An introductory example: U’s in Game of Thrones books](https://becarioprecario.bitbucket.io/inla-gitbook/ch-intro.html#an-introductory-example-us-in-game-of-thrones-books)
#### Aqui, queremos estimar uma distribuição para o número de Us nas páginas dos livros.
Vamos estimar o número médio de Us em um parágrafo de um texto placeholder. Temos os seguintes dados:
   

```r
>text <- data.frame(us = sapply(pages, function(x) sum(strsplit(x, "")[[1]] == "u")))
>summary(text$us)
Min. 1st Qu. Median  Mean   3rd Qu. Max.

0.430 3.652 5.001    5.319  6.593 18.413
```
Aqui, a **média amostral é 5.319

## Estimação usando [[1. Inferência Bayesiana]]

1. Primeiro, precisamos considerar, uma vez que estamos fazendo uma contagem, que uma probabilidade de poisson para verossimelhança (likelihood) é uma boa ideia. Temos então a distribuição abaixo, onde $\lambda$ é a média da distribuição, e o **parâmetro de interesse**.
$$
   \text{Número de Us por página: }U_i \sim Po(\lambda),\ i=1,\ldots,31
$$
	Lembrando que a função de probabilidade de uma poisson é: $$
	\text{verossimelhança: }P(X = x \mid\lambda) = \frac{\exp(-\lambda)\lambda^x}{x!}
	$$
	**Parainferir uma priori sob $\lambda$: **
	$$Prior: y \sim Gama\left(\frac{\overline{x}^2}{s}, \frac{\overline{x}}{s}\right)$$

2. Temos que **uma Gamma é a distribuição priori conjunta para uma verossimelhança de Poisson**. This is defined by two parameters, a and b, that define the mean, $a/b$, and variance, $a/b^2$.  
3. Dado nosso chute de priori, podemos tomar nossa distribuição Gamma com média 30 e variância 5, o que dá alta probabilidade a priori de $\lambda$ estar entre 20 e 40, logo, os parâmetros da distribuição prior Gamma são $a=180$ e $b=6$ 
   ![[Método INLA-20240728202536775.webp]]

4. A common way to visualize the likelihood and the prior is to plot them together. Note how they are in different scales but the modes are close, which means that our prior guess was not that bad after all. **The posterior distribution will be obtained by combining the prior and the likelihood using Bayes’ rule**.

```r
logposterior <- function(lambda) {
  dgamma(lambda, 180, 6, log = TRUE) +
  sum(dpois(us, lambda, log = TRUE))
}
```

   - Uma estimativa para a *Máxima A Posteriori (MAP)* pode ser obtida ao maximizar a soma do log da prior e do log da verossimelhança

Dado que uma distribuição Gamma é conjugada por uma verossimelhança poisson, temos a posterior em forma fechada (closed form), e é $Gamma(a + \sum_{i=1}^{31} U_i, b_n)$, plotada abaixo junto à estimativa de MAP
**MAP Estimate:** The MAP estimate is a point estimate of the parameter that maximizes the posterior distribution. In other words, it is the value of the parameter that is most probable given the observed data and prior beliefs.

```r
g1 = mean(us)^2 / var(us)
g2 = var(us) / mean(us)
# Grande chance de alpha estar entre 4.5 e 6.5

logposterior <- function(lambda) {
  dgamma(lambda, g1, g2, log = TRUE) +
  sum(dpois(us, lambda, log = TRUE))
}

#Maximize log-posterior
MAP <- optim(mean(us), logposterior, control = list(fnscale = -1))

MAP$par
# > 5.278235 
```
Aqui, ``par`` é a **estimativa na base do MAP.**

## Estimação usando [[MCMC]]
>![[g6sxt8bj.bmp|848]]
>Figure 1.2: Posterior distribution of the number of u’s in a book of Game of Thrones using a conjugate prior (black solid line) and MAP estimate (dotted red line).

A Metropolis-Hastings algorithm to estimate the posterior distribution of the parameter λ can be implemented in this case. As a proposal density we will consider a log-Normal distribution centered at the current value of the mean λ and with small standard deviation equal to 0.05.

```r
set.seed(1)

n.sim <- 40000
lambda <- rep(NA, n.sim)
lambda[1] <- 5
```

Aqui, determinamos a raiz pseudoaleatória , então definimos o array onde serão colocadas as amostras de $\lambda$. Lembrando que o [[Algoritmo de Metropolis-Hasting]] é um **amostrador**, então após um número de repetições de *burn-in*, começamos a gerar uma amostra da distribuição da posteriori

``` r
#Log-acceptance probability
for (i in 2:n.sim) {
  lambda.new <- rnorm(1, mean = lambda[i - 1], sd = 1)  # Usando normal como proposta

  acc.prob <-
    dnorm(lambda[i -1], mean = lambda.new, sd = 1, log = TRUE) +   # Proposta Normal
    dgamma(lambda.new, gamma.a, gamma.b, log = TRUE) -            # Prior Gamma
    dnorm(lambda.new, mean = lambda[i - 1], sd = 1, log = TRUE) - # Proposta Normal
    dgamma(lambda[i - 1], gamma.a, gamma.b, log = TRUE)            # Prior Gamma
   
  acc.prob <- min(1, exp(acc.prob))
```
The Metropolis-Hastings algorithm uses a proposal distribution to obtain new values for the ensemble of parameters. This is, given current value θ a new value θ′ is drawn from density q(⋅∣θ). The proposal distribution can be chosen in many different ways. However, not all proposals will be accepted. When a new proposal is drawn it is accepted with probability
$$\min\left\{1, \frac{q(\theta \mid \theta^{'})\pi(\theta^{'} \mid \mathbf{y})}{q(\theta^{'} \mid \theta)\pi(\theta \mid \mathbf{y})}\right\} = \min\left\{1, \frac{q(\theta \mid \theta^{'})\pi(\mathbf{y} \mid \theta^{'})\pi(\theta^{'})}{q(\theta^{'} \mid \theta)\pi(\mathbf{y} \mid \theta)\pi(\theta)}\right\}
$$
by using Bayes’ rule. Note that now the scaling constant π(y) is not needed to compute the ratio, which is why the Metropolis-Hastings algorithm is so popular.

```r
  # Accept/reject new value
  acc.prob <- min(1, exp(acc.prob))
    lambda[i] <- lambda.new
  } else {
    lambda[i] <- lambda[i - 1]
  }
```

Agora, para concluir, excluímos o burn-in e obtemos nossa amostra:
```r
lambda2 <- lambda[seq(101, n.sim, by = 5)]
summary(lambda2)
> Min. 1st Qu. Median Mean 3rd Qu. Max.
> 0.3879 2.7767 3.8817 4.1966 5.2721 16.4381
```

Aonde obtemos nossa **estimação da média do MCMC de 3.8817**

## Estimação Usando [[Método INLA]]
primeiro, partimos que:
 - $U_i \sim Po(\lambda),\ i=1,\ldots, 31$
 - $\log(\lambda) = \alpha$
 - $\pi(\alpha) \propto 1$, ou seja, é **linear**

Então:
```r 
GoT.inla <- inla(us ~ 1, data = text, family = "poisson",
  control.predictor = list(compute = TRUE)
)
```

Então, temos as estatísticas de $log(\alpha)$:
```r
GoT.inla$summary.fixed

> 			mean     sd        0.025quant 0.5quant 0.975quant mode kld
> (Intercept) 1.692555 0.06388766 1.567337 1.692555 1.817772 1.692555 0
```

```r
marg.lambda <- inla.tmarginal(exp, inla$marginals.fixed[[1]])
inla.est <- inla.zmarginal(marg.lambda)

> Mean 5.4443
> Stdev 0.345971
> Quantile 0.025 4.79586
> Quantile 0.25 5.20391
> Quantile 0.5 5.43278
> Quantile 0.75 5.67171
> Quantile 0.975 6.15422
```

logo, **a média fornecida pelo INLA é de 5.4443**

Podemos comparar os valores:

| **$\overline{x}$**     | 5.319 |
| ---------------------- | ----- |
| **Bayesiana clássica** | 5.278 |
| **M-H**                | 3.881 |
| **INLA**               | 5.444 |
Podemos ver que o modelo de MCMC está mal ajustado.