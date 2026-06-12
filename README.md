# V8 – no Chromium

This repository is meant to build Google's [V8] JavaScript engine as a static
library (monolith). Its purpose is to provide a common place to maintain
a non-Chromium-based build pipeline of V8.

It still uses [GN] and [Ninja] but patches are applied based on the version
number when required. This is mostly meant to support Windows. As of [September
2024], Google dropped support for MSVC compiler / MSVC STL headers.

<!-- Links -->
[V8]: https://v8.dev/docs
[GN]: https://gn.googlesource.com/gn
[Ninja]: https://ninja-build.org/
[September 2024]: https://groups.google.com/g/v8-users/c/J8Q6VrX9e4M/m/DVJYVq8MAwAJ

## Usage

1. Download an [artifact].
2. Extract in the desired location (e.g. `vendors\v8\`).
3. Include headers (e.g. `vendors\v8\include`).
4. Link with the static library (e.g. `vendors\v8\lib\v8_monolith.lib`).
5. Enable features:
```
-DV8_COMPRESS_POINTERS
-DV8_ENABLE_SANDBOX
-DV8_ENABLE_WEBASSEMBLY
```
6. Build :)

<!-- Links -->
[artifact]: https://github.com/poirierlouis/v8-nocr/actions/runs/27419674917/artifacts/7596011761

## Guarantees

There are no guarantees regarding the quality of the build. It is provided
as-is. It currently lacks a workflow to run tests provided in V8's repository.

## Platforms and Features

### Versions

|      OS | Arch |       Version |
|--------:|-----:|--------------:|
| Windows |  x64 | [14.6.202.34] |

<!-- Links -->
[14.6.202.34]: https://github.com/poirierlouis/v8-nocr/actions/runs/27419674917/artifacts/7596011761

### Features

|      OS |   Arch | i18n | WebAssembly | Pointer Compression | Sandbox | Temporal |
|--------:|-------:|:----:|:-----------:|:-------------------:|:-------:|:--------:|
| Windows |    x64 |  ✅   |      ✅      |          ✅          |    ✅    |    ❌     |
| Windows |  arm64 |  -   |      -      |          -          |    -    |          |
|   Linux | x86_64 |  -   |      -      |          -          |    -    |          |
|   Linux |  arm64 |  -   |      -      |          -          |    -    |          |
