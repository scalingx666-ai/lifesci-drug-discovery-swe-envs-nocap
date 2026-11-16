# Issue

**Title:** fix v1.10 convergence bug

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] SCF convergence regression introduced in v1.10, esp. for SAD guess (default), has been addressed

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] So #3138 added a `sqrt` to the occupations, which everyone agreed was theoretically sound. But though all the SCFs in the test suite converged, there were reports of serious convergence regression in real-world cases once it was available in v1.10 .
- Characteristics: very different SAD energy, jumps in SCF energies, more iterations to converge or fails to converge, sometimes positive SCF energies. SAD is affected, SADNO is ok. worse with larger basis sets
- Solution: Lines 462-463 were already sqrt-ing the occupations anticipating no sqrt in the density formulation. Then 3138 fixed the nominal density formulation, and the net result was bad `D  = C * √n * Cᵀ` for the SAD energy. SADNO was recomputing, so not affected. With this PR, we're now storing the actual occupation `n` in `occ` vector, rather than the unexpected `sqrt(n)` _and_ not net 4th-routing, so should be both correct and using expected definitions. Both solutions (pre-3183 and post-this-PR) are sqrt floats into a vector, so I don't think it should be a numerical or performance hit.
- [x] added a test for the hydrogen atom
- [x] see the Performance table at #3392 to show 2k improvement in SCF iteration count across cmake suite with this change.
- [x] TODO run full test suite and probably reset reference guess energies
- [x] I turned off SPHINXMAN_STRICT to probably heal the docs until py314 PR. I added a TODO at the py314 PR to remember to turn it back on

#### Case A

input
```
import psi4

atin = {'driver': 'energy',
 'extras': {},
 'id': '1098604',
 'keywords': {'dft_radial_points': 99,
              'dft_spherical_points': 590,
              'freeze_core': 'true',
              'guess': 'sad',
              'scf_type': 'df'},
 'model': {'basis': 'aug-cc-pvtz', 'method': 'b3lyp'},
 'molecule': {'extras': {},
              'fix_com': True,
              'fix_orientation': True,
              'fragment_charges': [0.0, 0.0],
              'fragment_multiplicities': [1, 1],
              'fragments': [[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10], [11, 12, 13, 14, 15, 16]],
              'geometry': [2.61043402, -0.00044121, 0.24843046, 1.28378693, -2.15474029, 0.17400534, 2.37863532,
                           -3.88331582, 0.23788555, -1.34118081, -2.25465883, 0.01259364, -2.29429321, -4.06019305,
                           -0.04782615, -2.68646031, 0.00025214, -0.07713276, -4.72563084, 0.00048674, -0.2063009,
                           -1.34057398, 2.25477469, 0.01232476, -2.29320462, 4.06054493, -0.04824151, 1.28435551,
                           2.15420507, 0.17365266, 2.3796579, 3.88246292, 0.23716531, 0.06343214, 1.25951567, 9.5218084,
                           1.78397865, 2.31679045, 9.22112492, -1.65536353, 2.32230563, 9.81842076, 0.06406082,
                           -1.25889834, 9.52205829, 1.78510185, -2.31541111, 9.22157212, -1.65424464, -2.32248301,
                           9.81891377],
              'id': 392429,
              'identifiers': {'molecular_formula': 'C7H9N',
                              'molecule_hash': 'c59221b6926802a47537353b5568d595b5bc70a1'},
              'molecular_charge': 0.0,
              'molecular_multiplicity': 1,
              'name': 'C7H9N',
              'provenance': {'creator': 'QCElemental',
                             'routine': 'qcelemental.molparse.from_string',
                             'version': '0.30.1'},
              'schema_name': 'qcschema_molecule',
              'schema_version': 2,
              'symbols': ['N', 'C', 'H', 'C', 'H', 'C', 'H', 'C', 'H', 'C', 'H', 'C', 'H', 'H', 'C', 'H', 
'H'],
              'validated': True},
 'protocols': {},
 'provenance': {'creator': 'QCElemental', 'routine': 'qcelemental.models.results', 'version': '0.30.1'},
 'schema_name': 'qcschema_input',
 'schema_version': 1}

atres = psi4.schema_wrapper.run_qcschema(atin)

import pprint
pprint.pprint(atres.dict(), width=200)
```

pre-PR (after 3138)
```
           '                           Total Energy        Delta E     RMS |[F,P]|\n'
           '\n'
           '   @DF-RKS iter SAD:  -316.21992278452490   -3.16220e+02   0.00000e+00 \n'
           '   @DF-RKS iter   1:  -205.32913877701043    1.10891e+02   5.42322e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter   2:  -224.06952449095508   -1.87404e+01   1.89655e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter   3:  -249.71626804837922   -2.56467e+01   1.46675e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter   4:  -248.93677917763452    7.79489e-01   1.49680e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter   5:  -249.16709307201521   -2.30314e-01   1.49107e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter   6:  -249.21682688224649   -4.97338e-02   1.48963e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter   7:  -249.28885403246261   -7.20272e-02   1.48836e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter   8:  -250.00805758055347   -7.19204e-01   1.47470e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter   9:  -250.80842641078536   -8.00369e-01   1.45541e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  10:  -250.84764512040914   -3.92187e-02   1.45463e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  11:  -250.84713032557238    5.14795e-04   1.45450e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  12:   -33.64641476808652    2.17201e+02   3.00618e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  13:  -151.60434597363016   -1.17958e+02   1.51821e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  14:  -288.66595321060510   -1.37062e+02   5.13194e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter  15:   -59.53389989856954    2.29132e+02   2.72529e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  16:   -73.40981523089800   -1.38759e+01   2.57745e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  17:   -72.56067150318013    8.49144e-01   2.58702e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  18:   -73.11367286027092   -5.53001e-01   2.57986e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  19:   -73.23326235796704   -1.19589e-01   2.57898e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  20:   -73.97412379492712   -7.40861e-01   2.57205e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  21:   -73.96806880444144    6.05499e-03   2.57167e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  22:  -131.31290332913841   -5.73448e+01   2.27466e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  23:  -111.75337694828593    1.95595e+01   2.31469e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  24:   -73.72184927054090    3.80315e+01   2.54436e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  25:  -138.39489760006825   -6.46730e+01   1.95629e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  26:  -280.48387004114795   -1.42089e+02   8.67408e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter  27:   -56.44328663699048    2.24041e+02   2.78565e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  28:  -126.37076683459448   -6.99275e+01   2.32620e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  29:   -96.82723268959373    2.95435e+01   2.50890e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  30:   -98.76724569068173   -1.94001e+00   2.48317e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  31:   -99.32659965921866   -5.59354e-01   2.47680e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  32:   -98.97535690354279    3.51243e-01   2.48023e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  33:   -98.22876057565459    7.46596e-01   2.49101e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  34:   -97.60923064397460    6.19530e-01   2.49766e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  35:   -97.13963460392267    4.69596e-01   2.49711e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  36:  -278.81940499647163   -1.81680e+02   1.55059e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  37:  -158.70027731640232    1.20119e+02   2.64786e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  38:  -287.04643050811126   -1.28346e+02   6.35662e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter  39:   -92.68909678066260    1.94357e+02   2.26094e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  40:  -103.41026119644972   -1.07212e+01   2.13116e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  41:  -103.16650171453890    2.43759e-01   2.13833e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  42:  -104.05929997025902   -8.92798e-01   2.13265e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  43:  -106.08201886152341   -2.02272e+00   2.11001e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  44:  -105.94331085529834    1.38708e-01   2.11251e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  45:  -106.20487040281679   -2.61560e-01   2.10975e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  46:  -132.20434756291928   -2.59995e+01   2.00243e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  47:  -155.76620610498713   -2.35619e+01   2.07900e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  48:  -141.60167870636070    1.41645e+01   2.09304e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  49:  -124.90366956004247    1.66980e+01   2.18431e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  50:  -281.44142743968581   -1.56538e+02   7.17661e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter  51:   -70.95661438878294    2.10485e+02   2.59792e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  52:   -86.17313088219395   -1.52165e+01   2.42485e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  53:   -90.52103693285423   -4.34791e+00   2.38897e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  54:   -92.38632707528332   -1.86529e+00   2.36480e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  55:   -94.06613618527636   -1.67981e+00   2.34954e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  56:   -83.57586190813959    1.04903e+01   2.45173e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  57:   -83.48123561101325    9.46263e-02   2.43967e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  58:   -85.85989270687787   -2.37866e+00   2.41667e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  59:   -84.08021041497102    1.77968e+00   2.44182e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  60:  -121.15861610293233   -3.70784e+01   2.20518e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  61:  -140.40441505364097   -1.92458e+01   1.93889e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  62:  -288.74439449555115   -1.48340e+02   6.33314e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter  63:   -44.14950389564867    2.44595e+02   2.90593e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  64:   -65.81630579530636   -2.16668e+01   2.66101e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  65:   -63.68402418583648    2.13228e+00   2.68758e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  66:   -60.65319993533722    3.03082e+00   2.71810e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  67:   -61.24709757919583   -5.93898e-01   2.70951e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  68:   -61.10072470311852    1.46373e-01   2.71195e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  69:   -60.81733643589248    2.83388e-01   2.71521e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  70:   -60.78175637697291    3.55801e-02   2.71557e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  71:   -59.16605015160617    1.61571e+00   2.72936e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  72:  -134.03686703418248   -7.48708e+01   2.22651e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  73:  -148.16702761536692   -1.41302e+01   1.81316e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  74:  -277.91113949274347   -1.29744e+02   1.09868e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  75:  -262.38213176719341    1.55290e+01   1.36592e-02 DIIS/ADIIS\n'
           '   @DF-RKS iter  76:  -320.63945351724550   -5.82573e+01   5.30663e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter  77:  -318.02996413171275    2.60949e+00   4.87838e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter  78:  -324.82038694972817   -6.79042e+00   2.28263e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter  79:  -326.45235167089930   -1.63196e+00   1.88107e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter  80:  -326.93975704358490   -4.87405e-01   5.38044e-04 DIIS/ADIIS\n'
           '   @DF-RKS iter  81:  -326.97676531196095   -3.70083e-02   3.59017e-04 DIIS/ADIIS\n'
           '   @DF-RKS iter  82:  -326.98738779714006   -1.06225e-02   2.51252e-04 DIIS/ADIIS\n'
           '   @DF-RKS iter  83:  -326.99770140536339   -1.03136e-02   1.02762e-04 DIIS/ADIIS\n'
           '   @DF-RKS iter  84:  -326.99947668228072   -1.77528e-03   4.28412e-05 DIIS\n'
           '   @DF-RKS iter  85:  -326.99978861362740   -3.11931e-04   8.54168e-06 DIIS\n'
           '   @DF-RKS iter  86:  -326.99979757982169   -8.96619e-06   3.96711e-06 DIIS\n'
           '   @DF-RKS iter  87:  -326.99980003728439   -2.45746e-06   1.45831e-06 DIIS\n'
           '   @DF-RKS iter  88:  -326.99980037502849   -3.37744e-07   1.93683e-07 DIIS\n'
           '  Energy and wave function converged.\n'
```

with PR
```
          '                           Total Energy        Delta E     RMS |[F,P]|\n'
           '\n'
           '   @DF-RKS iter SAD:  -325.79440821095068   -3.25794e+02   0.00000e+00 \n'
           '   @DF-RKS iter   1:  -326.20312893365315   -4.08721e-01   2.15459e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter   2:  -325.63769104378059    5.65438e-01   2.73561e-03 DIIS/ADIIS\n'
           '   @DF-RKS iter   3:  -326.98835628709872   -1.35067e+00   2.73423e-04 DIIS/ADIIS\n'
           '   @DF-RKS iter   4:  -326.99241093749532   -4.05465e-03   2.23417e-04 DIIS/ADIIS\n'
           '   @DF-RKS iter   5:  -326.99905089738058   -6.63996e-03   6.91306e-05 DIIS\n'
           '   @DF-RKS iter   6:  -326.99973363574259   -6.82738e-04   1.92976e-05 DIIS\n'
           '   @DF-RKS iter   7:  -326.99979692134883   -6.32856e-05   4.50836e-06 DIIS\n'
           '   @DF-RKS iter   8:  -326.99979996861384   -3.04727e-06   1.55230e-06 DIIS\n'
           '   @DF-RKS iter   9:  -326.99980037942862   -4.10815e-07   1.44554e-07 DIIS\n'
           '  Energy and wave function converged.\n'
```

#### Case B

input too big to post, but it's a protein HF/6-31G*

pre-PR (after 3138) did not converge
```
                           Total Energy        Delta E     RMS |[F,P]|

   @DF-RHF iter SAD: -5268.15423368303436   -5.26815e+03   0.00000e+00 
   @DF-RHF iter   1: -2835.97921868223102    2.43218e+03   1.86473e-02 DIIS/ADIIS
   @DF-RHF iter   2: 12605.33631523363147    1.54413e+04   3.02647e-02 DIIS/ADIIS
   @DF-RHF iter   3: 10009.97697675413838   -2.59536e+03   3.13564e-02 DIIS/ADIIS
   @DF-RHF iter   4: 10600.07023041166030    5.90093e+02   3.45322e-02 DIIS/ADIIS
   @DF-RHF iter   5:  1174.39682100895698   -9.42567e+03   2.76258e-02 DIIS/ADIIS
```

with PR
```
                          Total Energy        Delta E     RMS |[F,P]|

   @DF-RHF iter SAD: -7194.43817026159377   -7.19444e+03   0.00000e+00 
   @DF-RHF iter   1: -7206.49632123941501   -1.20582e+01   1.16460e-03 DIIS/ADIIS
   @DF-RHF iter   2: -7209.31324930712344   -2.81693e+00   7.47464e-04 DIIS/ADIIS
   @DF-RHF iter   3: -7210.52994941593897   -1.21670e+00   1.26916e-04 DIIS/ADIIS
   @DF-RHF iter   4: -7210.59093633528209   -6.09869e-02   4.95355e-05 DIIS
   @DF-RHF iter   5: -7210.59947136105529   -8.53503e-03   1.06344e-05 DIIS
   @DF-RHF iter   6: -7210.60031247098959   -8.41110e-04   5.56251e-06 DIIS
   @DF-RHF iter   7: -7210.60050250298900   -1.90032e-04   2.13750e-06 DIIS
   @DF-RHF iter   8: -7210.60053809982855   -3.55968e-05   8.69078e-07 DIIS
   @DF-RHF iter   9: -7210.60054325297824   -5.15315e-06   3.06774e-07 DIIS
   @DF-RHF iter  10: -7210.60054386128195   -6.08304e-07   9.41156e-08 DIIS
   @DF-RHF iter  11: -7210.60054391422182   -5.29399e-08   3.69407e-08 DIIS
  Energy and wave function converged.
```

## Checklist
- [ ] Tests added for any new features
- [ ] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `144882d942e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.