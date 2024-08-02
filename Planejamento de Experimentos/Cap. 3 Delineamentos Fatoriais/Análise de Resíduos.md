#estatística #estatística_geral #material_p2_geral #planex
![Untitled](Untitled%2010.png)

A verificação de tais suposições é feita através da chamada análise de resíduos, e constitui uma etapa indispensável para a validação do modelo em estudo e, consequentemente, validação de quaisquer conclusões que venham a ser obtidas através da análise dos dados experimentais.

Por definição, um resíduo é a diferença entre a observação yij e o seu valor estimado (ou ajustado) ^yij, obtido a partir do modelo estatístico sendo estudado, isto é, 

![Untitled](Untitled%2011.png)

yij = mu - ti - Eij

y^ = mu^ + t^i

A suposição de independência pode ser verificada graficamente plotando-se os resíduos na ordem em que os dados foram coletados. 

```r
#exemplo dos saquinhos
x <- rnorm(n=24, mean = 0, sd = 1)
hist(x) # parece assimétrica em n pequenos, assim, apenas olhando para histogramas, é difícil assumir normalidade

y <- rnorm(n=240, mean = 0, sd = 1)
hist(y) # agora, já fica mais fácil
```

A suposição de normalidade pode ser verificada graficamente através da construção de um histograma para os resíduos.

![A maneira mais efetiva de provar normalidade, plotando o percentil empírico contra o percentil teórico](Untitled%2012.png)

A maneira mais efetiva de provar normalidade, plotando o percentil empírico contra o percentil teórico

$fn(x) = 1/2 \sum(I_{xi ≤ x})$, ou seja, a quantidade de valores de xi menor que x dividido por dois é o **percentil empírico**

O **percentil teórico** é a distribuição da normal, o que seria x = y (?)

![Untitled](Untitled%2013.png)

Não há indicativos de heterocedasticidade das variâncias, pois a dispersão dos resíduos parece similar dentro de cada nível do fator de interesse (concentração), e pode ser observado um padrão aleatório em torno de zero no gráfico dos resíduos versus valores ajustados.

![Parece aleatório, este gráfico pode provar independência, assim como o teste de Durbin Wabson](Untitled%2014.png)

Parece aleatório, este gráfico pode provar independência, assim como o teste de Durbin Wabson

### Testes

Algumas observações importantes sobre a análise de resíduos de um modelo de análise de variância:

1. É recomentada a realização da análise de resíduos considerando-se tanto a **análise gráfica** quanto os **testes formais** sugeridos
2. A presença de observações discrepantes (outliers) pode distorcer seriamente a ANOVA.
3. Pequenos desvios da suposição de normalidade não são motivos de maiores preocupações para a ANOVA envolvendo delineamentos com fatores fixos.
4. É motivo de maiores preocupações situações nas quais a distribuição dos resíduos apresentar caudas consideravelmente mais pesadas (ou mais leves) do que a distribuição normal.
5. O teste F e os procedimentos de comparações múltiplas são levemente afetados (dizemos que eles são robustos!) por pequenos desvios da normalidade. Consequências de pequenos desvios da normalidade podem levar a um nível de significância ligeiramente diferente do valor nominal, e um menor menor poder associado ao teste, isto é, uma menor probabilidade de rejeitarmos a hipótese nula.
6. As funções [`planex::plotResiduals()`](https://fndemarqui.github.io/planex/reference/plotResiduals.html) e [`planex::testResiduals()`](https://fndemarqui.github.io/planex/reference/testResiduals.html) fornecem os principais gráficos e testes realizados na análise de resíduos de um modelo de análise de variâncias.

Testes de normalidade:

- Teste de Shapiro-Wilk;
- Teste de Anderson-Darling.

Em ambos os testes a hipótese nula é de que as observações seguem uma distribuição normal, e a hipótese alternativa é que a distribuição das observações não é normal;

Testes de homogeneidade das variâncias:

- Teste de Bartlett;
- Teste de Levene.

Em ambos os testes a hipótese nula é de que a variância é constante, isto é, a mesma dentro de cada nível do fator (ou fatores) de interesse, e a hipótese alternativa é de que pelo variância seja diferente dentro de pelo menos 2 níveis.

**Para chegar em uma conclusão**, tomamos a análise gráfica e formal, caso ambas concordarem na conclusão, ótimo. Caso contrário, há de se explicar porque dessa divergência, não há uma prova absoluta.

