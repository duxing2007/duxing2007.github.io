---
layout: post
title: gcc编译概述
---

# 
gcc编译过程中会生成三种中间语言GENERIC(就是AST), GIMPLE, RTL(Register Transfer Language)

使用`-fdump-tree-all`生成的.original文件就是GENERIC，生成的.gimple文件就是GIMPLE。感觉.gimple文件的可读性比.original好。
```
g++ -fdump-tree-all  -g -O0 -std=c++20 -pthread  test_co9.cpp -o  test_co9

test_co9.cpp.005t.original
test_co9.cpp.006t.gimple
test_co9.cpp.009t.omplower
```

使用`-fdump-rtl-all`可以生成很多rtl相关的中间文件
```
g++ -fdump-rtl-all  -g -O0 -std=c++20 -pthread  test_co9.cpp -o  test_co9

test_co9.cpp.255r.expand
test_co9.cpp.256r.vregs
test_co9.cpp.340r.dfinish
```

# 参考资料

1. [Overview of GCC’s internals](https://gcc-python-plugin.readthedocs.io/en/latest/gcc-overview.html)
2. 《深入分析GCC-王亚刚》
3. [GENERIC](https://gcc.gnu.org/onlinedocs/gccint/GENERIC.html)
4. [GIMPLE](https://gcc.gnu.org/onlinedocs/gccint/GIMPLE.html)
5. [RTL](https://gcc.gnu.org/onlinedocs/gccint/RTL.html)



