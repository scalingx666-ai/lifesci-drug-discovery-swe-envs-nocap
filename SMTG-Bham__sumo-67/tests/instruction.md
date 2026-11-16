# Issue

**Title:** Phonon bandplot: JSON dumping/loading, overlaying plots

## Description

Here's an attempt at #65 

So far we can dump a JSON of the Pymatgen object with `--to-json filename.json`, and select multiple of them to add to the plotting output with `--from-json bands-1.json bands-2.json ...`, . If no FORCE_SETS etc. is chosen but --from-json is set, then instead of looking for FORCE_SETS it will just plot the series of JSON files.

I tweaked the style file so the default green is a little darker and we get a green -> pale-blue sequence of up to four colours.

![phonon_band](https://user-images.githubusercontent.com/2511383/61541518-be0da800-aa37-11e9-9c60-708b45110e5f.png)

Todo:

- `--style` seems to be broken?
- Check the x-axis scaling is working correctly with some qha data. (If anyone has some lying around that would be great.)
- `--labels`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `507fdd225ab8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.