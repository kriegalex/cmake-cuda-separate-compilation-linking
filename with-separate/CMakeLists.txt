
# please make sure nvcc dir is in PATH
project(with-separate CXX CUDA)

# all .cu .cuh files in lib dir
file(GLOB LIB_CU_SRCS ${CMAKE_CURRENT_SOURCE_DIR}/lib/*.cu)
file(GLOB LIB_CU_HDRS ${CMAKE_CURRENT_SOURCE_DIR}/lib/*.cuh)
# all .cu .cuh files in crt dir
file(GLOB MAIN_CU_SRCS main.cu)
# only for CLion (derps without a cpp file)
file(GLOB DUMMY_SRCS dummy.cpp)

# modern cmake is cuda aware, cuda prefix is gone
add_library(cmake-with-scl-lib STATIC ${LIB_CU_SRCS} ${LIB_CU_HDRS})
# ask for separate compilation on lib
set_target_properties(cmake-with-scl-lib PROPERTIES CUDA_SEPARABLE_COMPILATION ON)
add_executable(cmake-with-scl ${MAIN_CU_SRCS} ${DUMMY_SRCS})
# AND ask for separate compilation on exec
set_target_properties(cmake-with-scl PROPERTIES CUDA_SEPARABLE_COMPILATION ON)
target_link_libraries(cmake-with-scl PRIVATE cmake-with-scl-lib)