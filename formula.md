$$p\big(\boldsymbol{x}_{0:N}\big)=p\big(\boldsymbol{x}_N\big)\prod_{n=1}^N p\big(\boldsymbol{x}_{n-1} \vert \boldsymbol{x}_n\big)$$

$$p\big(\boldsymbol{x}_{n-1} \vert \boldsymbol{x}_n \big)=\mathcal{N} \big( \boldsymbol{x}_{n-1} \vert \boldsymbol{\mu}_n \big( \boldsymbol{x}_n \big), \boldsymbol{\Sigma}_n \big( \boldsymbol{x}_n \big) \big)$$

$$q\big(\boldsymbol{x}_{1:N} \vert \boldsymbol{x}_0\big)$$

$$q(\boldsymbol{x}_0)$$\

$$\lambda = \big( \lambda_1, \dots, \lambda_N \big) \in \mathbb{R}_{\geq 0}^{N}$$

$$q\big(\boldsymbol{x}_{1:N} \vert \boldsymbol{x}_0 \big)=q\big( \boldsymbol{x}_N \vert \boldsymbol{x}_0 \big) \prod_{n=2}^{N} q\big( \boldsymbol{x}_{n-1} \vert \boldsymbol{x}_n, \boldsymbol{x}_0 \big)$$

$$q\big( \boldsymbol{x}_N \vert \boldsymbol{x}_0 \big)=\mathcal{N} \big( \boldsymbol{x}_N \vert \sqrt{\overline{\alpha}_N} \boldsymbol{x}_0, \overline{\beta}_N \boldsymbol{I} \big)$$

$$q\big( \boldsymbol{x}_{n-1}, \boldsymbol{x}_n, \boldsymbol{x}_0 \big)=\mathcal{N} \big( \boldsymbol{x}_{n-1} \vert \tilde{\boldsymbol{\mu}}_n (\boldsymbol{x}_n, \boldsymbol{x}_0), \lambda_n^2 \boldsymbol{I} \big)$$


$$\tilde{\boldsymbol{\mu}}_n \big( \boldsymbol{x}_n, \boldsymbol{x}_0 \big)=\sqrt{\overline{\alpha}_{n-1}}\boldsymbol{x}_0 + \sqrt{\overline{\beta}_{n-1} - \lambda_n^2}.\dfrac{\boldsymbol{x}_n - \sqrt{\overline{\alpha}_n}\boldsymbol{x}_0}{\sqrt{\overline{\beta}_n}}$$


$$\overline{\alpha}_1, \overline{\alpha}_2, \dots, \overline{\alpha}_N \in (0, 1)$$

$$\overline{\beta}_n := 1 - \overline{\alpha}_n$$

$$q\big( \boldsymbol{x}_n \vert \boldsymbol{x}_0 \big)=\mathcal{N} \big( \boldsymbol{x}_n \vert \sqrt{\overline{\alpha}_n} \boldsymbol{x}_0, \overline{\beta}_n \boldsymbol{I} \big)$$


$$\boldsymbol{x}_n = \sqrt{\overline{\alpha}_n} \boldsymbol{\overline{\beta}_n} \boldsymbol{\epsilon}_n, \boldsymbol{\epsilon}_n \sim \mathcal{N}(\boldsymbol{0}, \boldsymbol{I})$$

$$\alpha_n := \overline{\alpha}_n / \overline{\alpha}_{n-1}, \beta_n := 1 - \alpha_n$$

$$\tilde{\beta}_n := \dfrac{\overline{\beta}_{n-1}}{\overline{\beta}_n}\beta_n$$

$$q\big( \boldsymbol{x}_n \vert \boldsymbol{x}_{n-1} \big)=\mathcal{N} \big( \bold{x}_n \vert \sqrt{\alpha}_n \boldsymbol{x}_{n-1}, \beta_n \boldsymbol{I} \big)$$

$$L_{\mathrm{elbo}}=\mathbb{E}_q \log \dfrac{p(\bold{x}_{0:N})}{q(\bold{x}_{1:N}\vert \bold{x}_0)}$$


$$\max_{\lbrace \boldsymbol{\mu}_n, \boldsymbol{\Sigma}_n \rbrace_{n=1}^N} L_{\mathrm{elbo}} \leftrightarrow \min_{\lbrace \boldsymbol{\mu}_n, \boldsymbol{\Sigma}_n \rbrace_{n=1}^N} D_{KL} \big( q(\boldsymbol{x}_{0:N}) \Vert p(\boldsymbol{x}_{0:N}) \big) $$


$$\boldsymbol{\Sigma}_n(\boldsymbol{x}_n)=\sigma_n^2 \boldsymbol{I}$$


$$\boldsymbol{\mu}_n^{\ast} (\boldsymbol{x}_n)$$


$$\boldsymbol{\mu}_n^{\ast} (\boldsymbol{x}_n)=\tilde{\boldsymbol{\mu}}_n \Bigg( \boldsymbol{x}_n, \dfrac{1}{\sqrt{\overline{\alpha}_n}} \Big( \boldsymbol{x}_n - \sqrt{\overline{\beta}_n} \mathbb{E}_{q(\boldsymbol{x}_0 \vert \boldsymbol{x}_n)} \lbrack \boldsymbol{\epsilon}_n \rbrack \Big) \Bigg)$$


$$\sigma_n^{\ast 2}=\lambda_n^2 + \gamma_n^2 \dfrac{\overline{\beta}_n}{\overline{\alpha}_n} \Bigg( 1 - \mathbb{E}_{q(\boldsymbol{x}_n)} \dfrac{\lVert \mathbb{E}_{q(\boldsymbol{x}_0 \vert \boldsymbol{x}_n)} \lbrack \boldsymbol{\epsilon}_n \rbrack\rVert_2^2}{d} \Bigg)$$


$$\boldsymbol{\epsilon}_n = \dfrac{\boldsymbol{x}_n - \sqrt{\overline{\alpha}_n} \boldsymbol{x}_0}{\sqrt{\overline{\beta}_n}}$$


$$\gamma_n = \sqrt{\overline{\alpha}_{n-1}} - \sqrt{\overline{\beta}_{n-1} - \lambda_n^2}\sqrt{\dfrac{\overline{\alpha}_n}{\overline{\beta}_n}}$$


$$\hat{\boldsymbol{\mu}}_n(\boldsymbol{x}_n)=\tilde{\boldsymbol{\mu}}_n \Bigg( \boldsymbol{x}_n, \dfrac{1}{\sqrt{\overline{\alpha}_n}} \Big( \bold{x}_n - \sqrt{\overline{\beta}_n} \hat{\boldsymbol{\epsilon}}_n(\boldsymbol{x}_n) \Big) \Bigg)$$


$$\min_{\lbrace \hat{\boldsymbol{\epsilon}}_n  \rbrace_{n=1}^N} \mathbb{E}_n  \mathbb{E}_{q(\boldsymbol{x}_0, \boldsymbol{x}_n)} \lVert \boldsymbol{\epsilon}_n - \hat{\boldsymbol{\epsilon}}_n (\boldsymbol{x}_n) \rVert_2^2$$

$$\hat{\sigma}_n^{2}=\lambda_n^2 + \gamma_n^2 \dfrac{\overline{\beta}_n}{\overline{\alpha}_n} \Bigg( 1 - \mathbb{E}_{q(\boldsymbol{x}_n)} \dfrac{\lVert \hat{\boldsymbol{\epsilon}}_n (\boldsymbol{x}_n)\rVert_2^2}{d} \Bigg)$$

$$\overline{\alpha}_n$$

$$\overline{\beta}_n$$

$$\tilde{\boldsymbol{\mu}}_n (\boldsymbol{x}_n, \boldsymbol{x}_0)$$