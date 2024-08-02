***Pertence à: [[Processos Estocásticos]]***

GMRFs são uma classe de modelos utilizados principalmente para dados espaciais e temporais, onde se assume que as variáveis seguem uma distribuição Gaussiana e têm dependências de Markov.

In short, a latent GMRF model is a hierarchical model where, at the first stage we find a distributional assumption for the observables $y$ usually assumed to be conditionally independent given some [[Latent Parameters (parâmetros latentes)]] $η$ and, possibly, some additional parameters $θ_1$
$$
\pi(y|\eta, θ1) = \Pi_{j} \pi(y_j|\eta_j, \theta_1)
$$
The latent parameters $η$ are part of a larger latent random field x, which constitutes the second stage of our
hierarchical model. The latent field $x$ is modelled as a GMRF with precision matrix $Q$ depending on some
[[Hyperparameters (hiperparâmetros)]] $θ_2$

Ou seja:
no primeiro momento, obtemos a distribuição assumida $y \sim \pi(y|\eta, \theta_1$), que é assumida independente, dado o hiperparâmetro $\eta$ e, possívelmente, algum parâmetro adicional $\theta$
TODO