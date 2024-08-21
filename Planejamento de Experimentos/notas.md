e. geral:
Via de regra, um objeto no R armazenando uma variável categórica deve ser da classe `factor`. Na análise de dados de um experimento planejado a não conversão (quando necessária) para a classe `factor` implicará no ajuste incorreto do modelo, invalidando dessa forma qualquer tipo de análise.


Diferença entre fator fixo e aleatório: **as hipóteses**

Hipóteses para:
- Fator fixo: a soma dos taos há de ser = 0![[Pasted image 20240716082137.png]]![[Pasted image 20240716082212.png]]
- Fator aleatório:
		Agora, tao_i é uma VA em vez de constante
		![[Pasted image 20240716082342.png]]
		$Y_{ij} = μ + τ_{i} + ϵ_{ij}$ 

![[notas-20240716083854773.webp]]
grau de liberdade ele vai zaralhar
vai ter saida errada
experimento fatorial tem que ser balanceado

# 9/07
**Faz parte de: [[Planejamento de Experimentos]]**

- Pacote Planex no R
- emmeans para comparações de múltiplas vars. que o agricolae também faz, mas o primeiro faz 
	- Retomamos no slide de planex pg. 69

sintáxe: ````emmeans(mod, pairwise ~ temperatura|tipo,  adjust = "none") ```` para ajustar o modelo

	![[Pasted image 20240709075319.png]]

Quando tiver controle -> Teste de Dunnet (`contrast(comp, method="dunett", ref=4))
**dia 23 prova!!!**
terça que vem revisão


```
baterias = baterias %>%
	mutate(
		across(c(v1, v2), as.factor)
	)
```

```
mod = aov(tempo ~ temperatura*tipo, data=baterias)
interactionPlot(mod)  # gráfico de interações
plotResiduals(mod)
testResiduals(mod)  # ver se o modelo está bem ajustado
```