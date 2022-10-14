# SGEMM-GPU-Kernel-Performance

This data set measures the running time of a matrix-matrix product  𝐴∗𝐵=𝐶 , 

where all matrices have size 2048 x 2048, using a parameterizable SGEMM GPU kernel with 241600 possible parameter combinations. 

For each tested combination, 4 runs were performed and their results are reported as the 4 last columns. 

All times are measured in milliseconds*.

There are 14 parameter, the first 10 are ordinal and can only take up to 4 different powers of two values, and the 4 last variables are binary. 

Out of 1327104 total parameter combinations, only 241600 are feasible (due to various kernel constraints). 

This data set contains the results for all these feasible combinations.

*The experiment was run on a desktop workstation running Ubuntu 16.04 Linux with an Intel Core i5 (3.5GHz), 16GB RAM, and a NVidia Geforce GTX 680 4GB GF580 GTX-1.5GB GPU. We use the 'gemm_fast' kernel from the automatic OpenCL kernel tuning library 'CLTune' ([Web Link]).*


## Independent variables:
- MWG, NWG: per-matrix 2D tiling at workgroup level: {16, 32, 64, 128} (integer)
- KWG: inner dimension of 2D tiling at workgroup level: {16, 32} (integer)
- MDIMC, NDIMC: local workgroup size: {8, 16, 32} (integer)
- MDIMA, NDIMB: local memory shape: {8, 16, 32} (integer)
- KWI: kernel loop unrolling factor: {2, 8} (integer)
- VWM, VWN: per-matrix vector widths for loading and storing: {1, 2, 4, 8} (integer)
- STRM, STRN: enable stride for accessing off-chip memory within a single thread: {0, 1} (categorical)
- SA, SB: per-matrix manual caching of the 2D workgroup tile: {0, 1} (categorical)

## Output:

- Run1, Run2, Run3, Run4: performance times in milliseconds for 4 independent runs using the same parameters. 
- They range between 13.25 and 3397.08.
