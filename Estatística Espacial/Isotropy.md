- **Definition**: In the context of spatial data, isotropy means that the spatial correlation or variability of a variable is the same in all directions.
- **Implications**: If a spatial process is isotropic, the variogram or covariance function used to model the spatial correlation will look the same regardless of the direction in which it is computed. This implies that the spatial structure does not change with direction.
- **Example**: Suppose we are measuring soil moisture levels across a field. If the process is isotropic, the variability in soil moisture levels at a given distance apart would be the same whether we measure north-south, east-west, or in any other direction.

If the semivariogram function γ (h) depends upon the separation vector only through its length ||h||, then we say that **the variogram is isotropic**; that is, if γ (h) is a real-valued function of a univariate argument, and can be written as γ (||h||). If not, we say it is anisotropic

**Isotropic variograms** are popular because of their simplicity, interpretability, and, in particular, because a number of relatively simple parametric forms are available as candidates for the semivariogram. **Denoting ||h|| by d for notational simplicity**, we now consider a few of the more important such forms.


📖 Concepts

### 1. Nugget (Pepita) **τ²**

![Untitled](91a89ef6-c5ca-4696-8090-4090b622b88a.png)

**The nugget** é o valor mínimo, por isso, subtraindo um ao outro, obtemos a variância de ***s***

- **Definição**: O nugget representa a variabilidade espacial em escalas muito pequenas, que é menor do que a menor distância de amostragem. Ele pode ser interpretado como o efeito de pequenas variações locais, erros de medição ou outras variabilidades não detectadas devido à escala de amostragem.
- **Visualização no Variograma**: No gráfico do variograma, o nugget é o valor da semivariância quando a distância h é zero (ou próximo de zero). Se o variograma começa acima do eixo y (ou seja, não parte do zero), o valor inicial é o nugget.
- **Interpretação**: Um nugget grande indica que há uma significativa variabilidade em pequenas escalas ou erros de medição elevados.

### 2. Sill (Platô)

(treshold - limite) é o valor máximo que a função semivariograma atinge

![*The sill minus the nugget, which is simply σ² in this case, is called the partial sill*](Untitled%2017%201.png)

*The sill minus the nugget, which is simply σ² in this case, is called the partial sill*

- **Definição**: O sill é o valor da semivariância em que o variograma se estabiliza (atinge um platô) à medida que a distância h aumenta. Representa a variabilidade total da variável, incluindo a variabilidade de longo alcance.
- **Visualização no Variograma**: No gráfico, o sill é a altura do platô onde a semivariância se estabiliza. Este valor é essencialmente a variância total dos dados quando a distância entre pontos amostrados é grande o suficiente para não haver mais correlação espacial.
- **Interpretação**: O sill reflete a variabilidade inerente na totalidade do conjunto de dados. Ele é a soma do nugget e da variabilidade espacial.

### 3. Range (Alcance) *R*

The range is the minimal value for ***d*** at wich γ(d) **reaches the sill**

- **Definição**: O range é a distância além da qual a semivariância atinge o sill e se estabiliza. Até esta distância, os pontos ainda apresentam correlação espacial; além desta, os pontos são considerados independentes entre si.
- **Visualização no Variograma**: No gráfico, o range é a distância no eixo x onde o variograma atinge o sill pela primeira vez. Em um variograma esférico, esta é a distância onde a curva do variograma se nivela.
- **Interpretação**: O range define a extensão do efeito espacial. Dados amostrais localizados dentro dessa distância estão correlacionados, enquanto dados além dessa distância não apresentam correlação espacial significativa.
- **Sill** *(ceil)*
    
    
- **Range ( *R* ):**
    - **Nugget ( τ² **):**




#IC 
### Formas de Variogramas Isotrópicos / selection of models for the variogram: (*p.26, 27)*

1. **Linear**
    
    ![Untitled](Untitled%2018%201.png)
    
    Fazendo d → 0, obtemos o ***nugget:*** τ²
    
    Note that γ (d) → ∞ as d → ∞, and so this semivariogram does not correspond to a weakly stationary process (although it is intrinsically stationary).
    
    *This semivariogram is plotted in Figure 2.1(a) using the parameter values τ 2 = 0.2 and σ2 = 0.5.*
    
2. **Spherical**:
    
    ![Untitled](Untitled%2019%201.png)
    
    The spherical semivariogram is valid in r = 1, 2, or 3 dimensions, but for r ≥ 4 it fails to correspond to a spatial variance matrix that is positive definite (as required to specify a valid joint probability distribution). This variogram owes its popularity largely to the fact that it offers clear illustrations of the nugget, sill, and range, three characteristics traditionally associated with variograms
    
    *consider Figure 2.1(b), which plots the spherical semivariogram using the parameter values τ 2 = 0.2, σ2 = 1, and φ = 1.*
    
3. **Exponential**
    
    ![Untitled](Untitled%2020.png)
    
    The exponential has an advantage over the spherical in that it is simpler in functional formwhile still being a valid variogram in all dimensions (and without the spherical’s finite range requirement)
    
    *note from Figure 2.1(c), which plots this semivariogram assuming τ 2 = 0.2, σ2 = 1, and φ = 2,*
    
    the sill is only reached asymptotically; strictly speaking, the range R = 1/φ is infinite. In cases like this, **the notion of an effective range is often used**, i.e., the distance at which there is essentially no lingering (persistent) spatial correlation. To make this notion precise, we must convert from γ scale to C scale (possible here since limd→∞ γ(d) exists; the exponential is not only intrinsically but also weakly stationary)
    
    ![Untitled](Untitled%2021.png)
    
    ![9edf8y18.bmp](9edf8y18.bmp)
    

![Untitled](Untitled%2022.png)

<aside>
❗ both R and φ are sometimes referred to as the range parameter, although φ is often more accurately referred to as the decay parameter

</aside>

![Untitled](Untitled%2023.png)

![p.29](Untitled%2024.png)

p.29

