# Notation

Notation follows the JMP (`literature/OMPSM_Franco.tex`) unless stated otherwise.
Blackboard bold is reserved for indices.
Add new symbols here when they are first introduced, with the section where they appear.

## Indices

| Symbol | Meaning |
|---|---|
| $j$ | Establishment |
| $c$ | Market ("city"): county or commuting zone |
| $n$ | Industry (sector) |
| $t$ | Year (not used in the JMP; introduced here for the time dimension) |
| $k$ | Polynomial order in the sieve, $k = 1,2,3$ |

## Demand

| Symbol | Meaning |
|---|---|
| $\Upsilon(\cdot)$ | Kimball (HDIA) aggregator: strictly increasing, concave, $\Upsilon(0)=0$ |
| $y_{jc}$, $Y_c$ | Per-capita consumption of variety $j$; per-capita local-goods bundle |
| $p_{jc}$ | Price of establishment $j$ in market $c$ |
| $\varphi(\cdot) \equiv (\Upsilon')^{-1}(\cdot)$ | Demand function: $y_{jc}/Y_c = \varphi(p_{jc}/\mathbb{D}_c)$ |
| $\mathbb{D}_c$ | Competition price index (the Lagrange multiplier over $Y_c$) |
| $\mathbb{P}_c$ | Ideal price index of the local-goods bundle |
| $\mathbb{C}_c \equiv W_c/\mathbb{D}_c$ | Competition index |
| $\sigma(\cdot)$ | Price elasticity of demand as a function of the relative price $p/\mathbb{D}$ |
| $\psi(\cdot)$ | Optimal relative price, $p_{jc}/\mathbb{D}_c = \psi(\mathbb{C}_c/z)$ |
| $\zeta(\cdot)$ | Inverse of $x\varphi(x)$; maps $s^y_{jc}\,\mathbb{P}_c/\mathbb{D}_c$ to $p_{jc}/\mathbb{D}_c$ |
| $\delta(\cdot)$ | Consumer-surplus ratio (area under demand over sales) |
| $\overline{p}$ | Choke price: $\varphi(\overline{p}) = 0$ |

## Production and estimation

| Symbol | Meaning |
|---|---|
| $\mu_{jc}$ | Markup (price over marginal cost) |
| $\beta$ ($\beta_n$) | Labor output elasticity (industry-specific in the multi-sector case) |
| $\omega_{jc}$ | Hicks-neutral productivity |
| $\nu_{jc}$ | Ex-post shock or measurement error in output |
| $\alpha^l_{jc} \equiv W_c l_{jc}/(p_{jc} y_{jc})$ | Labor expenditure share of sales (wage bill over sales) |
| $s^y_{jc}$ | Establishment sales share in market $c$ |
| $\varsigma_{k,c}$ | Market-specific sieve coefficients: $\varsigma_{k,c} = -\varsigma_k(\mathbb{P}_c/\mathbb{D}_c)^k$ |
| $\upsilon_{jc}$ | Composite error: measurement error plus sieve approximation error |
| $\mathcal{M}_c$ | Market-level aggregate markup: sales-weighted harmonic mean of $\mu_{jc}$ |

## Baseline framework (`paper/Scratch.tex`, Section `sec:baseline`)

Industry-indexed versions of the symbols above carry a subscript $n$ (for example $\Upsilon_n$, $\varphi_n$, $\sigma_n$, $\mu_n$, $\mathbb{P}_{nc}$, $\mathbb{D}_{nc}$).

| Symbol | Meaning |
|---|---|
| $C$, $N$ | Number of regions; number of industries |
| $L_c$ | Population of region $c$ |
| $I_c$ | Per-capita household income in region $c$ (taken as given) |
| $\theta_n$ | Cobb-Douglas expenditure share of industry $n$, $\sum_n \theta_n = 1$ |
| $\mathcal{J}_{nc}$ | Finite set of establishments in industry $n$, region $c$ |
| $y_{jnc}$, $Y_{nc}$ | Per-capita consumption of variety $j$; per-capita industry bundle |
| $q_{jnc} = L_c y_{jnc}$ | Total output (quantity sold) of establishment $j$ |
| $\lambda_{nc}$ | Multiplier in the household's lower-tier problem; $\mathbb{D}_{nc} \equiv \lambda_{nc}/Y_{nc}$ |
| $\mathcal{X}$, $\mathcal{X}^f \subseteq \mathcal{X}$ | Set of inputs; subset of flexible inputs (labor $l \in \mathcal{X}^f$) |
| $v^x_{jnc}$ | Quantity of input $x$ ($v^l_{jnc} = l_{jnc}$) |
| $W^x_c$ | Price of input $x$ in region $c$ ($W^l_c = W_c$) |
| $\beta^x_n$ | Output elasticity of input $x$ in industry $n$ |
| $\gamma_n \equiv \sum_x \beta^x_n$ | Returns to scale in industry $n$ |
| $\lambda_{jnc}$ | Marginal cost (multiplier in the cost-minimization problem) |
| $\alpha^x_{jnc} \equiv W^x_c v^x_{jnc}/(p_{jnc} q_{jnc})$ | Expenditure share of input $x$ in sales |

Departures from the JMP: here $\alpha^x$ uses total sales $p q$ in the denominator, where the JMP writes $p y$. The two are the same object, because the JMP's production function is in total quantities. The JMP's $\nu_{jc}$ (ex-post shock or measurement error) is not yet in the baseline framework.

Macro warning: in `preamble.tex`, `\D` is $\Delta$, not $\mathbb{D}$. Write `\mathbb{D}` in full. `\P` and `\C` are $\mathbb{P}$ and $\mathbb{C}$.

## Labor market power extension (JMP appendix `a:muestlmp`)

| Symbol | Meaning |
|---|---|
| $\Upsilon^l(\cdot)$, $\varphi^l(\cdot)$, $\zeta^l(\cdot)$ | Labor-supply analogues of $\Upsilon$, $\varphi$, $\zeta$ |
| $\mathbb{D}^l_c$, $\mathbb{W}_c$ | Wage competition index; ideal wage index |
| $\varrho_{jc}$ | Markdown (MRPL over wage) |
| $s^l_{jc}$ | Establishment wage-bill share in market $c$ |

## Open notation issues

- `\varsigma` is used both for the sieve coefficients (Section `s:myproc`) and for Lagrange multipliers in the JMP planner problem (Appendix `a:spprob`). This paper only needs the sieve meaning, but be careful when porting planner results.
- The JMP's Appendix `a:muestderiv` writes $s_{jc}$ without the superscript $y$ in one line. This is a typo for $s^y_{jc}$.
