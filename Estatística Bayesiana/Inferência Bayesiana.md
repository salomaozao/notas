***Pertence à: [[Estatística Bayesiana]]***

In the Bayesian paradigm all unknown quantities in the model are treated as random variables and the aim is to compute (or estimate) the joint _posterior_ distribution. This is, the distribution of the parameters, θ, conditional on the observed data y. The way that posterior distribution is obtained relies on Bayes’ theorem:
$$
\pi(\theta \mid \mathbf{y}) = \frac{\pi(\mathbf{y} \mid\theta)\pi(\theta)}{\pi(\mathbf{y})}


$$ $$
posterior = \frac{VM*priori}{p.marg}$$
O que, ainda, é equivalente, em um âmbito de inferência, à:
$$
P(\theta|y)=\frac{p(y\theta)p(\theta)}{\int p(y|\theta)p(\theta) d\theta}
$$
onde $\theta$ é uma VA, na qual obtemos média, mediana, moda, quantis, etc. de $\pi(\theta)$

Primeiro, estabelecemos que $y$ são os dados e $\theta$ é a distribuição dos parâmetros, então, temos que:
- $\pi$ é a função de densidade de probabilidade, ou seja, $\pi = f(x)$
- $\pi(\theta | y)$ é a **posteriori**, a distribuição dos parâmetros dado os dados que temos
- $\pi(y|\theta )$ é a **verossimelhanca**, ou seja, dado os parâmetros, qual a probabilidade dos dados ocorrerem
- $\pi(\theta)$ é a **priori**, a distribuição dos parâmetros
- $\pi(y)$ é a **probabilidade marginal** (distribuição dos dados), que serve também como constante de normalização.

Geralmente, a integral no denominador é **intratável**, ou computacionalmente muito cara, então usamos métodos como [[MCMC]] para amostrar da distribuição condicional e estimamos a distribuição marginal para cada parâmetro de interesse

Note that the posterior distribution $π(θ∣y)$ is often a highly multivariate distribution and that it is only available in closed form for a few models because the marginal likelihood $π(y)$ is often difficult to estimate. In practice, the posterior distribution is estimated without computing the marginal likelihood. This is why Bayes’ theorem is often stated as
$$
\pi(\theta \mid \mathbf{y}) \propto \pi(\mathbf{y} \mid \theta)\pi(\theta)
$$
$$
Posterior \propto VM * priori
$$
($\propto$ = proporcional a)
This means that the posterior can be estimated by re-scaling the product of the likelihood and the prior so that it integrates up to one

The **likelihood** of the model describes the data generating process given the parameters (distribuição dos parâmetros), and the **prior** usually reflects any previous knowledge about the model parameters. When this knowledge is scarce, vague priors are assumed so that the posterior distribution is driven by the observed data.
### Distribuição Posterior marginal (posterior _marginal_ distribution)
Summary statistics on the model parameters $θ$ can be obtained from the joint posterior distribution $π(θ∣y)$. In addition, the posterior _marginal_ distribution of each element of $θ$ can be obtained by integrating the remainder of the parameters out: 
$$
\pi(\theta_i \mid \mathbf{y}) = \int \pi(\theta \mid \mathbf{y}) d\theta_{-i},\ i=1,\ldots, \textrm{dim}(\theta)
$$

Podemos usar [[Conjugate Priors]] para cada parâmetro, obtendo a distribuição da posteriori em, forma fechada. Entenda mais lendo [[Conjugate Priors]]
