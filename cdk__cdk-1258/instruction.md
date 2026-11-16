# Issue

**Title:** Update the connectivity checker to either respect/ignore (default) va…

## Description

…r/multi attach bonds and explicit component grouping.

The default behaviour is unchanged and returns connected component in the strict graph-theoretic sense but we now have the option to a more chemically meaningful splitting.

 <table>
      <tr><th>No. Strict Components</th><th>No. Loose Components</th><th>SMILES</th></tr>
      <tr><td>2</td><td>2</td><td><pre><img width="98" height="56" alt="image" src="https://github.com/user-attachments/assets/b914b606-1bc2-4337-8d4d-3267c04cf06a" /></pre></td></tr>
      <tr><td>2</td><td>1</td><td><pre><img width="55" height="71" alt="image" src="https://github.com/user-attachments/assets/4a2a675b-cdc4-4141-816c-489d355e3d1a" /></pre></td></tr>
      <tr><td>4</td><td>2</td><td><pre><img width="126" height="75" alt="image" src="https://github.com/user-attachments/assets/b523d7ae-be1f-46d5-9fb4-a7245cf40e7a" /></pre></td></tr>
      <tr><td>2</td><td>1</td><td><pre><img width="204" height="60" alt="image" src="https://github.com/user-attachments/assets/a4056728-9c01-4409-b954-1b8c4ad5a5bd" /></pre></td></tr>
      <tr><td>5</td><td>2</td><td><pre><img width="274" height="85" alt="image" src="https://github.com/user-attachments/assets/83f87b1f-e38b-4881-8208-b138882efc8b" /></pre></td></tr>
  </table>


I have renamed the "reaction group" property to the more generic "component group" and redirected the old constant

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a2c35ac55e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.