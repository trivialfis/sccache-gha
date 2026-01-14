# Temporary repository for the rapidsai fork sccache GitHub composite action

A composite GitHub Action that sets up [rapidsai/sccache](https://github.com/rapidsai/sccache) with GitHub Actions cache support using `actions/cache`.

## Windows Note

On Windows, you must use the **Ninja generator** (`-G Ninja`) with CMake. The default Visual Studio/MSBuild generator does not respect `CMAKE_CXX_COMPILER_LAUNCHER` and will not use sccache.

```yaml
- name: Configure CMake (Windows)
  if: runner.os == 'Windows'
  run: |
    cmake -B build -S . -G Ninja \
      -DCMAKE_BUILD_TYPE=Release \
      -DCMAKE_C_COMPILER_LAUNCHER=sccache \
      -DCMAKE_CXX_COMPILER_LAUNCHER=sccache
```