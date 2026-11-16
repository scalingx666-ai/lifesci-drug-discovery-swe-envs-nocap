# Issue

**Title:** Sugar Detection Utility

## Description

This new functionality, the <i>SugarDetectionUtility</i>, can be used for algorithmically separating glycosides into their aglycone and sugar moieties. The main feature is the ability to create copies of both the aglycone and individual sugar fragments from a given molecule, with proper handling of attachment points and stereo chemistry, and some optional post-processing options. The new class extends the <i>SugarRemovalUtility</i> and uses the same algorithm (described [here](https://doi.org/10.1186/s13321-020-00467-y)) to generate the aglycone (with slight deviations, see below).

Background:
The <i>SugarRemovalUtility</i> is focused on generating a sensible aglycone and extracts the removed sugars only as Tetrahydrofuran/Tetrahydropyran (CNP IDs refer to compounds in the [COCONUT natural products database](https://coconut.naturalproducts.net/)):
<p></p>
<img width="3564" height="1417" alt="image" src="https://github.com/user-attachments/assets/7a023e78-320f-4a61-8f65-79262e92ab10" />
<p></p>
<p>This shortcoming is now resolved by the Sugar <i>Detection</i> Utility:</p>
<p></p>
<img width="3524" height="1457" alt="image" src="https://github.com/user-attachments/assets/2485932c-3bf0-4345-9498-b00c4ba9b383" />
<p></p>
<p>The Sugar <i>Detection</i> Utility supports:</p>
<ul>
  <li>Duplication of connecting hetero atoms in glycosidic bonds, to produce more sensible educts (see above)</li>
  <li>Preservation of stereo chemistry at connection points (see above)</li>
  <li>Detection and extraction of both circular and linear sugar moieties (see the Sugar Removal Utility documentation for more details on this)</li>
<p></p>
<img width="3626" height="1462" alt="image" src="https://github.com/user-attachments/assets/45b5f518-17ae-4fbb-9526-e163791e6413" />
<p></p>
  <li>Saturation of broken bonds with either implicit hydrogen atoms or pseudo ("R") atoms</li>
<p></p>
<img width="3576" height="1462" alt="image" src="https://github.com/user-attachments/assets/3161cec7-47db-431b-9011-f324d72b8490" />
<p></p>
  <li>Post-processing of sugar fragments including bond splitting (O-glycosidic, ether, ester, peroxide) to separate the individual sugars</li>
<p></p>
<img width="3418" height="1418" alt="image" src="https://github.com/user-attachments/assets/539a9511-7ef7-4d9f-aae1-e0eec60dd962" />
<p></p>
  <li>Limiting this post-processing by size, so that small modifications remain attached to the sugars</li>
<p></p>
<img width="3608" height="1457" alt="image" src="https://github.com/user-attachments/assets/e9661506-f7c2-4c99-8df0-31868aad6bfa" />
<p></p>
  <li>Optional mapping of atoms and bonds from the original molecule to their copies in the aglycone and sugar fragments (to retrieve atoms indices or an extracted fragment or to get group indices for all atoms in the original molecule</li>
</ul>

<p></p>All sugar detection and removal operations respect the settings inherited from the parent <i>SugarRemovalUtility</i> class, including terminal vs. non-terminal sugar removal, preservation mode settings, various detection thresholds, etc. (for documentation, see the code or the paper linked above)
<p></p>
<p>In two cases, the initial <i>SugarRemovalUtility</i> results are corrected for extraction:</p>
<ul>
    <li>When a sugar would lose its C6</li>
</ul>
<p></p>
<img width="3619" height="1345" alt="image" src="https://github.com/user-attachments/assets/755ceabb-71b5-4ca3-b37c-962e5a846237" />
<p></p>
<ul>
    <li>When a sugar is on the "carboxy end" of an ester bond to the aglycone</li>
<p></p>
<img width="3509" height="1367" alt="image" src="https://github.com/user-attachments/assets/1a1090fc-a0e5-4d97-9d7d-b5a8f4062468" />
<p></p>
</ul>
<p><strong>Basic Usage Example:</strong></p>
<pre>
SugarDetectionUtility utility = new SugarDetectionUtility(SilentChemObjectBuilder.getInstance());
//check the overloaded variants of this method for more options
List<IAtomContainer> fragments = utility.copyAndExtractAglyconeAndSugars(molecule);
IAtomContainer aglycone = fragments.get(0);  // First element is always the aglycone
// Subsequent elements are individual sugar fragments
</pre>

The code is documented and extensively tested.

If you want to see the SugarDetectionUtility in action, check out our [MOlecule fRagmenTAtion fRamework (MORTAR) application](https://github.com/FelixBaensch/MORTAR), the SDU will be part of the next release.

A paper describing the algorithm is coming up.

Looking forward to your feedback!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `acd73ce43873`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.