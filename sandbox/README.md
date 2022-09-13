This directory contains scratch files to test functionalities of "-fvalidate-ast-input-files-content"

**Standard compilation**:

```shell
clang -Xclang -fvalidate-ast-input-files-content -std=c++14 -o foo.h.pch -x c++-header foo.h
clang -Xclang -fvalidate-ast-input-files-content -c -include foo.h main.cpp
```

**With ccache**:

```shell
ccache --set-config sloppiness=pch_defines,time_macros
ccache clang -std=c++14 -o foo.h.pch -x c++-header foo.h
# clang implicitly loads "foo.h.pch" (from -include)
ccache clang -c -include foo.h main.cpp
```
