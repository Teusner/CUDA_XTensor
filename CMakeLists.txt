cmake_minimum_required(VERSION 3.0.2)
project(cuda_test LANGUAGES CUDA CXX)

# Cuda
enable_language(CUDA)
find_package(CUDA REQUIRED)

# XTensor
find_package(xtensor REQUIRED)

# GCC Compilation
add_executable(main_gcc main.cpp)
target_link_libraries(main_gcc PUBLIC xtensor)
target_include_directories(main_gcc PUBLIC ${xtensor_INCLUDE_DIRS})


# NVCC Compilation
add_executable(main_nvcc main.cu)
target_link_libraries(main_nvcc PUBLIC xtensor)
target_include_directories(main_nvcc PUBLIC ${CUDA_INCLUDE_DIRS} ${xtensor_INCLUDE_DIRS})
