***Pertence a: [[Estatística Bayesiana]]***

Métodos de Markov Chain Monte Carlo são uma classe de [[Métodos Computacionais]] que obtem amostras da distribuiçao conjunta posteriori (the joint posterior distribution).

Estes métodos são baseados em construir uma cadeia de markov com uma distribuição da posteriori estacionária, então, ao amostrar desta cadeia de markov repetidamente, amostras da distribuição posterior conjunta são obtidas após um número de iterações.

Diversos algorítmos foram propostos mas dois deles provém a *toolbox* para inferência bayesiana. 





































*** 
Os métodos de Monte Carlo também podem ser divididos em duas categorias:

- **Integração** de Monte Carlo: quando utilizado para resolver problemas de integração numérica
- **Simulação** de Monte Carlo: quando utilizado para resolver problemas mais gerais através de simulação

Dado uma função de prob. Podemos constriur uma **Cadeia de Markov** (que designa a probabilidade de transição de um elemento ao outro) aonde há uma aproximação da distribuição dos elementos; $$X^{(0)} -> X^{(1)}; T=0, 1,2$$Temos também a seguinte notação: $$P[X_t | X_{t-1}, X_{t-2}, \ldots, X_0] = P[X_t | X_{t-1}]$$ Dessa forma, para determinar a sequência de valores que a cadeia pode assumir, podemos **determinar a distribuição do próximo valor conhecendo apenas o valor anterior**. A distribuição de probabilidade condicional, que determina se a cadeia se move de um estado para outro é chamada de **kernel de transição** ou **matriz de transição**, e pode ser denotada por $K(X_t, X_{t-1})$

![Cadeia de Markov](x5apxfwm.bmp)
## Estacionaridade

1. Uma cadeia de Markov é dita **estacionária** se suas propriedades estatísticas não mudam ao longo do tempo.
   **Propriedades:**
	- **Distribuição Invariante:** Existe uma distribuição de probabilidade π\piπ tal que $πP=π$, onde $P$ é a matriz de transição da cadeia de Markov.
	- **Tempo Invariante:** As probabilidades de transição de um estado para outro são constantes ao longo do tempo.
	- **Estado Estável:** Após um número suficiente de passos, a distribuição de probabilidade dos estados converge para a distribuição estacionária, independentemente da distribuição inicial.
2. Uma cadeia de Markov é dita **não estacionária** se suas propriedades estatísticas mudam ao longo do tempo.
   **Propriedades:**
	- **Distribuição Variável:** A distribuição de probabilidade dos estados do sistema pode mudar ao longo do tempo.
	- **Transições Temporais:** As probabilidades de transição entre estados podem depender do tempo ou do passo da cadeia.
	- **Ausência de Equilíbrio:** A cadeia pode não atingir uma distribuição estacionária ou pode levar muito tempo para fazê-lo.

### Cadeias de Markov Estacionárias em MCMC

==Nos métodos de MCMC, o objetivo é criar uma cadeia de Markov que seja **estacionária** em relação à distribuição de probabilidade alvo==. Isso significa que a cadeia de Markov deve convergir para uma distribuição estacionária que coincide com a distribuição desejada.

**Características em MCMC:**
1. **Distribuição Alvo:** A distribuição estacionária da cadeia de Markov é a distribuição da qual queremos amostrar.
2. **Convergência:** Após um número suficiente de iterações, as amostras geradas pela cadeia de Markov serão amostras válidas da distribuição alvo.
3. **Mixing Time:** O tempo necessário para a cadeia se aproximar suficientemente da distribuição estacionária é conhecido como "tempo de mistura". Quanto menor o tempo de mistura, mais rapidamente a cadeia atinge a distribuição estacionária
**Fase de Burn-in:** Nos primeiros passos da cadeia, as amostras podem não seguir a distribuição estacionária. Esse período é conhecido como fase de "burn-in". Amostras obtidas durante esta fase são geralmente descartadas. Para garantir que as amostras utilizadas para inferência venham da distribuição estacionária, é comum descartar as primeiras NNN amostras da cadeia (onde NNN é o período de burn-in).

***Leia: [[Métodos de MCMC]]***