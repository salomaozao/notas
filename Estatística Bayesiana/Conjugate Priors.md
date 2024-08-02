**Conjugate priors** são um conceito importante em estatística Bayesiana. Eles ocorrem quando a forma funcional da distribuição a posteriori pertence à mesma família da distribuição a priori. Isso simplifica significativamente os cálculos na inferência Bayesiana.

As mentioned above, the posterior distribution is only available in closed form ([[Closed Forms]]) for a few models. Models with _conjugate_ priors are those in which the prior is of the same form as the likelihood

### Por exemplo:

For example, let it be a set of observations $\{y_i\}_{i=1}^n$ that follow a Gaussian distribution

with $μ$ the unknown mean and $τ$ a known precision. The prior on $μ$ can be a Normal distribution with mean $μ_0$ and precision $τ_0$: $\mu \sim N(\mu_0, \tau_0)$

The posterior distribution of $μ$ (i.e., the distribution of $μ$ given data $y$) is $N(μ_1,τ_1)$ with: 
$$
\mu_1 = \mu_0 \frac{\tau_0}{\tau_0 + \tau n} + \overline{y}\frac{\tau n}{\tau_0 + \tau n}
$$
$$
\tau_1 = \tau_0 + n\tau
$$
Então, temos uma média desconhecida $\mu_0$, e queremos inferi-lá, obtendo $\mu_1$ que pertence a $N(\mu_1, \tau_1)$. Temos os dados $y$ e, da distribuição, sabemos a precisão $\tau_0$.

This illustrates Bayesian learning quite well. First of all, the posterior mean is a compromise between the prior mean $μ_0$ and the mean of the observed data $\overline{y}$

When the number of observations is large, then the posterior mean is close to that of the data. If $n$ is small, more weight is given to our prior belief about the mean.