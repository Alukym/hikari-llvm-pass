# hikari-llvm-pass

```bash
mkdir -p build
pushd build
cmake -G Ninja -DCMAKE_BUILD_TYPE=Release ../
cmake --build .
popd
```

## References
[Android NDK r27 Clang 18 Hikari 混淆器 LLVM Pass 插件加载方案](https://eterocell.com/posts/7dbf3410/)