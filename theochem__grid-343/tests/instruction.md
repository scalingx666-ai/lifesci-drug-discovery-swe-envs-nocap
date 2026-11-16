# Issue

**Title:** fix: correct analytical Coulomb potential for p-type Gaussians

## Description

## Description

.

This PR corrects a fundamental mathematical flaw in `grid.coulomb.coulomb_gaussian_p` where the analytical electrostatic potential returned for $p$-type radial Gaussian charge densities violated Poisson's equation $\nabla^2 V(\mathbf{r}) = -4\pi \rho(\mathbf{r})$.

---

### Root Cause & Mathematical Correction

For a normalized $p$-type radial Gaussian charge density:

$$\rho(r) = \frac{2}{3} \frac{\alpha^{5/2}}{\pi^{3/2}} r^2 e^{-\alpha r^2}$$

The exact solution to Poisson's equation with $V(\infty) = 0$ is obtained by radial integration of Gauss's law:

$$V(r) = \frac{4\pi}{r} \int_0^r \rho(r') r'^2 dr' + 4\pi \int_r^\infty \rho(r') r' dr'$$

Evaluating the integrals:
1. **Interior charge:**
   $$\frac{4\pi}{r} \int_0^r \rho(r') r'^2 dr' = \frac{\mathrm{erf}(\sqrt{\alpha} r)}{r} - \frac{4\alpha^{3/2}}{3\sqrt{\pi}} r^2 e^{-\alpha r^2} - 2 \sqrt{\frac{\alpha}{\pi}} e^{-\alpha r^2}$$
2. **Exterior shell:**
   $$4\pi \int_r^\infty \rho(r') r' dr' = \frac{4\alpha^{3/2}}{3\sqrt{\pi}} r^2 e^{-\alpha r^2} + \frac{4}{3} \sqrt{\frac{\alpha}{\pi}} e^{-\alpha r^2}$$

Summing both integrals cancels the $r^2 e^{-\alpha r^2}$ terms identically and leaves:

$$V_{\text{exact}}(r) = \frac{\mathrm{erf}(\sqrt{\alpha} r)}{r} - \frac{2}{3} \sqrt{\frac{\alpha}{\pi}} e^{-\alpha r^2}$$

The previous implementation in `coulomb_gaussian_p` had omitted the $-2\sqrt{\alpha/\pi} e^{-\alpha r^2}$ term from the interior integral, leaving an erroneous $+ \frac{4}{3} \sqrt{\frac{\alpha}{\pi}} e^{-\alpha r^2}$. This caused:
- Wrong sign and magnitude for the Gaussian tail term.
- A **+150% error at the nucleus ($r \to 0$)**: $\frac{10}{3}\sqrt{\alpha/\pi}$ instead of the physical limit $\frac{4}{3}\sqrt{\alpha/\pi}$.
- Unnormalized limit was erroneously $5\pi/\alpha^2$ instead of $2\pi/\alpha^2$.

---

### Graphical Proof & Poisson Equation Verification

![Poisson Equation Verification and Potential Comparison](https://raw.githubusercontent.com/alok-108/assets/main/grid_coulomb_p_gaussian_bug.png)

---

### Commit Structure (5 Atomic Commits)

This PR is organized into 5 logical commits:

1. **`fix(coulomb): correct p-type Gaussian potential formula and nuclear limit`**
   - Corrected `term2` sign and magnitude to $-(2/3) \sqrt{\alpha/\pi} e^{-\alpha r^2}$.
   - Updated $r \to 0$ threshold limit to $(4/3) \sqrt{\alpha/\pi}$.
2. **`docs(coulomb): update p-type Gaussian Coulomb potential docstrings`**
   - Updated Sphinx docstrings with the exact analytical formulas and physical limits.
3. **`test(coulomb): update unit tests for corrected p-type Gaussian potential`**
   - Updated existing `test_coulomb_gaussian_p()` test expectations for both normalized and unnormalized cases.
4. **`test(coulomb): add Poisson equation numerical validation for p-type Gaussians`**
   - Added `test_coulomb_gaussian_p_poisson_equation()` testing $\nabla^2 V(r) = -4\pi \rho(r)$ via numerical spherical Laplacian differentiation across diverse $\alpha$ values.
5. **`test(coulomb): add multi-center p-type Gaussian tests in coulomb_potential`**
   - Added `test_coulomb_potential_with_p_gaussians()` testing combined multi-center $s$-type and $p$-type Gaussian superposition at nuclear and off-nuclear points.

---

### Verification

All 11 tests in `tests/test_coulomb.py` and the complete test suite pass. Ruff formatting and linting pass without errors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad304ca1dda8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.