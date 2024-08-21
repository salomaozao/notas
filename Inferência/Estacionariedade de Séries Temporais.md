***Faz parte de [[__Índices/Inferência]]***

Estacionariedade é um conceito fundamental na análise de [[Séries Temporais]] que se refere à propriedade de uma série temporal cujas características estatísticas, como média, variância e autocorrelação, permanecem constantes ao longo do tempo. A análise de séries temporais estacionárias é mais simples e previsível, pois suas propriedades não mudam, facilitando a modelagem e a previsão. Existem diferentes tipos de estacionariedade, cada um com suas próprias características e implicações.
### Tipos de Estacionariedade

1. **Estacionariedade Estrita (ou Forte)**:
    
    - Uma série temporal é estritamente estacionária se a distribuição conjunta de quaisquer conjuntos de valores da série é a mesma, independentemente do tempo em que são observados.
    - Matemática: Se $(X_t,X_{t+1},…,X_{t+k})$ tem a mesma distribuição conjunta que $(X_{t+τ},X_{t+τ+1},…,X_{t+τ+k})$ para qualquer $τ$.
2. **Estacionariedade Fraca (ou Covariância-Estacionária)**:
    - Uma série temporal é fracamente estacionária se suas estatísticas de primeira e segunda ordem (média, variância e autocovariância) são constantes ao longo do tempo.
        - Média constante: $E[Xt]=μ$ para todo $t$.
        - Variância constante: $Var(Xt)=σ^2$ para todo $t$.
        - Autocovariância constante: $Cov(Xt,Xt+k)=γ(k)$ para todo $t$ e defasagem $k$.

***Veja também [[Transformando Séries Não Estacionárias em Estacionárias]]***