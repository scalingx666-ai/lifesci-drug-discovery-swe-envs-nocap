# Issue

**Title:** Improved metal sandwich compound rendering

## Description

This PR fixes somethings and adds much better layout / rendering of sandwich compounds.

# Main Change 1: Fixing counter ion re-bonding 

We rebond some counter ions +ve/-ve when laying out molecules. This was conflicting with the correct SMILES for sandwich compounds where the ring is charged:

<img width="256" alt="Screenshot 2026-08-17 at 13 46 14" src="https://github.com/user-attachments/assets/9c100494-2ebb-4cb1-8732-4c698126781f" />

The ionic bond rebonding was tweaked to first neutralize such rings - the effective charge.

<img width="128" alt="Screenshot 2026-08-17 at 13 49 11" src="https://github.com/user-attachments/assets/3092f8d2-540f-4f19-8bea-bfbcf1f8e78c" />

# Main Change 2: 

8 member rings are the first ring size where we may have a double bond stereochemistry. As such they were NEVER laid out as a regular polygon, this is not nice when you have sandwich compounds.

<img width="128" alt="Screenshot 2026-08-17 at 13 50 00" src="https://github.com/user-attachments/assets/7acfd811-9713-4989-84d4-bea3289df128" />

We now check if there is a cis/trans bond and if there is we switch to the macrocycle layout.

<img width="256" alt="Screenshot 2026-08-17 at 13 52 02" src="https://github.com/user-attachments/assets/b9ece97c-0ae8-4f79-ae16-3f99c91f0fbe" />

I realised a possible better fix for this later in that we just reorder the templates: 

# Main Change 3 - orient the sandwich compounds 

<img width="128" alt="Screenshot 2026-08-17 at 13 56 00" src="https://github.com/user-attachments/assets/e7f7447f-9d2c-4576-a2a0-9232b228ffff" />

This includes provisions to try not to move non-simple rings and handling of triple deck er sandwich's.

<img width="200" alt="Screenshot 2026-08-17 at 13 56 07" src="https://github.com/user-attachments/assets/7f8d5667-fe52-4f9a-ae5a-785d3411cddf" />

<img width="128"  alt="Screenshot 2026-08-17 at 13 56 03" src="https://github.com/user-attachments/assets/fa0dcdc6-414b-403a-bb24-175fdeecfa34" />

It also now correctly display piano stools.

<img width="256" alt="Screenshot 2026-08-17 at 14 05 16" src="https://github.com/user-attachments/assets/c51e553d-8670-4667-ba86-f91de4827d2e" />


<img width="256" alt="Screenshot 2026-08-17 at 14 04 07" src="https://github.com/user-attachments/assets/04b1289b-de3b-4028-91f3-71568ac34d47" />


# Main Change 4 - rendering improvements

Center atom labels when the bonds are co-linear. I now allowed 8m rings to have "donut" rings and these donut rings can be cut out / and do cutting out of other bonds. The bond cuts are now also more correct - you want the metal bond behind the top ring but in front of the bottom ring.

<img width="512" alt="Screenshot 2026-08-17 at 14 01 15" src="https://github.com/user-attachments/assets/cc9bd3f2-295d-47e1-beda-cae143bc05a3" />

There is more than could be done for example tilting rings and adding bold bonds. For now though this is already much better.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1510b1679e72`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.