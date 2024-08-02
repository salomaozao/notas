O algoritmo de Metropolis-Hasting usa uma distribuição proposta para obter novos valores para o conjunto de parâmetros, ou seja, dado um valor $\theta$, um novo $\theta'$ é proposto da densidade $q(\cdot \mid \theta)$.

A **distribuição proposta** $q$ pode ser escolhida de várias maneiras diferentes, entretanto, nem todas propostas serão aceitas. Quando uma nova proposta é elaborada ela é aceita com probabilidade 

$$\min\left\{1, \frac{q(\theta \mid \theta^{'})\pi(\theta^{'} \mid \mathbf{y})}{q(\theta^{'} \mid \theta)\pi(\theta \mid \mathbf{y})}\right\}$$
Aqui, $q(\theta \mid \theta^{'})$ representa a densidade da distribuição proposta $q(\cdot \mid \theta')$ avaliado em $\theta$, note também que a probabilidade de aceitação contém a distribuição posterior a ser estimada ( $\pi(\theta|y)$ )(que é desconhecida)

Podemos reformular:
$$
\pi(\theta \mid \mathbf{y}) \propto \pi(\mathbf{y} \mid \theta)\pi(\theta) \rightarrow \min\left\{1, \frac{q(\theta \mid \theta^{'})\pi(\mathbf{y} \mid \theta^{'})\pi(\theta^{'})}{q(\theta^{'} \mid \theta)\pi(\mathbf{y} \mid \theta)\pi(\theta)}\right\}

$$

by using Bayes’ rule. Note that now the scaling constant **π(y)** is not needed to compute the ratio, which is why the Metropolis-Hastings algorithm is so popular.

A proporção assegura que novos valores propostos são aceitos na proporção certas para serem amostras da distribuição posterior. Além disso, a proporção também favorece mudar para novos valores quando há uma alta chance de voltar ao valor atual. 

Isto faz sentido porque isso vai prevenir de ficar preso em área de baixa probabilidade posterior.

***
1. **Obtemos a distribuição proposta 
2. **Passamos Y pela regra de aceitação → $Y = g(⋅|X_t)$**
3. **Se aceito,** $X_{t+1}  = Y$

A proposta deve ser escolhida de forma que a cadeia gerada vá, de fato, convergir para a distribuição $f$

As condições necessárias para a cadeia gerada são: **irreducibilidade**, **recorrência positiva** e **aperiodicidade**. 

Uma distribuição proposta com o mesmo suporte da distribuição alvo, geralmente irá satisfazer estas condições de regularidade
### Links interessantes:
- [R-INLA: MCMC](https://becarioprecario.bitbucket.io/inla-gitbook/ch-intro.html#markov-chain-monte-carlo)
- [Material de Bayesiana UFPR](http://cursos.leg.ufpr.br/ce089/08_MCMC.html#3_Algoritmos_de_Metropolis-Hastings) 