# Issue

**Title:** Fix reduced mass calculation

## Description

- fix the calculation of the reduced mass to consistent with reference calculations in other implementations as well as DFT reference data (see issue #367)
- more consistent variable names to avoid exploiting variables for different purposes (`isqm` serves also as scratch variable in a later part of the code)
- 
- took Psi4 implementation https://github.com/psi4/psi4/blob/0df59280773a86f7ae1f6cc577731074a0fbaad9/psi4/driver/qcdb/vib.py#L582 as reference and documentation from: https://gaussian.com/vib/

**Normalization** is a relatively straightforward process. Before it is printed out, each of the `3N` elements of `l_{\text{CART},k,i}` is scaled by the normalization factor `N_i` for that particular vibrational mode. The normalization is defined by:

$$
N_i = \sqrt{ \left( \sum_k \left[ l_{\text{CART},k,i} \right]^2 \right)^{-1} }, \quad k = 1 \dots 3N \quad \text{(Eq. 12)}
$$

**Reduced mass** $\mu_i$ for the vibrational mode is calculated similarly ($k = 1 \dots 3N$):

$$
\mu_i = \left( \sum_k \left[ l_{\text{CART},k,i} \right]^2 \right)^{-1}
= \left( \sum_k \left( \frac{l_{\text{MWC},k,i}}{\sqrt{m_k}} \right)^2 \right)^{-1}
= N_i^2 \quad \text{(Eq. 13)}
$$

Note that since $D$ is orthonormal, and we can (and do) choose $L$ to be orthonormal, then $l$ is orthonormal as well.

Since $$D^\top D = I$$ and $$L^\top L = I$$, it follows that $$I = (DL)^\top (DL) = L^\top D^\top D L = L^\top L = I $$

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f9ec00a196dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.