one might well wonder how we choose one of them for a given data set, or whether the data can really distinguish them. A variogram model is chosen by plotting the ***empirical semivariogram.***  A simple nonparametric estimate
of the semivariogram, and then comparing it to the various theoretical shapes available from the choices in the previous subsection. The customary empirical semivariogram is:

![Untitled](Untitled%2025.png)

where N (d) is the set of pairs of points such that ||si − sj || = d, and |N (d)| is the number of pairs in this set

Notice that, unless the observations fall on a regular grid, the distances between the pairs will all be different, so this will not be a useful estimate as it stands. Instead we would “grid up” the d-space into intervals I1 = (0, d1), I2 = (d1, d2), and so forth, up to IK = (dK−1, dK ) for some (typically regular) grid, we then alter our definition of N (d) to:

![*p.30 - N(dk) é a distância entre dois pontos si e sj*](Untitled%2026.png)

*p.30 - N(dk) é a distância entre dois pontos si e sj*

Outra proposta para o semivariograma ^y(d) é: 

![Untitled](Untitled%2027.png)

Que é menos sensível a outliers e outros.

