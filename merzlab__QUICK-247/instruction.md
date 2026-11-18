# Issue

**Title:** GPU porting of new grid weight derivative algorithm

## Description

I have ported new grid weight derivative algorithm to GPU.  The computed gradients are as accurate as ones resulting from Tim's CPU implementation. Eg. PSB5 gradients at B3LYP/6-31G level of theory (serial on left, cuda on right)

> ----------------------------------------			----------------------------------------
>  COORDINATE    XYZ            GRADIENT				 COORDINATE    XYZ            GRADIENT
> ----------------------------------------			----------------------------------------
>     1X    -1.2017471418    -0.0046821407		      |	    1X    -1.2017471418    -0.0046821348
>     1Y     0.4258140325    -0.0156725855		      |	    1Y     0.4258140325    -0.0156725974
>     1Z     4.7428184122     0.0376439199		      |	    1Z     4.7428184122     0.0376439111
>     2X    -1.3660225743    -0.0021278961		      |	    2X    -1.3660225743    -0.0021279004
>     2Y     1.5848010010     0.0154644401		      |	    2Y     1.5848010010     0.0154644510
>     2Z     3.9624240526    -0.0109909137		      |	    2Z     3.9624240526    -0.0109909106
>     3X    -1.0188797978     0.0012952327		      |	    3X    -1.0188797978     0.0012952321
>     3Y     1.5693751598    -0.0141956394		      |	    3Y     1.5693751598    -0.0141956222
>     3Z     2.6313203409     0.0126019153		      |	    3Z     2.6313203409     0.0126018966
>     4X    -1.7630289046     0.0028100567		      |	    4X    -1.7630289046     0.0028100544
>     4Y     2.4739650089    -0.0066633974		      |	    4Y     2.4739650089    -0.0066633947
>     4Z     4.4193730175    -0.0028154120		      |	    4Z     4.4193730175    -0.0028154060
>     5X    -1.1390552170    -0.0008180337		      |	    5X    -1.1390552170    -0.0008180319
>     5Y     2.6728435541     0.0112014209		      |	    5Y     2.6728435541     0.0112014083
>     5Z     1.7501491136    -0.0107328029		      |	    5Z     1.7501491136    -0.0107327951
>     6X    -0.6253332978    -0.0032202570		      |	    6X    -0.6253332978    -0.0032202565
>     6Y     0.6538894299     0.0072565558		      |	    6Y     0.6538894299     0.0072565566
>     6Z     2.2204718696     0.0036264176		      |	    6Z     2.2204718696     0.0036264147
> 

After optimizations, the new implementation is several times faster than old less accurate algorithm (eg. 478 ms vs 3.26 s kernel time for Taxol B3LYP/STO-3G test on Titan V). The new kernel only consumes ~110 registers per thread. The performance can be further improved by increasing the number of threads per block. I have set this to 256 for now because the size of a temporary device array  depends on it: https://github.com/Madu86/QUICK/blob/sswder/src/cuda/gpu.cu#L2144 . Increasing this too much may cause problems when running calculations of large molecular systems on cards with low device memory. We should increase the tpb after a systematic study. 
I have also made changes to call Tim's grid weight derivative implementation in CPU version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2bf3da57ea4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.