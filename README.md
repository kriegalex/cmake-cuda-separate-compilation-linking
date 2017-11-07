# Separate Compilation Linking with CMake
This example builds on the [parallel-forall repo][1] separate compilation example by adding CMake to it.

## Compile and launch

```bash
git clone https://github.com/kriegalex/cmake-cuda-separate-compilation-linking.git cmake-cuda-scl
cd cmake-cuda-scl
mkdir build && cd build
cmake -DCMAKE_CUDA_FLAGS="-arch=sm_60" ..
make -j4
cd bin/
```

Please change *-arch=sm_60* according to [your GPU compute capability][2].

[1]: https://github.com/parallel-forall/code-samples/tree/master/posts/separate-compilation-linking
[2]: https://en.wikipedia.org/wiki/CUDA#GPUs_supported
