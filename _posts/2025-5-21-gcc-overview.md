---
layout: post
title: gcc编译概述
---

# 
gcc编译过程中会生成三种中间语言GENERIC(就是AST?), GIMPLE, RTL(Register Transfer Language)

使用`-fdump-tree-all`生成的.original文件就是GENERIC，生成的.gimple文件就是GIMPLE。感觉.gimple文件的可读性比.original好。
```
g++ -fdump-tree-all  -g -O0 -std=c++20 -pthread  test_co9.cpp -o  test_co9

test_co9.cpp.005t.original
test_co9.cpp.006t.gimple
test_co9.cpp.009t.omplower
test_co9.cpp.010t.lower
test_co9.cpp.012t.ehopt
test_co9.cpp.013t.eh
test_co9.cpp.014t.coro-lower-builtins
test_co9.cpp.015t.cfg
test_co9.cpp.016t.coro-early-expand-ifns
test_co9.cpp.017t.ompexp
test_co9.cpp.020t.fixup_cfg1
test_co9.cpp.021t.ssa
test_co9.cpp.022t.walloca1
test_co9.cpp.023t.warn-printf
test_co9.cpp.025t.waccess1
test_co9.cpp.029t.fixup_cfg2
test_co9.cpp.030t.local-fnsummary1
test_co9.cpp.031t.einline
test_co9.cpp.049t.profile_estimate
test_co9.cpp.053t.release_ssa
test_co9.cpp.054t.local-fnsummary2
test_co9.cpp.094t.fixup_cfg3
test_co9.cpp.095t.ehdisp
test_co9.cpp.101t.adjust_alignment
test_co9.cpp.240t.veclower
test_co9.cpp.241t.cplxlower0
test_co9.cpp.243t.switchlower_O0
test_co9.cpp.247t.ehcleanup2
test_co9.cpp.248t.resx
test_co9.cpp.250t.isel
test_co9.cpp.253t.waccess3
test_co9.cpp.254t.optimized
test_co9.cpp.341t.statistics
test_co9.cpp.342t.earlydebug
test_co9.cpp.343t.debug
```

使用`-fdump-rtl-all`可以生成很多rtl相关的中间文件
```
g++ -fdump-rtl-all  -g -O0 -std=c++20 -pthread  test_co9.cpp -o  test_co9

test_co9.cpp.255r.expand
test_co9.cpp.256r.vregs
test_co9.cpp.257r.into_cfglayout
test_co9.cpp.258r.jump
test_co9.cpp.270r.reginfo
test_co9.cpp.293r.outof_cfglayout
test_co9.cpp.294r.split1
test_co9.cpp.296r.dfinit
test_co9.cpp.297r.mode_sw
test_co9.cpp.298r.asmcons
test_co9.cpp.303r.ira
test_co9.cpp.304r.reload
test_co9.cpp.311r.pro_and_epilogue
test_co9.cpp.314r.jump2
test_co9.cpp.325r.split4
test_co9.cpp.326r.stack
test_co9.cpp.327r.zero_call_used_regs
test_co9.cpp.328r.alignments
test_co9.cpp.330r.mach
test_co9.cpp.331r.barriers
test_co9.cpp.334r.eh_ranges
test_co9.cpp.335r.endbr_and_patchable_area
test_co9.cpp.336r.shorten
test_co9.cpp.337r.nothrow
test_co9.cpp.338r.dwarf2
test_co9.cpp.339r.final
test_co9.cpp.340r.dfinish
```

# 参考资料

1. [Overview of GCC’s internals](https://gcc-python-plugin.readthedocs.io/en/latest/gcc-overview.html)
2. 《深入分析GCC-王亚刚》
3. [GENERIC](https://gcc.gnu.org/onlinedocs/gccint/GENERIC.html)
4. [GIMPLE](https://gcc.gnu.org/onlinedocs/gccint/GIMPLE.html)
5. [RTL](https://gcc.gnu.org/onlinedocs/gccint/RTL.html)



