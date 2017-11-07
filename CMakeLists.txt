# CMake 3.9 required
cmake_minimum_required(VERSION 3.9 FATAL_ERROR)

# help debugging Makefile cmd if ON
set(CMAKE_VERBOSE_MAKEFILE OFF)

# Save libs and executables in the same place
set(EXECUTABLE_OUTPUT_PATH "${CMAKE_BINARY_DIR}/bin" CACHE PATH
    "Output directory for applications")

# help CLion engine with CUDA headers
include_directories(/usr/local/cuda/include)

add_subdirectory(with-separate)
add_subdirectory(without-separate)