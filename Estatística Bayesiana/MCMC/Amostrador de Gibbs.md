## [Amostrador de Gibbs](http://cursos.leg.ufpr.br/ce089/08_MCMC.html#4_Amostrador_de_Gibbs)

**Gibbs Sampling** é um algoritmo de Monte Carlo via Cadeias de Markov ([[MCMC]]) utilizado para amostrar de distribuições complexas, especialmente útil em contextos bayesianos onde as distribuições a posteriori são difíceis de calcular diretamente.

Gibbs sampling can be regarded as a particular case of the Metropolis-Hastings algorithm ([[Algoritmo de Metropolis-Hasting]]) in which the proposal distributions are the full conditional distribution of the model parameters, i.e., $π(θi∣y,θ−i)$. This ensures that the acceptance probability in the Metropolis-Hastings algorithm is always one, which means that all proposals are automatically accepted

In practice, convergence to the posterior distribution will take a number of iterations, and the first batch of simulations (or _burn-in_) is **discarded** for inference. Furthermore, given that samples are often correlated, a thinning is applied to the remaining samples, and many of them will be discarded as well. Several criteria can be used to assess that the simulation have converged to the stationary state

### Passos do Algoritmo de Gibbs Sampling

Considere um vetor de variáveis aleatórias $\mathbf{X} = (X_1, X_2, \ldots, X_n)$ cuja distribuição conjunta é $p(X_1, X_2, \ldots, X_n)$.
1. **Inicialização**: Escolha valores iniciais para todos os parâmetros do modelo $X(0)=(X1(0)​,X2(0)​,…,Xn(0)​).$.
    
2. **Iteração**: Atualize cada parâmetro $X_i$, um de cada vez, amostrando da distribuição condicional completa para esse parâmetro dado os valores atuais de todos os outros parâmetros.
   $$
X_1^{(t+1)} \sim p(X_1 \mid X_2^{(t)}, X_3^{(t)}, \ldots, X_n^{(t)})
$$ $$X_2^{(t+1)} \sim p(X_2 \mid X_1^{(t+1)}, X_3^{(t)}, \ldots, X_n^{(t)})$$ $$
X_n^{(t+1)} \sim p(X_n \mid X_{-n}^{(t+1)})

$$


- ### Multiestágios (Vários parâmetros):
	**Tendo que:** 
	
	$$
	\pi(\theta_i|\theta_{-i}) = {\pi(\theta)}/\int{\pi(\theta)d\theta}
	$$
	
	**temos os passos:** 
	
	1. definir os parâmetros para t=0, definindo $\theta^{(0)}_i \approx \pi(\theta^{(0)}_i|\theta^{(0)}_{-i})$
	2. . 
	    
	    ![Untitled](Untitled%202%202.png)
	    
	3. Repita o segundo passo para o número de iterações desejado

- ### Dois estágios (duas VAs)

	Dado que as VAs *X* e *Y possuem dist. conjunta f*(*x*,*y*), e assim $f_{Y|X}, f_{X|Y}$, o amostrador consegue obter $(X_t, Y_t)$ , desde que sea viável a simulação de ambas distribuições condicionais de tal modo:
	
	![Untitled](Untitled%203%202.png)
### Aplicação em Séries Temporais

No contexto de [[Séries Temporais]], xo Gibbs Sampling permite que amostremos as distribuições condicionais completas dos parâmetros e estados latentes de um modelo dinâmico, mesmo quando essas distribuições são complexas e de alta dimensão. Isso é particularmente útil para fazer inferências e previsões baseadas em dados observacionais ao longo do tempo.
### Benefícios e Desafios

- **Benefícios**:
    
    - Simplicidade de implementação.
    - Capacidade de lidar com distribuições complexas.
    - Aplicabilidade em modelos bayesianos de séries temporais.
- **Desafios**:
    
    - Convergência lenta em alguns casos.
    - Sensibilidade a escolhas iniciais e problemas de mistura das cadeias.

Gibbs Sampling é uma ferramenta poderosa na análise de séries temporais, especialmente quando combinado com modelos bayesianos, permitindo uma inferência robusta e flexível em contextos de dados temporais complexos.

### Exemplo de Uso

Considere um modelo de séries temporais onde queremos inferir sobre os parâmetros $θ$ e os estados latentes $X$ dados os dados observados $Y$: $\mathbf{Y} = (Y_1, Y_2, \ldots, Y_T)$ Podemos usar Gibbs sampling para iterativamente amostrar:
$\theta^{(t+1)} \sim p(\theta \mid \mathbf{X}^{(t)}, \mathbf{Y})$, logo: $\mathbf{X}^{(t+1)} \sim p(\mathbf{X} \mid \theta^{(t+1)}, \mathbf{Y})$

