# Issue

**Title:** primitives_normalized false qp_import_trexio.py

## Description

If primitives_normalized is True the export under trexio format followed by the import under trexio format leads to the wrong energy. Here is small script to test that:

echo "2" > h2.xyz
echo "" >> h2.xyz
echo "H 0.0 0.0 0.0" >> h2.xyz
echo "H 0.0 0.0 0.8" >> h2.xyz

rm -rf h2.ezfio
qp create_ezfio h2.xyz -b sto-3g
qp set_file ./h2.ezfio
qp run scf
E=$(qp run print_energy | grep "E(HF)" | awk '{printf $3}')

qp run export_trexio
qp_import_trexio.py ./h2.ezfio/work/h2.ezfio.h5

qp set_file ./h2.ezfio/work/h2.ezfio.h5.ezfio
E2=$(qp run print_energy | grep "E(HF)" | awk '{printf $3}')
echo "F" > h2.ezfio/work/h2.ezfio.h5.ezfio/ao_basis/primitives_normalized
E3=$(qp run print_energy | grep "E(HF)" | awk '{printf $3}')

# Check
echo "E before trexio : $E "
echo "E from trexio  ao_basis/primitives_normalized True   : $E2"
echo "E from trexio ao_basis/primitives_normalized False   : $E3"

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e95a05366bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.