`The` integrated nested Laplace approximation (INLA) is a method for approximate Bayesian inference. In the last years it has established itself as an alternative to other methods such as Markov chain Monte Carlo([[MCMC]]) because of its speed and ease of use via the R-INLA package. Although the INLA methodology focuses on models that can be expressed as latent Gaussian Markov random fields ([[Gaussian Markov Random Fields (GMRFs)]]), this encompasses a large family of models that are used in practice.

[This](https://inla.r-inla-download.org/r-inla.org/doc/inla-manual/inla-manual.pdf) manual describes the INLA program, a new instrument which allows the user to easily perform approximate Bayesian inference using integrated nested Laplace approximation (INLA). We describe the set of models which can be solved by the inla program and provide a series of worked out examples illustrating its usage in details. Appendix A contains a reference manual for the inla program.

The main advantage of the INLA approach over MCMC is that it is much faster to compute; it gives answers in minutes and seconds where MCMC requires hours and days.

### Para entender o método INLA, é importante, também, saber: 
- [[1. Inferência Bayesiana]]
- [[Latent Gaussian Models (LGMs)]]
- [[Gaussian Markov Random Fields (GMRFs)]]
- [[Laplace approximation]]

O foco do método INLA é estimar as distribuições marginais posteriores dos parâmetros dos modelos. Temos, então, ao invés de estimar uma distribuição posterior altamente multivariada $\pi(\theta_i|y)$, o foco é apenas em obter uma aproximação de uma distribuição posterior univariada $\pi(\theta_i|y)$.

Although the models that INLA can fit are restricted to the class of models that can be expressed as a latent [[Gaussian Markov Random Fields (GMRFs)]], this includes lots of commonly used models.

[[Caso de uso de Inf. Bayesiana]]

## Modelo
> In order to describe the models that INLA can fit, a vector of $n$ observations $y=(y_1,…,y_n)$ will be considered. Note that some of them may be missing observations. Furthermore, these observations will have an associated likelihood (not necessarily from the exponential family). In general, mean $μ_i$ of observation $y_i$ can be linked to the linear predictor $η_i$ via a convenient function.

Observations will be independent given its linear predictor, i.e.,
$$\eta_i = \alpha + \sum_{j=1}^{n_\beta} \beta_j z_{ji} +\sum_{k=1}^{n_f} f^{(k)}(u_{ki})+\varepsilon_i;\ i=1,\ldots,n$$
Here,
- $α$ is the **intercept**
- $β_j, j=1,…,n_β$, **coefficients** of some covariates $\{\mathbf{z}_j\}_{j=1}^{n_{\beta}}$
- Functions $f(k)$ define $n_f$ **random effects** on some vector of covariates {uk}nfk=1.
- Finally, $ε_i$ is an **error term**, that may be missing depending on the *likelihood*.

Within the INLA framework, the vector of latent effects $x$ (read [[Latent Parameters (parâmetros latentes)]]) will be represented as follows:
$$
\mathbf{x} = \left(\eta_1, \ldots,\eta_n, \alpha, \beta_1, \ldots \right)
$$

The latent GRMF structure ([[Gaussian Markov Random Fields (GMRFs)]], [[Latent Gaussian Models (LGMs)]]) of the model will have zero mean and precision matrix $Q(θ2$), which will depend on a vector of hyperparameters $θ_2$. To simplify notation we will consider $θ=(θ_1,θ_2)$ and will avoid referring to $θ_1$ or $θ_2$ individually. Given the structure of GMRF, precision matrix $Q(θ)$ will often be very sparse. INLA will take advantage of this sparse structure as well as conditional independence properties of GMRFs in order to speed up computations.
### Links interessantes:
- [A manual for the inla program](https://inla.r-inla-download.org/r-inla.org/doc/inla-manual/inla-manual.pdf)  1.1 ~ 1.4: Inferência Bayesiana
- [INLA gitbook]: **Bayesian inference with INLA**, muito bom
