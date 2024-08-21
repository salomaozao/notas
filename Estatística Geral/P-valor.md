***Pertence à [[Estatística Geral]]***

 O valor de p é uma medida usada em testes estatísticos para avaliar a **força da evidência contra a hipótese nula**. 

- **Valor de p Pequeno (menor que $\alpha$)**: Sugere que os resultados observados são improváveis sob a hipótese nula. Isso indica evidências suficientes para rejeitar a hipótese nula em favor da hipótese alternativa.
- **Valor de p Grande ($\text{p-valor}>\alpha$)**: Sugere que os resultados observados são consistentes com a hipótese nula. Isso indica que não há evidências suficientes para rejeitar a hipótese nula.

***
Se tomarmos como, por exemplo:
```
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)   74.283      1.593   46.62  < 2e-16 ***
percentual    14.947      1.317   11.35 1.23e-09 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

podemos interpretar os **códigos de significância** como: 
- **" * * * "**: $p<0.0001$
- **" * * "**:  $0.001<p<0.01$
- **" * "**:  $0.01<p<0.05$
- **" . "**:  $0.05<p<0.1$
- **"  "**:  $p>0.1$
Temos, em ordem, alta significância (" * * * ") que rejeitamos $H_0$, até baixa significância ("  ") que não rejeitamos $H_0$.