# The one-dimensional Ising model

An interactive, single-file web demo of the one-dimensional Ising model, solved exactly with the transfer matrix. It is based on lecture notes by Sang Hoon Lee for Chapter 2, which follow K. Christensen and N. R. Moloney, *Complexity and Criticality* (2005). It is a companion to the Ising introduction and the percolation demos.

Everything runs in the browser. There is no build step, no server and no dependencies beyond an optional web font. Units are k<sub>B</sub> = 1, and J = 1 unless stated.

## Running it

Open `index.html` in any modern browser (Chrome, Edge, Firefox or Safari).

To publish it with GitHub Pages, push this repository, then go to **Settings → Pages**, choose **Deploy from a branch**, and select the branch and the root folder. The page will be served at `https://<user>.github.io/<repository>/`.

## What the page contains

**Live chain.** A periodic chain of 100 to 1 000 spins under Metropolis updates, shown as the current state and a space-time history in which domains appear as stripes.

- Controls: temperature (with presets), field H, chain length and speed.
- Readouts: the time-averaged m and ε against the exact values, the number of domain walls, the mean domain length against 2/(1 − tanh βJ), and the correlation length.
- Charts: the measured correlation function against the exact sin²2φ (λ<sub>−</sub>/λ<sub>+</sub>)<sup>r</sup>, the domain-length distribution against its exact geometric form, and m over time.

**The transfer matrix.**

- the matrix T<sub>ss′</sub> = exp[βJss′ + (βH/2)(s + s′)] and its eigenvalues λ<sub>±</sub>, live for chosen T, H and J
- Z = Tr T<sup>N</sup> = λ<sub>+</sub><sup>N</sup> + λ<sub>−</sub><sup>N</sup>, checked against a brute-force sum over every microstate for N up to 16
- the free energy of a finite ring converging to −T ln λ<sub>+</sub>
- the special cases J = 0 (non-interacting spins) and H = 0

**Free energy, magnetization and response.**

- f(T, H) against H, with its cusp at the critical point (0, 0)
- m(T, H), which is a jump only at T = 0
- χ(T, H), and χ(T, 0) = βe<sup>2βJ</sup>, which diverges exponentially
- ε and c at H = 0, where c stays bounded
- the fluctuation–dissipation comparison with non-interacting spins

**Correlation function and the sum rule.** g(r) = tanh<sup>r</sup> βJ = e<sup>−r/ξ</sup>, ξ = −1/ln tanh βJ with its ½e<sup>2βJ</sup> limit, and a table checking Σ g = e<sup>2βJ</sup> = k<sub>B</sub>Tχ(T, 0).

**The critical point and percolation.** (T<sub>c</sub>, H<sub>c</sub>) = (0, 0), reachable from one side only, and the exact correspondence p ↔ tanh βJ with one-dimensional percolation.

**Why domain walls win.** The free-energy comparison of one domain and a droplet with two domain walls, F<sub>2-dom</sub> − F<sub>1-dom</sub> ≈ 4J − 2k<sub>B</sub>T ln N, plotted against N. The largest stable domain N* = e<sup>2J/k<sub>B</sub>T</sup> is compared with ξ.

## Methods

| Topic | Approach |
| --- | --- |
| Exact results | Closed forms from the eigenvalues λ<sub>±</sub>; ε by differentiating ln λ<sub>+</sub> numerically |
| Brute-force check | Direct sum over all 2<sup>N</sup> states of a ring for N ≤ 16 |
| Live chain | Random-sequential Metropolis updates on a ring; time averages reset whenever T or H changes |
| Correlations with a field | g(r) = sin²2φ (λ<sub>−</sub>/λ<sub>+</sub>)<sup>r</sup> with cos 2φ = m, which reduces to tanh<sup>r</sup> βJ at H = 0 |

## Files

```
index.html   the complete demo (HTML, CSS and JavaScript in one file)
README.md    this file
```

## References

**Key reference.** K. Christensen and N. R. Moloney, *Complexity and Criticality*, Imperial College Press, London (2005), Chapter 2.

1. E. Ising, "Beitrag zur Theorie des Ferromagnetismus," *Z. Phys.* **31**, 253 (1925).
2. H. A. Kramers and G. H. Wannier, "Statistics of the two-dimensional ferromagnet. Part I," *Phys. Rev.* **60**, 252 (1941).
3. S. G. Brush, "History of the Lenz–Ising model," *Rev. Mod. Phys.* **39**, 883 (1967).
4. N. Goldenfeld, *Lectures on Phase Transitions and the Renormalization Group*, Addison-Wesley (1992).

## Credits

Lecture notes: Sang Hoon Lee.

Created by Claude Opus 5.5.
