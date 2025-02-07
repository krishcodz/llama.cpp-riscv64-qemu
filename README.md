## To run llama.cpp on qemu - riscv64

### 1. Copy these files into the llama.cpp

### 2. Run these commands :

```bash
mkdir build && cd build
```

```bash
cmake .. -DCMAKE_C_COMPILER=riscv64-unknown-linux-gnu-gcc -DCMAKE_CXX_COMPILER=riscv64-unknown-linux-gnu-g++ -DCMAKE_C_FLAGS="-march=rv64gc -mabi=lp64d" -DCMAKE_CXX_FLAGS="-march=rv64gc -mabi=lp64d"
```

```bash
make -j$(nproc)
```

```bash
qemu-riscv64 -L /path/to/sysroot/ -cpu rv64,v=true,vlen=256,elen=64,vext_spec=v1.0 ./bin/llama-cli -m /path/to/model.gguf -p "Hi" -n 100
```
