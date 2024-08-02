***Pertence a: [[Fatores]]***
- Quando dois fatores são cruzados, cada nível de um fator aparece com cada nível do outro fator em todas as combinações possíveis.

O modelo linear para delineamentos com dois fatores fixos cruzados $A$ e $B$ é:
$$
\begin{eqnarray}
        y_{ijk}=\mu+\tau_{i}+\beta_{j}+(\tau \beta)_{ij}+\epsilon_{ijk}, ~~
        {
        \left\{\begin{array}{lcc}
            i=1, ..., a \\
            j=1, ..., b \\
            k=1, ..., n
        \end{array}\right.
        },    \nonumber
    \end{eqnarray}
$$
em que

- $μ$ é a média geral, comum a todos os tratamentos;
- $τ_i$ é o [[Efeito]] do i-ésimo nível do fator $A$;
- $β_j$ é o [[Efeito]] do j-ésimo nível do fator $B$;
- $(τβ)_{ij}$ representa o efeito de interação entre os níveis $i$ e $j$ dos fatores $A$ e $B$, respectivamente;
- $ϵ_{ijk}$ é o erro aleatório (não observável) associado à variabilidade não explicada pelo modelo.

Temos, como em outros delineamentos com fatores fixos:
$$
  \sum_{i=1}^{a}\tau_{i}=\sum_{j=1}^{b}\beta_{j}=\sum_{i=1}^{a}(\tau\beta)_{ij}=\sum_{j=1}^{b}(\tau\beta)_{ij}=0.
$$

Em um experimento com dois fatores fixos cruzados, os efeitos de linhas e colunas (ou fatores A e B, respectivamente) são de igual interesse. Mais especificamente, estamos interessados em testar a hipótese de igualdade das linhas, isto é,

- **Para o Fator A:** hipótese de igualdade das linhas
    - H0: As médias das diferentes condições de A são iguais $\mu_{A1} = \mu_{A2} = \mu_{A3}$.
    - H1: Pelo menos uma média de A é diferente.
$$
       {
    \left\{\begin{array}{lcc}
    H_{0}: \tau_{1}=\tau_{2}=\dots=\tau_{a}=0 \\
    H_{1}: \tau_{i}\neq 0 \mbox{ para pelo menos um i}
    \end{array}\right.
    }
$$
- **Para o Fator B:** hipótese de igualdade das colunas
    - H0: As médias das diferentes condições de B são iguais $\mu_{B1} = \mu_{B2}$.
    - H1: Pelo menos uma média de B é diferente.
$$
       {
    \left\{\begin{array}{lcc}
    H_{0}: \beta_{1}=\beta_{2}=\dots=\beta_{b}=0 \\
    H_{1}: \beta_{j}\neq 0 \mbox{ para pelo menos um j}
    \end{array}\right.
    }
$$

Também temos interesse em verificar se existem efeitos de interação entre os fatores A e B (linhas e colunas), isto é,
- **Interação A x B:**
    - H0: Não há interação entre A e B (o efeito de A é o mesmo para todos os níveis de B e vice-versa).
    - H1: Há interação entre A e B (o efeito de A depende do nível de B e vice-versa).
$$
      {
        \left\{\begin{array}{lcc}
        H_{0}: (\tau\beta)_{ij}=0, ~~\forall~(i,j) \\
        H_{1}: (\tau\beta)_{ij} \neq 0 \mbox{ para pelo menos um par $(i,j)$}
        \end{array}\right.
        }
$$
**Soma de quadrados**: $SQTotal = SQFatorA+SQFatorB+SQIntAB+SQRes.$, com g.l.: $abn-1 = (a-1) + (b-1) + (a-b)(b-1) + ab(n-1)$

# Exemplo:
```{r}
library(planex)
library(agricolae)

data("queima")
glimpse(queima)
```

***Exercício 14.4***: Um experimento foi conduzido para determinar se a temperatura (°C) de queima ou a posição da fornalha afetam a densidade de um ânodo de carbono. Análise adequadamente os dados provenientes desse experimento, apresentando as suas conclusões.

```{r}
modelo = aov(densidade~posicao*temperatura, data=queima)
summary(modelo)
interactionPlot(modelo)
```

```
                    Df Sum Sq Mean Sq F value Pr(>F)
posicao              1   7160    7160   0.105  0.750
temperatura          1    234     234   0.003  0.954
posicao:temperatura  1    234     234   0.003  0.954
Residuals           14 951063   67933
```
![[5.1 Delineamentos com dois fatores fixos cruzados-20240722191332810.webp|500]]
## Podemos concluir, a tabela ANOVA, que:

- o fator temperatura e posição são significativos, logo, não rejeitamos **a hipótese de igualdade de linhas** e a **hipótese de igualdade de colunas**, então aceitamos $H_{0}: \tau_{1}=\tau_{2}=\dots=\tau_{a}=0$ e $H_{0}: \beta_{1}=\beta_{2}=\dots=\beta_{b}=0$

- IntAB (a interação entre os dois fatores) não são é significativa, logo, rejeitamos $H_{0}: (\tau\beta)_{ij}=0, ~~\forall~(i,j)$

lembrando apenas que: $$SQTotal = SQFatorA+SQFatorB+SQIntAB+SQRes$$
### Podemos concluir, com o gráfico, que:
- Há um efeito principal significativo no fator "posição", já que há uma diferença clara nas médias entre o ponto 1 e o ponto 2.  
- Há também um efeito principal significativo no fator "temperatura", já que as médias estão em níveis diferentes.
- Já que as linhas são relativamente paralelas, temos um indicador de que a interação entre posição e temperatura não é forte; os efeitos dos fatores é o mesmo para todas as interações

## Agora, podemos fazer a ANOVA
 Devido à ausência de interação significativa, podemos analisar cada fator separadamente. Para comparar os níveis do fator AA, podemos utilizar todos os dados disponíveis, independentemente dos níveis de BB, e vice-versa. Caso contrário, devemos realizar comparações múltiplas dentro de cada combinação dos níveis de A e B. Cada combinação dos níveis de A e B deve ser analisada separadamente para entender as diferenças entre as médias
 
```{r}
summary(LSD.test(modelo, "posicao"))
```

|     | densidade | groups |     |     |
| --- | --------- | ------ | --- | --- |
| 1   | 729.8889  | a      |     |     |
| 2   | 690.0000  | a      |     |     |

```{r}
summary(LSD.test(modelo, "temperatura"))
```
 
 
|     | densidade | groups |     |     |
| --- | --------- | ------ | --- | --- |
| 825 | 1034.0000 | a      |     |     |
| 800 | 552.3333  | b      |     |     |
| 850 | 543.5000  | b      |     |     |