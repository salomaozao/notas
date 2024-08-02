
Quando a distribuição posterior não está disponível em forma fechada, é necessário recorrer a outros métodos para estimá-la ou, alternativamente, para gerar amostras dela. Dada uma amostra da posterior, o [[Teorema Ergódico]] assegura que momentos e outras quantidades de interesse podem ser estimados.

Em geral, métodos computacionais focam em **estimar integrais que aparecem na inferência bayesiana.**

Por exemplo, a média posterior do parâmetro $\theta_i$, onde $\theta_i \in \Theta_i$ ($\Theta_i$ sendo um espaço), pode ser computado como:
$$\int_{\Theta_i} \theta_i \pi(\theta_i \mid \mathbf{y}) d\theta_i$$
Distribution $π(θ_i∣y)$ is the marginal posterior distribution of univariate parameter $θ_i$. Similarly, the posterior variance or any other moment can be computed as well. **Integrals of this type can be conveniently approximated using numerical integration methods and the [[Laplace approximation]]**

Furthermore, typical Monte Carlo methods ([[MCMC]]) to sample from densities known up to a constant can be used to obtain samples from the posterior distribution. These methods include rejection sampling and other methods, such as [[Amostrador de Gibbs]] e [[Algoritmo de Metropolis-Hasting]]. However, most of these methods will not work well in high dimensional spaces.
[[Estimativas pontuais]] (point estimates) of the model parameters can be obtained by maximizing the the product of the likelihood and the prior.