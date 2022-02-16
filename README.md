# Cuda Xtensor

A minimal not working example showing a compilation problem of xtensor using nvcc.

# Compiler versions

## C++ compiler version
```bash
> c++ --version
c++ (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0
```

## NVCC Version
```bash
> nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2019 NVIDIA Corporation
Built on Sun_Jul_28_19:07:16_PDT_2019
Cuda compilation tools, release 10.1, V10.1.243
```

# Problem
When the following line is uncommented in main.cu, nvcc isn't able to compile the code.
```c++
#include <xtensor/xtensor.hpp>
```

Compilation fail message :
```bash
> make
Scanning dependencies of target main_nvcc
[ 25%] Building CUDA object CMakeFiles/main_nvcc.dir/main.cu.o
/***/***/install/include/xtensor/xexpression.hpp:102:67: error: ‘xt::xsharable_expression’ is not a type
         friend xshared_expression<D> detail::make_xshared_impl<D>(xsharable_expression<D>&&);
                                                                   ^~~~~~~~~~~~~~~~~~~~
make[2]: *** [CMakeFiles/main_nvcc.dir/build.make:63 : CMakeFiles/main_nvcc.dir/main.cu.o] Erreur 1
make[1]: *** [CMakeFiles/Makefile2:78 : CMakeFiles/main_nvcc.dir/all] Erreur 2
make: *** [Makefile:84 : all] Erreur 2
```

> Note : `/***/***/` stands for a deliberately masked path :wink: