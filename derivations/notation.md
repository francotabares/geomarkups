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
