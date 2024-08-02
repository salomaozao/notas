In this section we describe the **classical** (i.e., minimum mean-squared error) approach to **spatial prediction** in the point-referenced data setting. The approach is commonly referred to as **kriging**

The problem is one of optimal spatial prediction: given observations of a random field Y = (Y (s1) , . . . , Y (sn))′, how do we predict the variable Y at a site s0 where it has not been observed? In other words, what is the best predictor of the value of Y (s0) based upon the data y?

<aside>
📖 ***Loss:*** O quanto a função de predição diferencia dos dados observados.

</aside>

### 2.4.2 Ordinary Kriging

**Ordinary Kriging (OK)** é a forma mais comum de kriging, amplamente utilizada devido à sua flexibilidade em lidar com um valor médio desconhecido, mas constante, do processo espacial. Aqui estão os pontos chave:

1. **Assunções**:
    - O processo tem uma média constante, mas desconhecida, ***μ***.
    - O processo é **estacionário de segunda ordem**, o que significa que a função de covariância entre dois pontos depende apenas da distância entre eles, não de suas localizações absolutas.
2. **Fórmula de Predição**:
A predição em um ponto não amostrado s_0 é dada por uma combinação linear ponderada dos valores observados:
    
   ![Untitled](IC%2058bd3e7e9f8242578ff35aa9ba4ee614/Untitled%2036.png)
    
    onde λi\lambda_iλi são os pesos de kriging atribuídos a cada observação Y(si)Y(s_i)Y(si).
    

1. **Determinação dos Pesos**:
    
    Os pesos são determinados resolvendo o sistema de equações de kriging, que é baseado no semivariograma. As equações garantem que a predição seja a combinação linear dos valores observados com a menor variância possível, sujeita à restrição de que a soma dos pesos seja igual a 1:
    
    ![γ(si−s0) é a semivariância entre o ponto sis_isi e o ponto de predição s0s.](Untitled%2037.png)
    
    γ(si−s0) é a semivariância entre o ponto sis_isi e o ponto de predição s0s.
    
    onde **γ** é a **semivariância** e **μ** é um **multiplicador de Lagrange**.
    
    <aside>
    📖 O **multiplicador de Lagrange μ** pode ser interpretado como um parâmetro adicional que ajusta os pesos para garantir que a restrição seja satisfeita. 
    A função de Lagrage (L) pode ser descrita como:
    
    ![Untitled](Untitled%2038.png)
    
    </aside>
    

### 2.4.3 Semivariograma

O **semivariograma** é crucial na krigagem que descreve a dependência espacial dos dados. Lembrando que o semivariograma tem, como componentes, o sill, nugget e range. O semivariograma γ(h) é definido como:

![A forma do semivariograma influencia diretamente a determinação dos pesos λi](Untitled%2039.png)

A forma do semivariograma influencia diretamente a determinação dos pesos λi

🟠

