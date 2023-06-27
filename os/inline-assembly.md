#### x86-specific constraints that bind to named registers
[x86 family章节](https://gcc.gnu.org/onlinedocs/gcc/Machine-Constraints.html#Machine-Constraints)
[what-do-the-0-9-constraints-do-in-gcc-inline-assembly](https://stackoverflow.com/questions/57485761/what-do-the-0-9-constraints-do-in-gcc-inline-assembly)
```console
a, b, c, d: the a, b, c, d registers, respectively (the "a" register being contextually al, ax, eax or rax, for example)
D: the di register
S: the si register
```
