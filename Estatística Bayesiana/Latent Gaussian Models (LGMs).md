
LGMs são uma classe de modelos hierárquicos onde as variáveis latentes seguem uma distribuição Gaussiana. Esses modelos são frequentemente usados em inferência Bayesiana e são uma parte importante da modelagem espacial e temporal.

A forma geral de um Modelo latente gaussiano é:
- **likelihood:** $\mathbf{y} | \mathbf{x}, \mathbf{\theta_2} \sim \prod_i \ p(y_i | \eta_i, \mathbf{\theta_2})$
- **Latent Field:** $\mathbf{x} | \mathbf{\theta_1} \sim p(\mathbf{x}|\mathbf{\theta_1}) = \mathcal{N}(0,\mathbf{\Sigma})$ 
- **Hyperpriors:** $\mathbf{{\theta}} = [\mathbf{\theta_1},\mathbf{\theta_2}]^T \sim p(\mathbf{\theta})$

is an observed dataset, are not covariates but rather is the joint distribution of all parameters in the linear predictor (including itself), and

are the hyperparameters of the latent field that are not Gaussian.
