# Notation

This paper's notation follows the JMP (`literature/OMPSM_Franco.tex`), with one deliberate departure in the indices (see below).
Blackboard bold is reserved for indices.
Add new symbols here when they are first introduced, with the section where they appear.
Symbols first defined in `paper/Scratch.tex` are marked with the section label.

## Indices

| Symbol | Meaning | JMP equivalent |
|---|---|---|
| $j$ | Establishment | $j$ |
| $i \in \{1,\dots,I\}$ | Industry | $n$ (sector) |
| $n \in \{1,\dots,N\}$ | Region (market): county or commuting zone | $a$ (model), $c$ (empirics) |
| $t$ | Period (year) | not used |
| $k$ | Polynomial order in the sieve, $k = 1,2,3$ | $k$ |

When porting JMP material, relabel sector $n \to i$ and city $c$ (or $a$) $\to n$.

## Set up and preferences (`sec:setup`, `sec:preferences`, with `sec:hdia`, `sec:hsa`, `sec:hiia`, `sec:common`)

| Symbol | Meaning |
|---|---|
| $N$, $I$ | Number of regions; number of industries |
| $L_{nt}$ | Population of region $n$ |
| $\mathcal{J}_{int}$ | Finite set of establishments in industry $i$, region $n$, period $t$ (taken as given) |
| $U_{nt}$ | Household utility |
| $U(Y_{1nt},\dots,Y_{Int},Y^T_{nt})$ | Upper-tier utility: weakly separable across industries, strictly increasing in each argument; otherwise unrestricted |
| $Y^T_{nt}$ | Bundle of traded goods (not modeled) |
| $\Upsilon_{in}(\cdot)$ | HDIA (Kimball) aggregator of industry $i$ in region $n$, constant over time: continuous on $[0,\infty)$, $C^2$ on $(0,\infty)$, strictly increasing, strictly concave, $\Upsilon_{in}(0)=0$ |
| $y_{jint}$, $Y_{int}$ | Per-capita consumption of variety $j$; per-capita industry-$i$ bundle |
| $\xi_{jint}$ | Quality (taste shifter) of variety $j$; utility depends on $e^{\xi_{jint}} y_{jint}$; costless, not in the production function |
| $p_{jint}$ | Price of establishment $j$ |
| $\vartheta_{int}$ | Multiplier in the household's lower-tier problem ($\lambda^W$ in the JMP; $\lambda$ is reserved here for marginal cost) |
| $\mathbb{D}_{int}$ | Competition price index, the index establishments compete against. HDIA: $\vartheta_{int}/Y_{int}$, defined by `eq:Dindex`. HSA: the single aggregator, defined by `eq:hsaD` ($A(\mathbf{p})$ in Matsuyama and Ushchev). HIIA: the ideal price index itself, $\mathbb{D}_{int} = \mathbb{P}_{int}$ |
| $\mathbb{P}_{int}$ | Ideal price index of the industry-$i$ bundle |
| $\varphi_{in}(\cdot) \equiv (\Upsilon_{in}')^{-1}(\cdot)$ | Demand function: $e^{\xi_{jint}} y_{jint}/Y_{int} = \varphi_{in}(\check{p}_{jint})$ |
| $\check{p}_{jint} \equiv p_{jint} e^{-\xi_{jint}}/\mathbb{D}_{int}$ | Quality-adjusted relative price (`eq:relprice`). Check notation as in Errico and Lashkari; tildes are reserved for variables observed with error |
| $h_{in}(\cdot)$ | Share function, used for both families. HSA: the budget-share function ($s(\cdot)$ in Matsuyama and Ushchev; renamed to avoid a clash with sales shares). HDIA: $h_{in}(\check{p}) \equiv \check{p}\,\varphi_{in}(\check{p})$. HIIA: $h_{in}(\check{p}) \equiv -\check{p}\,\theta_{in}'(\check{p})$ |
| $H_{int} \equiv \sum_j h_{in}(\check{p}_{jint})$ | Market-level term in the budget share $h_{in}(\check{p}_{jint})/H_{int}$. HDIA: $\mathbb{P}_{int}/\mathbb{D}_{int}$. HSA: 1. HIIA: no simpler form ($-C/P$ in Matsuyama and Ushchev's notation) |
| $\theta_{in}(\cdot)$ | HIIA function defining the ideal price index, $\sum_j \theta_{in}(p_{jint}e^{-\xi_{jint}}/\mathbb{P}_{int}) = 1$ (`eq:hiia`): continuously differentiable, and decreasing and convex where positive |
| $\gamma_{in}$ | Scale of the CES case under HSA, $h_{in}(\check{p}) = \gamma_{in}\check{p}^{1-\sigma_{in}}$, and under HIIA, $\theta_{in}(\check{p}) = \gamma_{in}\check{p}^{1-\sigma_{in}}$ (not to be confused with returns to scale $\gamma_i$) |
| $q_{jint} = L_{nt} y_{jint}$ | Total output (quantity sold) of establishment $j$ |
| $\sigma_{in}(\cdot)$ | Price elasticity of demand as a function of the quality-adjusted relative price $\check{p}$ |

## Production and markups (`sec:production`)

| Symbol | Meaning |
|---|---|
| $\omega_{jint}$ | Hicks-neutral productivity |
| $\mathcal{X}$ | Set of inputs |
| $\mathcal{X}^f \subseteq \mathcal{X}$ | Flexible inputs, chosen in $t$ after $\omega_{jint}$ is known (labor $l \in \mathcal{X}^f$); the rest are fixed (chosen before $t$) |
| $v^x_{jint}$ | Quantity of input $x$ ($v^l_{jint} = l_{jint}$) |
| $W^x_{int}$ | Price of input $x$, specific to industry, region and period ($W^l_{int} = W_{int}$) |
| $\beta^x_i$ | Output elasticity of input $x$ in industry $i$, constant over time |
| $\gamma_i \equiv \sum_{x \in \mathcal{X}} \beta^x_i$ | Returns to scale (unrestricted) |
| $\gamma^f_i \equiv \sum_{x \in \mathcal{X}^f} \beta^x_i$ | Short-run returns to scale (flexible inputs only) |
| $\lambda_{jint}$ | Short-run marginal cost (multiplier in the cost-minimization problem) |
| $\mu_{jint} \equiv p_{jint}/\lambda_{jint}$ | Markup |
| $\mu_{in}(\cdot)$ | Markup as a function of the quality-adjusted relative price, $\sigma_{in}/(\sigma_{in} - 1)$ |
| $\alpha^x_{jint} \equiv W^x_{int} v^x_{jint}/(p_{jint} q_{jint})$ | Expenditure share of input $x$ in true sales |
| $\nu_{jint}$ | Measurement error in observed sales |
| $\tilde{R}_{jint} = p_{jint} q_{jint} e^{\nu_{jint}}$ | Observed sales |
| $\tilde{\alpha}^x_{jint} = \alpha^x_{jint} e^{-\nu_{jint}}$ | Observed expenditure share of input $x$ |

## Estimating equation (`sec:estequ`)

| Symbol | Meaning |
|---|---|
| $R_{jint} \equiv p_{jint} q_{jint}$ | True sales |
| $s^y_{jint}$ | True sales share in its region-industry-period |
| $\tilde{s}^y_{jint}$ | Observed sales share (built from $\tilde{R}$) |
| $\zeta_{in}(\cdot)$ | Inverse of $h_{in}$; maps $s^y_{jint} H_{int}$ to $\check{p}_{jint}$ |
| $\overline{p}_{in}$ | Choke price: $h_{in}(\check{p}) = 0$ for $\check{p} \geq \overline{p}_{in}$. Under HDIA, $\overline{p}_{in} = \Upsilon_{in}'(0)$ |
| $\underline{p}_{in}$ | Lower end of the elastic interval $(\underline{p}_{in}, \overline{p}_{in})$ where $\sigma_{in} > 1$ |
| $m_{in}(a) \equiv \log\mu_{in}(\zeta_{in}(a))$ | Log markup as a function of $a = s^y H$; $m_{in}(0) = 0$ |
| $a_{jint} \equiv s^y_{jint} H_{int}$ | Argument of $m_{in}$ |
| $\bar{e}_{int} \equiv \sum_j s^y_{jint} e^{\nu_{jint}}$ | Sales-weighted mean of $e^{\nu}$ in the market |
| $\kappa_k \equiv \mathbb{E}[e^{k\nu}]$ | Moments of the measurement error |
| $K$ | Sieve order (baseline $K=3$) |
| $\varsigma_{k,in}$ | Region-industry sieve coefficients of $m_{in}$ |
| $r_{in}(a)$ | Sieve approximation error |
| $\rho_k$ | Possibly fractional sieve exponents, $\rho_k > 0$ (open idea; the baseline uses $\rho_k = k$) |
| $\varsigma_{k,int} \equiv -(\varsigma_{k,in}/\kappa_k)(\bar{e}_{int} H_{int})^k$ | Market-specific coefficients in the estimating equation |
| $\Phi_{int} \equiv \bar{e}_{int} H_{int}$ | The single market-level shifter behind all $\varsigma_{k,int}$ |
| $\upsilon_{jint}$ | Composite error: measurement error in shares and sales, plus sieve error |
| $\mathbf{z}_{jint}$ | Instruments (baseline: lagged observed shares and powers) |
| $\mathcal{M}_{int}$ | Aggregate markup: sales-weighted harmonic mean of $\mu_{jint}$ (JMP; not yet used here) |

## JMP-only objects (not yet used here)

| Symbol | Meaning |
|---|---|
| $\mathbb{C} \equiv W/\mathbb{D}$ | Competition index |
| $\psi(\cdot)$ | Optimal relative price, $p/\mathbb{D} = \psi(\mathbb{C}/z)$ |
| $\delta(\cdot)$ | Consumer-surplus ratio (area under demand over sales) |
| $\Upsilon^l$, $\varphi^l$, $\zeta^l$, $\mathbb{D}^l$, $\mathbb{W}$, $\varrho$, $s^l$ | Labor market power extension (`a:muestlmp`): labor-supply aggregator and its inverse, wage indices, markdown, wage-bill share |

## Departures from the JMP

- Three families of preferences, HDIA, HSA and HIIA, written with a common share function $h_{in}$ and market term $H_{int}$. The JMP has HDIA (Kimball) only. Assumption 1 is the HDIA regularity condition, Assumption 1$'$ its HSA counterpart, and Assumption 1$''$ its HIIA counterpart.

- Indices: regions $n$ and industries $i$ (see above).
- $\alpha^x$ uses total sales $pq$ in the denominator, where the JMP writes $py$. They are the same object, because the JMP's production function is in total quantities.
- $\nu$ is measurement error in observed sales only, and input expenditures are measured without error. The JMP treats it as either an ex-post production shock or measurement error.
- The upper tier is a general weakly separable $U$ with a traded bundle, where the JMP uses Cobb-Douglas over local goods, housing and a traded good.

## Macro warnings and open notation issues

- In `preamble.tex`, `\D` is $\Delta$, not $\mathbb{D}$. Write `\mathbb{D}` in full. `\P` and `\C` are $\mathbb{P}$ and $\mathbb{C}$.
- `\varsigma` is used both for the sieve coefficients (JMP `s:myproc`) and for Lagrange multipliers in the JMP planner problem (`a:spprob`). This paper only needs the sieve meaning, but be careful when porting planner results.
- The JMP's Appendix `a:muestderiv` writes $s_{jc}$ without the superscript $y$ in one line. This is a typo for $s^y_{jc}$.
