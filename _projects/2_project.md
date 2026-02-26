---
layout: page
title: ARM Neoverse-N1 Compiler Options
description: Benchmarking toolchain for HPC flagships softwares on ARM Neoverse-N1 CPU
img: assets/img/headline/arm_flagship_benchmark.png
importance: 2
category: work
giscus_comments: true
---

Our supercomputing node 07 is equipped with an ARM Neoverse-N1 CPU. Our all baseline softwares are 64-bit running binaries.

However, before making changes, the toolchain will save copies of all of these. In detail, in this version, we only make changes at run-time. These changes
will be merged later if all results are ready and reliable. All workflow scripts can be found under the tools directory.
We used Spack to manage multiple packages and software.
Some benchmarks (e.g. HPL, MiniFE, ...) depend on Math-
Kernel Library (MKL) to compile source code. The existing
framework uses Intel MKL, which primarily targets Intel
processors and there is no available version for ARM archi-
tectures. In this case, we compiled OpenBLAS [cite Github
here], an open-source alternative to MKL, and linked against
these benchmarks.
For the M V M C benchmark, we need to further install
Scalable Linear Algebra PACKage (ScaLAPACK) from source
[2] and run the test in Python 2.7 virtual environment (created
from Anaconda).
For the High-Performance Linpack (HPL) benchmark com-
piled with OpenBLAS as the linked library, the optimal result
appears to be impractical. The most efficient run configuration
was observed to be 12|2, achieving a wall time of around
249.628 seconds. Considering that a 12|2 configuration on
a 128-core system is not feasible, we conducted a matrix-
multiplication test using the dgemm function from Open-
BLAS and ARMPL to ascertain the flop/s performance of
an individual core. The results are shown in table III. Sub-
sequently, upon recompiling HPL to link with ARM Perfor-
mance Libraries (ARMPL) [3], the best test run configuration
was 16|8, resulting in a wall time of approximately 226.108
seconds, equivalent to a performance rate of 147.7 Gflop/s.
Despite the performance exhibited by HPL in both scenarios
being quite low, the latter configuration better aligns with the
specifications of the current 128-core system.

<!-- **Table III. Performance of single core using dgemm** -->
<p class="text-muted" style="margin-top:0.5rem;">
  <strong>Table III.</strong> Performance of single core using <code>dgemm</code>.
</p>

|         | cblas_dgemm (OpenBLAS) | dgemm (ARMPL) |
| ------- | ---------------------: | ------------: |
| GFLOP/s |                 19.477 |        20.809 |

**Steps to compile**

```bash
# This is a bash comment
mkdir m4_source
cd m4_source
wget https://ftp.gnu.org/gnu/m4/m4-1.4.19.tar.gz
tar -xzvf m4-1.4.19.tar.gz

export CC=clang
export CXX=clang++
./configure --prefix=$HOME/m4_source/m4-1.4.19/
make && make install

export PATH=$HOME/m4_source/m4-1.4.19/bin:$PATH
```
