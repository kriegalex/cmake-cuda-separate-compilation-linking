
# please make sure nvcc dir is in PATH
project(without-separate CXX CUDA)

# all .cu .cuh files in crt dir
file(GLOB MAIN_CU_SRCS ${CMAKE_CURRENT_SOURCE_DIR}/*.cu)
file(GLOB MAIN_CU_HDRS ${CMAKE_CURRENT_SOURCE_DIR}/*.cuh)
# only for CLion (derps without a cpp file)
file(GLOB DUMMY_SRCS dummy.cpp)

# modern cmake is cuda aware, cuda prefix is gone
add_executable(cmake-without-scl ${MAIN_CU_SRCS} ${MAIN_CU_HDRS} ${DUMMY_SRCS})