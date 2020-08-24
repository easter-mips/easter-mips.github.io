# EasterCache

[EasterCache](https://github.com/easter-mips/EasterCache) 是使用 Chisel3 实现的，参数可配置的高性能 MIPS Cache。由于Cache在版本迭代过程中，为系统的引导引入了较为棘手的bug，因而最后提交包中使用的Cache并非为最新版本，而为分支`legacy-dcache`中的版本。仅仅使用了Chisel3开发的D-Cache，其余部分由SystemVerilog实现。

`master`分支为最新版本的Cache，完全由Chisel3实现，包含一个双发I-Cache，以及一个带有Victim Cache的D-Cache。相联度、行数、行大小都能非常容易的进行配置。
