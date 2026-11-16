# Issue

**Title:** Fix OpenMP memory leak and segfault in fragment Hessian diagonalization

## Description

This commit resolves a  segmentation fault and massive memory consumption in the GFN-FF fragment Hessian diagonalization (`frag_hess.f90`). 

The original implementation used a large automatic array `hess_mask` (size 3N x 3N) inside an OpenMP parallel region, leading to stack overflows on systems with moderate atom counts (~2000+). Additionally, an OpenMP `reduction(+:ev_calc)` on the eigenvector matrix caused each thread to allocate a private copy of the full matrix, resulting in O(N_threads * N_atoms^2) memory usage and OOM crashes.

Changes:
- Removed the `hess_mask` automatic array.
- Replaced the OpenMP reduction with shared memory access guarded by `!$omp critical`.
- Replaced array intrinsics (`pack`/`unpack`) with explicit loops to handle fragment data, improving efficiency and reducing memory overhead.

Outcomes:
- Didn't see any performance drop.
- The segfault is gone for me on ~3k atoms systems. 
- Apparently uses much less memory. Further, it doesn't require OMP_STACKSIZE to be increased.  

Less technical story:
Generally I had a problem with the frequency calculations when I did use --bhess with 3k+ atom systems. Setting OMP_STACKSIZE and unlimit wasn't helping (the program did run until it ran out of the memory).
So I did some debugging why by compiling with `-g -traceback -check bounds` and ran through gdb to get:
```
metadynamics with 1 initial structures loaded
           -------------------------------------------------
          |           Optimal kpush determination           |
           -------------------------------------------------
 * fragmented diagonalization... 9 fragments
warning: Could not recognize version of Intel Compiler in: "Intel(R) Fortran 25.0-1373"

Thread 25 "xtb" received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x1554f67f3300 (LWP 235702)]
0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
351	!$omp parallel default(none) &
Missing separate debuginfos, use: yum debuginfo-install glibc-2.28-225.el8.x86_64 libgcc-8.5.0-18.el8.x86_64
(gdb) set pagination off
(gdb) bt
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () from /soft_rocky8/compilers/intel/intel-oneapi-hpc-toolkit-2025.1.0.666/compiler/2025.1/lib/libiomp5.so
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=24) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b089600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b089600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6
(gdb) thread apply all bt

Thread 32 (Thread 0x1554f4be5680 (LWP 235709)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=31) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b070100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b070100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 31 (Thread 0x1554f4fe7600 (LWP 235708)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=30) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b071600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b071600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 30 (Thread 0x1554f53e9580 (LWP 235707)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=29) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b072b00) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b072b00) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 29 (Thread 0x1554f57eb500 (LWP 235706)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=28) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b078100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b078100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 28 (Thread 0x1554f5bed480 (LWP 235705)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=27) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b079600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b079600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 27 (Thread 0x1554f5fef400 (LWP 235704)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=26) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b07ab00) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b07ab00) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 26 (Thread 0x1554f63f1380 (LWP 235703)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=25) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b088100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b088100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 25 (Thread 0x1554f67f3300 (LWP 235702)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=24) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b089600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b089600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 24 (Thread 0x1554f6bf5280 (LWP 235701)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=23) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b08ab00) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b08ab00) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 23 (Thread 0x1554f6ff7200 (LWP 235700)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=22) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b090100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b090100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 22 (Thread 0x1554f73f9180 (LWP 235699)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=21) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b091600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b091600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 21 (Thread 0x1554f77fb100 (LWP 235698)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=20) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b092b00) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b092b00) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 20 (Thread 0x1554f7bfd080 (LWP 235697)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=19) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b094100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b094100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 19 (Thread 0x1554f7fff000 (LWP 235696)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=18) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b095600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b095600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 18 (Thread 0x1555307e2f80 (LWP 235695)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=17) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b096b00) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b096b00) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 17 (Thread 0x155530be4f00 (LWP 235694)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=16) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b09c100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b09c100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 16 (Thread 0x155530fe6e80 (LWP 235693)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=15) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b09d600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b09d600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 15 (Thread 0x1555313e8e00 (LWP 235692)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=14) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b09eb00) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b09eb00) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 14 (Thread 0x1555317ead80 (LWP 235691)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=13) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0b0100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0b0100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 13 (Thread 0x155531becd00 (LWP 235690)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=12) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0b1600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0b1600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 12 (Thread 0x155531feec80 (LWP 235689)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=11) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0b2b00) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0b2b00) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 11 (Thread 0x1555323f0c00 (LWP 235688)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=10) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0b8100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0b8100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 10 (Thread 0x1555327f2b80 (LWP 235687)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=9) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0b9600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0b9600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 9 (Thread 0x155532bf4b00 (LWP 235686)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=8) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0bab00) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0bab00) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 8 (Thread 0x155532ff6a80 (LWP 235685)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=7) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0bc100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0bc100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 7 (Thread 0x1555333f8a00 (LWP 235684)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=6) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0bd600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0bd600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 6 (Thread 0x1555337fa980 (LWP 235683)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=5) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0beb00) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0beb00) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 5 (Thread 0x155533bfc900 (LWP 235682)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=4) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0c4100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0c4100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 4 (Thread 0x155533ffe880 (LWP 235681)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=3) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0c5600) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0c5600) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 3 (Thread 0x15553860c800 (LWP 235680)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=2) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0c6b00) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0c6b00) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 2 (Thread 0x155538a0e780 (LWP 235679)):
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#1  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#2  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=1) at ../../src/kmp_runtime.cpp:8401
#3  0x000015554dcc9aae in __kmp_launch_thread (this_thr=0x15554b0e0100) at ../../src/kmp_runtime.cpp:6647
#4  0x000015554dd4c9a2 in __kmp_launch_worker (thr=0x15554b0e0100) at ../../src/z_Linux_util.cpp:702
#5  0x000015554d2481ca in start_thread () from /lib64/libpthread.so.0
#6  0x000015554ccb0e73 in clone () from /lib64/libc.so.6

Thread 1 (Thread 0x1555553dbdc0 (LWP 235673)):
#0  0x00000000030c210a in __intel_avx_rep_memset ()
#1  0x0000000001dea846 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:355
#2  0x000015554dd4b483 in __kmp_invoke_microtask () at ../../src/z_Linux_util.cpp:3181
#3  0x000015554dccaff3 in __kmp_invoke_task_func (gtid=0) at ../../src/kmp_runtime.cpp:8401
#4  0x000015554dcc432c in __kmp_fork_call (loc=0x394ce60, gtid=0, call_context=fork_context_intel, argc=17, microtask=<optimized out>, invoker=0x15554dccae80 <__kmp_invoke_task_func(int)>, ap=0x7fffeea3cca0) at ../../src/kmp_runtime.cpp:2711
#5  0x000015554dc85400 in __kmpc_fork_call (loc=0x394ce60, argc=17, microtask=0x1dea680 <xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515>) at ../../src/kmp_csupport.cpp:392
#6  0x0000000001e04179 in xtb_gfnff_fraghess::frag_hess_diag (nat=<optimized out>, hess=..., eig_calc=..., ispinsyst=<error reading variable: value requires 56880000 bytes, which is more than max-value-size>, nspinsyst=..., nsystem=9) at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
#7  0x000000000193f6d7 in xtb_relaxation_engine::l_ancopt (env=..., ilog=<optimized out>, mol=..., chk=..., calc=..., optlevel=<optimized out>, maxcycle_in=59546808, energy=6.9533558049271316e-310, egap=6.9533558049283173e-310, gradient=..., sigma=..., printlevel=-66612, fail=4294903548) at /home/wiczew1/build/xtb/src/relaxation_engine.f90:646
#8  0x00000000014d6184 in xtb_geoopt::geometry_optimization (env=..., mol=..., wfn=..., calc=..., egap=0, et=300, maxiter=59546596, maxcycle_in=59546808, etot=6.9533558049271316e-310, g=<error reading variable: value requires 68256 bytes, which is more than max-value-size>, sigma=..., tight=59546800, pr=51188116, initial_sp=51196600, fail=4294903548) at /home/wiczew1/build/xtb/src/geoopt_driver.f90:153
#9  0x00000000014fa2b8 in xtb_kopt::get_rmsd (calc=..., env=..., restart=<optimized out>, mol=..., chk=..., egap=<optimized out>, et=<optimized out>, maxiter=59546596, maxcycle=59546808, optlev=59546800, etot=6.9533558049271316e-310, g=..., sigma=..., rmsdval=6.953355804802627e-310) at /home/wiczew1/build/xtb/src/getkopt.f90:142
#10 0x00000000014f85f1 in xtb_kopt::get_kopt (metaset=..., env=..., restart=<optimized out>, mol=..., chk=..., calc=..., egap=6.9533558049283173e-310, et=2.9419945196751038e-316, maxiter=59546596, maxcycle=59546808, optlev=59546800, etot=6.9533558049271316e-310, g=..., sigma=..., acc=2.9419929386650371e-316) at /home/wiczew1/build/xtb/src/getkopt.f90:80
#11 0x000000000044ae16 in xtb_prog_main::xtbmain (env=..., argparser=...) at /home/wiczew1/build/xtb/src/prog/main.F90:727
#12 0x000000000046e4e0 in xtb_prog_primary () at /home/wiczew1/build/xtb/src/prog/primary.f90:57
#13 0x000000000040a17d in main ()
#14 0x000015554ccb1d85 in __libc_start_main () from /lib64/libc.so.6
#15 0x000000000040a09e in _start ()
(gdb) frame 0
#0  0x0000000001dea6d1 in xtb_gfnff_fraghess_mp_frag_hess_diag_.DIR.OMP.PARALLEL.2.split.split2515 () at /home/wiczew1/build/xtb/src/gfnff/frag_hess.f90:351
351	!$omp parallel default(none) &
(gdb) list 340,380
340	        logical                  :: hess_mask(3*nat,3*nat)       ! masked hessian array
341	        real(sp)                 :: ev_calc(3*nat,3*nat)         ! eigenvectors of entire system
342	        real(sp), allocatable    :: mini_hess(:,:)               ! eigenvectors of fragment
343	        real(sp), allocatable    :: eig(:)                       ! eigenvalues of fragment
344	        real(sp), allocatable    :: aux(:)                       ! for ssyev
345	
346	
347	        ev_calc  = 0.0e0_sp
348	        eig_calc = 0.0e0_sp
349	        nat3     = 3 * nat
350	
351	!$omp parallel default(none) &
352	!$omp private(isystem,i,ii,j,jj,nat_cur,nat3_cur,mini_hess,hess_mask,eig,lwork,aux,info) &
353	!$omp shared(nsystem,ev_calc,eig_calc,hess,nspinsyst,ispinsyst)
354	!!$omp do schedule(static)
355	!$omp do reduction(+:ev_calc,eig_calc)
356	        do isystem = 1 , nsystem
357	           hess_mask = .false.
358	           do i = 1,nspinsyst(isystem)
359	              do j = 1,i
360	
361	                 nat_cur =  nspinsyst(isystem)
362	                 nat3_cur = 3 * nat_cur
363	                 ii = 3*ispinsyst(i,isystem)
364	                 jj = 3*ispinsyst(j,isystem)
365	                 hess_mask(ii-2:ii,jj-2:jj) = .true.
366	                 hess_mask(jj-2:jj,ii-2:ii) = .true.
367	
368	               end do
369	           end do
370	
371	           allocate( mini_hess(nat3_cur,nat3_cur), source = 0.0e0_sp )
372	           allocate( eig(nat3_cur), source = 0.0e0_sp )
373	
374	           mini_hess = reshape( pack( hess, mask = hess_mask ), shape( mini_hess ) )
375	           lwork = 1 + 6*nat3_cur + 2*nat3_cur**2
376	           allocate(aux(lwork))
377	           call ssyev ('V','U',nat3_cur,mini_hess,nat3_cur,eig,aux,lwork,info)
378	           deallocate(aux)
379	!!$omp critical
380	           ev_calc  = unpack( reshape( mini_hess, [ nat3_cur*nat3_cur ]  ), mask = hess_mask, field = ev_calc )
(gdb) 
381	           eig_calc = unpack( eig, mask = any(hess_mask,1), field = eig_calc )
382	!!$omp end critical
383	
384	           deallocate( mini_hess,eig )
385	
386	        end do
387	!$omp end do
388	!$omp end parallel
389	
390	        do i = 1,nat3
(gdb) 

```


Things to review: What about the `!$omp do schedule(dynamic)` - better to use here  static or dynamic ?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f79eac83cc61`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.