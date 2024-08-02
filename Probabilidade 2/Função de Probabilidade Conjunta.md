***Pertence a: [[Probabilidade 2]]***
A função de probabilidade conjunta descreve a probabilidade de eventos combinados em variáveis aleatórias múltiplas. Aqui está um resumo detalhado em tópicos sobre a função de probabilidade conjunta:

#### Definição
- **Função de Probabilidade Conjunta**: 
  - Para duas variáveis aleatórias \( X \) e \( Y \), a função de probabilidade conjunta \( P(X = x, Y = y) \) fornece a probabilidade de \( X \) ser igual a \( x \) e \( Y \) ser igual a \( y \) simultaneamente.
  - Denotada como \( P(X = x, Y = y) \) ou \( P_{X,Y}(x, y) \).

#### Propriedades
- **Não-negatividade**:
  - \( P_{X,Y}(x, y) \geq 0 \) para todos os valores \( x \) e \( y \).
- **Soma das Probabilidades**:
  - Para variáveis aleatórias discretas, a soma das probabilidades conjuntas sobre todos os possíveis pares \((x, y)\) deve ser igual a 1.
    $$    \sum_{x} \sum_{y} P_{X,Y}(x, y) = 1  $$
  - Para variáveis contínuas, a integral sobre todas as combinações possíveis de \( x \) e \( y \) deve ser igual a 1.
    $$    \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f_{X,Y}(x, y) \, dx \, dy = 1
    $$


#### Distribuições Marginais
- **Distribuição Marginal de \( X \)**:
  - Obtida somando (ou integrando) a função de probabilidade conjunta sobre todos os possíveis valores de \( Y \).
    $$
    P_X(x) = \sum_{y} P_{X,Y}(x, y) \quad \text{(discreta)}
    $$
    $$
    f_X(x) = \int_{-\infty}^{\infty} f_{X,Y}(x, y) \, dy \quad \text{(contínua)}
    $$
- **Distribuição Marginal de \( Y \)**:
  - Obtida somando (ou integrando) a função de probabilidade conjunta sobre todos os possíveis valores de \( X \).
    $$
    P_Y(y) = \sum_{x} P_{X,Y}(x, y) \quad \text{(discreta)}
    $$
    $$
    f_Y(y) = \int_{-\infty}^{\infty} f_{X,Y}(x, y) \, dx \quad \text{(contínua)}
    $$

#### Independência
- **Variáveis Independentes**:
  - Duas variáveis aleatórias \( X \) e \( Y \) são independentes se e somente se a função de probabilidade conjunta é o produto das funções de probabilidade marginais.
    $$
    P_{X,Y}(x, y) = P_X(x) \cdot P_Y(y) \quad \text{(discreta)}
    $$
    $$
    f_{X,Y}(x, y) = f_X(x) \cdot f_Y(y) \quad \text{(contínua)}
    $$

#### Função de Densidade de Probabilidade Conjunta (Contínua)
- **Função de Densidade de Probabilidade Conjunta (f.d.p.)**:
  - Para variáveis contínuas \( X \) e \( Y \), a função de densidade de probabilidade conjunta \( f_{X,Y}(x, y) \) é a derivada segunda da função de distribuição conjunta \( F_{X,Y}(x, y) \).
    $$
    f_{X,Y}(x, y) = \frac{\partial^2}{\partial x \, \partial y} F_{X,Y}(x, y)
    $$

#### Propriedades Esperadas
- **Esperança de Variáveis Conjuntas**:
  - A esperança conjunta de uma função \( g(X, Y) \) é dada por:
    $$
    E[g(X, Y)] = \sum_{x} \sum_{y} g(x, y) P_{X,Y}(x, y) \quad \text{(discreta)}
    $$
    $$
    E[g(X, Y)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} g(x, y) f_{X,Y}(x, y) \, dx \, dy \quad \text{(contínua)}
    $$

#### Funções de Distribuição
- **Função de Distribuição Conjunta (f.d.a.)**:
  - A função de distribuição acumulada conjunta \( F_{X,Y}(x, y) \) para variáveis \( X \) e \( Y \) é definida como:
    $$
    F_{X,Y}(x, y) = P(X \leq x, Y \leq y)
    $$
  - Para variáveis discretas:
    $$
    F_{X,Y}(x, y) = \sum_{x_i \leq x} \sum_{y_j \leq y} P_{X,Y}(x_i, y_j)
    $$
  - Para variáveis contínuas:
    $$
    F_{X,Y}(x, y) = \int_{-\infty}^{x} \int_{-\infty}^{y} f_{X,Y}(x', y') \, dx' \, dy'
    $$

#### Exemplo Prático (Discreta)
- **Exemplo**:
  - Suponha duas variáveis aleatórias \( X \) e \( Y \) que representam o número de caras obtidas em duas lançadas de uma moeda.
  - \( X \) e \( Y \) podem assumir valores de 0 a 1.
  - A função de probabilidade conjunta \( P_{X,Y}(x, y) \) pode ser representada em uma tabela:
    $$
    \begin{array}{c|cc}
    P_{X,Y}(x, y) & y=0 & y=1 \\
    \hline
    x=0 & \frac{1}{4} & \frac{1}{4} \\
    x=1 & \frac{1}{4} & \frac{1}{4} \\
    \end{array}
    $$
  - A soma das probabilidades individuais deve ser 1:
    $$
    \sum_{x} \sum_{y} P_{X,Y}(x, y) = \frac{1}{4} + \frac{1}{4} + \frac{1}{4} + \frac{1}{4} = 1
    $$

#### Exemplo Prático (Contínua)
- **Exemplo**:
  - Suponha duas variáveis contínuas \( X \) e \( Y \) com uma função de densidade conjunta \( f_{X,Y}(x, y) = e^{-(x+y)} \) para \( x \geq 0 \) e \( y \geq 0 \).
  - A função de densidade deve satisfazer a condição de normalização:
    $$
    \int_{0}^{\infty} \int_{0}^{\infty} e^{-(x+y)} \, dx \, dy = 1
    $$
  - Para encontrar a distribuição marginal de \( X \):
    $$
    f_X(x) = \int_{0}^{\infty} e^{-(x+y)} \, dy = e^{-x} \int_{0}^{\infty} e^{-y} \, dy = e^{-x}
    $$
  - Similarmente, para \( Y \):
    $$
    f_Y(y) = \int_{0}^{\infty} e^{-(x+y)} \, dx = e^{-y} \int_{0}^{\infty} e^{-x} \, dx = e^{-y}
    $$

### Conclusão
A função de probabilidade conjunta é fundamental na teoria das probabilidades e estatísticas, fornecendo uma maneira de analisar a interdependência entre duas ou mais variáveis aleatórias. Ela permite calcular probabilidades de eventos combinados e derivar distribuições marginais e esperanças de funções conjuntas, sendo essencial para a modelagem de fenômenos estocásticos ([[Processos Estocásticos]]).