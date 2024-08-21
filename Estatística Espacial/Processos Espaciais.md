Um **processo espacial** refere-se a uma coleção de variáveis aleatórias associadas a localizações específicas no espaço. Por exemplo, poderíamos ter um processo espacial que descreve a concentração de um poluente em diferentes pontos de uma cidade.

### Stationarity:

∀ h ∈ R^r:

The process is said to be ***strictly stationary*** (sometimes strong stationarity) if:

- the distribution of (Y (s1) , . . . , Y (sn)) = (Y (s1 + h) , . . . , Y (sn + h)).
    
    ![Untitled](Untitled%2012%201.png)
    
    A distribuição conjunta ([[Função de Probabilidade Conjunta]]) de qualquer conjunto de pontos no espaço é invariante sob translações **Ou seja,** a variância **depende apenas do deslocamento**, logo, E[Y(s)] é cont., logo μ(s)=μ .
    

A spatial process is called ***weakly stationary*** (or second-order stationarity) if:

- μ (s) ≡ μ
    - A média μ(s) é constante: μ(s)=μ.
- Cov (Y (s) , Y (s + h)) = C (h)
    - A função de covariância C(h) depende **apenas da distância** entre os pontos, não de sua localização absoluta: C(h)=Cov( Z(s), Z(s+h) ).

Weak stationarity implies that the covariance relationship between the values of the process at any two locations can be summarized by a covariance function C (h), and this function depends only on the separation vector h.

*The covariance function C(h) is sometimes referred to as the covariogram, especially when plotted graphically.)*

Assumindo que todas as variâncias existem, se um processo é fortemente estacionário, ele automaticamente satisfaz as condições para ser fracamente estacionário. 

![*p.23*](Untitled%2013%201.png)

*p.23*

No exemplo ao lado, temos o seguinte: Temos Yt, t=1, 2, …

- Se t for par: Yt ~ N(0, 1)
- Se t for ímpar Yt ~ {-1 OU 1}

Logo,

- É fracamente estacionária; pois Cov(t, t’) = 0 e a média é constante
- mas não é estritamente estacionária, pois Z(1, 3) ≠ Z(1+1, 3+1)

