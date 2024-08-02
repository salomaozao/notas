***Cap. 1 de [[Regressão]]***
Alguns conjuntos de dados discutidos neste material, bem como algumas funções utilizadas para a realização das análises, estão disponíveis no pacote **reglin** (acesse a página do pacote para mais informações: [https://fndemarqui.github.io/reglin](https://fndemarqui.github.io/reglin)).

![[Pasted image 20240711080308.png]]

A equação apresentada acima é bastante geral, e acomoda duas classes bastante importantes de modelos, a saber:

1. Modelos lineares: $\beta_0 + \beta_1x + \epsilon_i$
2. Modelos não lineares: $e^{\beta_0+\beta_1x} + \epsilon$

Os modelos lineares, por sua vez, podem ser divididos em duas subclasses de modelos:

1. Modelos de regressão linear;
2. Modelos de análise de variância.

A diferença entre os modelos de regressão linear e os modelos de análise de variância, em linhas bastante gerais, reside no tipo de pergunta que desejamos responder. Mais especificamente, quando ajustamos um modelo de regressão linear estamos interessados, em última instância, em realizar previsões para a variável resposta com base no conhecimento de um conjunto de variáveis explicativas $\boldsymbol{x} = (x_{1}, \cdots, x_{k})$, como em [[Machine Learning]]. Já nos modelos de análise de variância, o foco está na verificação da existência/ausência de diferenças significativas em um conjunto de condições previamente determinadas.