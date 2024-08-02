Para entender a **cointegration**, é importante primeiro entender o conceito de **[[Estacionariedade de Séries Temporais]]**.  Muitas séries temporais financeiras, como preços de ações ou taxas de câmbio, são não estacionárias, o que significa que essas propriedades podem mudar ao longo do tempo.

### Cointegration e Equilíbrio de Longo Prazo

Cointegration sugere que mesmo que duas séries temporais, $X_t$​ e $Y_t$​, sejam não estacionárias, existe uma combinação linear dessas séries que é estacionária. Matematicamente, dizemos que $X_t$​ e $Y_t$​ são cointegradas se existe um coeficiente $β$ tal que:

$Z_t = Y_t - \beta X_t$​

onde $Z_t$​ é uma série estacionária.

### Aplicação da Cointegration

1. **Modelagem e Previsão**: Cointegration é frequentemente usada em modelos econométricos para ==capturar relações de longo prazo entre variáveis econômicas==. Por exemplo, o consumo e a renda podem ser cointegrados porque, no longo prazo, eles tendem a se mover juntos, mesmo que no curto prazo possam divergir.
    
2. **Arbitragem Estatística**: Em finanças, a cointegration é usada em estratégias de arbitragem estatística, como pares trading. Se duas ações são cointegradas, elas tendem a se mover juntas. Se os preços dessas ações divergem temporariamente, um trader pode vender a ação que está sobrevalorizada e comprar a que está subvalorizada, esperando que os preços voltem ao equilíbrio.
    
3. **Teste de Cointegration**: Existem vários testes para verificar a cointegration, como o teste de Engle-Granger e o teste de Johansen. Esses testes ajudam a determinar se as séries temporais têm uma relação de equilíbrio de longo prazo.
    

### Exemplo de Cointegration

Suponha que temos duas séries temporais: o preço de uma ação de uma empresa de petróleo (POilP_{Oil}POil​) e o preço do barril de petróleo (PBarrelP_{Barrel}PBarrel​). Embora cada uma dessas séries possa ser não estacionária, o preço da ação pode ser cointegrado com o preço do barril de petróleo, refletindo a relação de longo prazo entre os dois.

$P_{Oil,t} = \alpha + \beta P_{Barrel,t} + \epsilon_t$

Se ϵ for estacionário, então $P_{Oil}​$ e $P_{Barrel}$​ são cointegrados.
