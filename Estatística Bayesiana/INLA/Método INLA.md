The integrated nested Laplace approximation (INLA) is a method for approximate Bayesian inference. In the last years it has established itself as an alternative to other methods such as Markov chain Monte Carlo([[MCMC]]) because of its speed and ease of use via the R-INLA package. Although the INLA methodology focuses on models that can be expressed as latent Gaussian Markov random fields ([[Gaussian Markov Random Fields (GMRFs)]]), this encompasses a large family of models that are used in practice.

[This](https://www.google.com/url?q=https%3A%2F%2Finla.r-inla-download.org%2Fr-inla.org%2Fdoc%2Finla-manual%2Finla-manual.pdf&sa=D&sntz=1&usg=AOvVaw3JTTPo4X8z-LlB-gjAiVKb) manual describes the INLA program, a new instrument which allows the user to easily perform approximate Bayesian inference using integrated nested Laplace approximation (INLA). We describe the set of models which can be solved by the inla program and provide a series of worked out examples illustrating its usage in details. Appendix A contains a reference manual for the inla program.

The main advantage of the INLA approach over MCMC is that it is much faster to compute; it gives answers in minutes and seconds where MCMC requires hours and days.

### Para entender o método INLA, é importante, também, saber: 
- [[Inferência Bayesiana]]
- [[Latent Gaussian Models (LGMs)]]
- [[Gaussian Markov Random Fields (GMRFs)]]
- [[Laplace approximation]]

O foco do método INLA é estimar as distribuições marginais posteriores dos parâmetros dos modelos. Temos, então, ao invés de estimar uma distribuição posterior altamente multivariada $\pi(\theta_i|y)$, o foco é apenas em obter uma aproximação de uma distribuição posterior univariada $\pi(\theta_i|y)$.

Although the models that INLA can fit are restricted to the class of models that can be expressed as a latent [[Gaussian Markov Random Fields (GMRFs)]], this includes lots of commonly used models.

## Exemplo: Quantidade de Us em livros do Game of Thrones
Vamos considerar on número médio de Us em uma página de qualquier livro da série de GoT
1. Temos os seguintes dados:
   
```
##        Us      
##  Min.   :15.0  
##  1st Qu.:27.5  
##  Median :31.0  
##  Mean   :33.0  
##  3rd Qu.:36.5  
##  Max.   :62.0
```
2. Primeiro, precisamos considerar, uma vez que estamos fazendo uma contagem, que uma probabilidade de poisson para verossimelhança (likelihood) é uma boa ideia. Temos então a distribuição abaixo, onde $\lambda$ é a média da distribuição, e o **parâmetro de interesse**.
$$
   \text{Número de Us por página: }U_i \sim Po(\lambda),\ i=1,\ldots,31
$$
	Lembrando que a função de probabilidade de uma poisson é: $$
	\text{verossimelhança: }P(X = x \mid\lambda) = \frac{\exp(-\lambda)\lambda^x}{x!}
	$$
	Note that letter _u_ is not the most common vowel in English, and this fact can be used to make a choice about the prior distribution. Each page has about 20 lines and, say that we are certain that there will be about one or two _u_’s per line. 
	Podemos usar este fato para **inferir uma priori sob $\lambda$**

3. Temos que **uma Gamma é a distribuição priori conjunta para uma verossimelhança de Poisson**. This is defined by two parameters, a and b, that define the mean, $a/b$, and variance, $a/b^2$. The probability density of the Gamma distribution is:
$$
   \text{Priori: }f_X(x \mid a, b) = b\exp(-b\cdot x)\frac{(b\cdot x)^{a-1}}{\Gamma(a)}
$$
4. Dado nosso chute de priori, podemos tomar nossa distribuição Gamma com média 30 e variância 5, o que dá alta probabilidade a priori de $\lambda$ estar entre 20 e 40, logo, os parâmetros da distribuição prior Gamma são $a=180$ e $b=6$ (?)
   ![[Método INLA-20240728202536775.webp]]

5. A common way to visualize the likelihood and the prior is to plot them together. Note how they are in different scales but the modes are close, which means that our prior guess was not that bad after all. **The posterior distribution will be obtained by combining the prior and the likelihood using Bayes’ rule**.
6. 
   - Podemos obter a máxima verossimelhança ao tirar uma média do total de Us por página

```
   mean(GoT$Us)
   ## 33.03
```

   - Uma estimativa para a *Máxima A Posteriori (MAP)* pode ser obtida ao maximizar a soma do log da prior e do log da verossimelhança

```
     got.logposterior <- function(lambda) {
  dgamma(lambda, 180, 6, log = TRUE) + sum(dpois(GoT$Us, lambda,
    log = TRUE))
}

#Maximize log-posterior
got.MAP <- optim(30, got.logposterior, control = list(fnscale = -1))
got.MAP$par
## 32.52
```


### Links interessantes:
- https://becarioprecario.bitbucket.io/inla-gitbook/ch-intro.html - **Bayesian inference with INLA**, _Virgilio Gómez-Rubio_ (2021)
- [This](https://www.google.com/url?q=https%3A%2F%2Finla.r-inla-download.org%2Fr-inla.org%2Fdoc%2Finla-manual%2Finla-manual.pdf&sa=D&sntz=1&usg=AOvVaw3JTTPo4X8z-LlB-gjAiVKb)
  1.1 ~ 1.4: Inferência Bayesiana

