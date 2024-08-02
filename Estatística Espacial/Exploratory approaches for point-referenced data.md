<aside>
📖 **EDA**

Exploratory data analysis (EDA) tools are routinely implemented in the process of analyzing
one- and two-sample data sets, regression studies, generalized linear models, etc

</aside>

#### First Law of Geostatistics

#### 2.3.1 Basic techniques

The data is partitioned into a **mean term and an error term**. The mean corresponds to global (or first-order) behavior, while the error captures local (or second-order) behavior through a covariance function. EDA tools are available to examine both first- and second-order behavior.

![*p.33*](Untitled%2030.png)

*p.33*

![Untitled](Untitled%2031.png)

#### 2.3.1 Directional semivariograms

**Outra função de covariância entre duas distribuições:**

![*p.36 - eq 2.12*](Untitled%2032.png)

*p.36 - eq 2.12*

where again N (tk) = {(si, sj ) : ||si − sj || ∈ Ik} for k = 1, . . . , K, Ik indexes the kth bin, and there are Nk pairs of points falling in this bin. 

é uma generalização espacial de um autocorrelação defasada (lagged) na análise de série temporal. Since ^c uses a common ¯Y for all Y (si), it may be safer to employ (2.12) on the residuals

We note that the empirical covariance function is not used much in practice; the empirical variogram is much more common. Moreover, two further issues arise: first, how should we definê C(0), and second, regardless of this choice, we note that̂ γ(tk ) does not equal̂ C(0) −̂ C(tk), k = 1, . . . , K

![Untitled](Untitled%2033.png)

#### 2.3.2 Assessing anisotropy

![*p.37*](Untitled%2034.png)

*p.37*

We illustrate various **EDA techniques** to assess **anisotropy** using sampling of scallop abun dance on the continental shelf off the coastline of the northeastern U.S. The data comes
from a survey conducted by the Northeast Fisheries Science Center of the National Marine Fisheries Service. Figure 2.8 shows the sampling sites for 1990 and 1993. We see much
more sampling in the southwest to northeast direction than in the northwest to southeast direction. Evidently, it is more appropriate to follow the coastline in searching for scallops.

#### 2.3.2.1 Directional semivariograms and rose diagramsaz

he most common EDA technique for assessing anisotropy involves use of directional semivariograms. Typically, one chooses angle classes ηi ± ǫ, i = 1, . . . , L where ǫ is the halfwidth of the angle class and L is the number of angle classes. For example, a common choice of angle classes involves the four cardinal directions measured counterclockwise from the x-axis (0◦, 45◦, 90◦, and 135◦)

For a given angle class, the Matheron empirical semivariogram (2.9) can be used to provide a directional semivariogram for angle ηi. Theoretically, all types of anisotropy can be assessed from these directional semivariograms; however, in practice determining whether the sill, nugget, and/or range varies with direction can be difficult.

In particular, it is unclear how much variability will arise in directional variograms generated under **isotropy** 

<aside>
📖 **Revisando:** um variograma é isotrópico quando seu semivariograma depende apenas no vetor de separação ||h||, um semivariograma anisotrópico depende também na direção

</aside>

embora a isotropia implique que não deveria haver diferença significativa na variabilidade em diferentes direções, pode haver incerteza ou dificuldade em prever exatamente a quantidade de variabilidade que se observará nos variogramas direcionais devido a fatores como amostragem limitada ou ruído nos dados

We caution however that it is dangerous to read too much significance and interpretation into directional variograms. For example, from Figure 2.8, as noted above, we see far more sampling at greater distances in the southwest-northeast direction than in the northwest southeast direction. Moreover, no sample sizes (and thus no assessments of variability) are attached to these pictures. Directional variograms from data generated under a simple isotropic model will routinely exhibit differences of the magnitudes seen in Figure 2.9(a). Furthermore, it seems difficult to draw any conclusions regarding the presence of geometric anisotropy from this figure.

![*p.39 - fig.2,9*](Untitled%2035.png)

*p.39 - fig.2,9*

Possible conclusions from the figure are: the variability in the 45◦ direction (parallel to the coastline) is significantly less than in the other three directions and the variability perpendicular to the coastline (135◦) is very erratic, possibly exhibiting sill anisotropy.

**Direcional Variograms**: Um variograma direcional é uma ferramenta utilizada em geoestatística para medir a variabilidade espacial de um dado em diferentes direções. Em vez de medir a variabilidade em todas as direções ao mesmo tempo (como em um variograma isotrópico), um variograma direcional mede a variabilidade ao longo de direções específicas, como norte-sul ou leste-oeste.

#### 2.3.2.2 Empirical semivariogram contour (ESC) plots 🟠|

A more informative method for assessing anisotropy is a contour plot of the empirical
semivariogram surface in R²
$x_1 + x_2^3$

