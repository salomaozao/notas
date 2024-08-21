***Pertence à: [[Processos Estocásticos]]***

O teorema ergódico é um princípio fundamental em teoria das probabilidades e processos estocásticos. Em termos simples, ele afirma que, sob certas condições, as médias temporais de uma função de um processo estocástico convergem para as médias esperadas no espaço de probabilidade, ou seja, a média amostral de uma função ao longo do tempo tende à esperança matemática dessa função.

#### Aplicação no Contexto de Amostragem Posterior

Quando não podemos calcular a distribuição posterior explicitamente (em forma fechada), usamos métodos como Markov Chain Monte Carlo ([[MCMC]]) para gerar amostras dessa distribuição. Essas amostras nos permitem estimar momentos (como a média, variância, etc.) e outras quantidades de interesse da distribuição posterior.

#### Como o Teorema Ergódico Ajuda

1. **Médias Amostrais**: O teorema ergódico nos garante que a média das amostras geradas pelo algoritmo de MCMC converge para a média verdadeira da distribuição posterior conforme o número de amostras aumenta.
    
2. **Estimativas de Momentos**: Podemos estimar os momentos da distribuição (por exemplo, a média, variância) a partir das amostras geradas. A média amostral dos momentos convergirá para os momentos verdadeiros da distribuição posterior.
    
3. **Outras Quantidades de Interesse**: Além dos momentos, outras quantidades como quantis, intervalos de confiança, etc., também podem ser estimadas usando as amostras geradas.