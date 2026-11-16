# Issue

**Title:** Enable xtb as hcode with Gaussian

## Description

The purpose of the suggested changes is to allow calculations with xtb as the high level code using G16 and the `External` keyword together with the [xtb-gaussian](https://github.com/aspuru-guzik-group/xtb-gaussian) script. It fixes the following problems:

- Energy was not parsed correctly
- Update of recommended keywords in the documentation
- Inability to run opt + freq calculation with External and atoms not present in the default STO-3G basis set

The final point requires some background. The current behavior of Gaussian is to require a basis set for atoms even if the `External` keyword is used. The default basis set is STO-3G, which causes the program when calculating atoms not available in this basis set (for example I, Au, Pd). Gaussian allows the use of a dummy basis set that is defined for all atoms using the keyword `IOp(3/5=30)`. However, currently this setting does not completely carry over to the freq part of a opt+freq job, leading again to crashes. 

The strategy here is to split the opt + freq part into two parts. First the optimization is carried out as normal with the `opt_ts` keywords. The user should make sure that the `Freq` keyword is not included in those keywords. Then there is a check if the hessian has been calculated.

```python
            try:
                self.hessian = optts_calc.get_hessian()
```

If not, a freq calculation is run

```python
            except CouldNotGetProperty:
                self.atoms = optts_calc.get_final_atoms()
                optts_calc = Calculation(name=f'{self.name}_{name_ext}_extra_hess',
                                          molecule=self,
                                          method=method,
                                          n_cores=Config.n_cores,
                                          keywords=method.keywords.hess,
                                          bond_ids_to_add=bond_ids,
                                          other_input_block=method.keywords.optts_block)
                optts_calc.run()
```

This check should be compatible with the methods that do run opt+freq in the same job. I must credit Fernando R. Clemente from Gaussian Inc. for coming up with this strategy. If it looks good generally, we could proceed with some test etc. It would be great to be able to turn off the lcode in the case of using xtb as the hcode to save some time.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6505d5bbbd19`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.