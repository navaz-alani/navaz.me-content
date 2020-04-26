# The Concept of Programming Languages
*Understanding the motivation and key idea behind programming languages*

**Navaz Alani**, *Apr 25 2020*
****

This document aims to shed some light on the significance of programming languages
and, at a high level, how code is actually executed by the CPU.

## Instruction Sets

At the the very core of your computer is the Central Processing Unit (CPU). This is
basically the brain of your computer and does all of the information processing.
I think most people are already aware of the integral role that the CPU plays in
a computer but this document intends to go deeper. How does the CPU actually do what it
does? Of course, the answer provided here is just a **very** high level overview- there are
entire books written on this topic.

In essence, **a CPU is a machine which offers functionality through a particular set of
instructions**. Needless to say, this set of instructions is robust enough to make possible
all the computing that we observe today. The instructions can be grouped into three major
categories: data movement, arithmentic/logic and control flow (order of execution of
instructions).

A program is a **list of instructions to be executed by the CPU sequentially**. In the early
days of computing, computer scientists used to write programs using the CPU instruction set
itself. This was programming in *assembly language*. But as you can imagine, there are many
challenges associated with this. A few:

* Programs written for a particular CPU may not run on another CPU which implements
  a different instruction set
* The developer needs to have intricate knowledge of the CPU instruction set and
  implementation to be any good

This is where programming languages come in...

## Programming Languages

Programming languages provide a higher level of abstraction over the CPU instruction set.
The higher this level of abstraction, the higher the level of the programming language.
For example, C and Python are both programming languages, but they differ in the level of
abstraction that they provide over the CPU instruction set. C provides abstractions/constructs
which are much closer to the CPU's instruction set than Python's. As such, one may say that
C is, relative to Python, a low level programming langugage. But relative to assembly/machine
code, both C and Pyhton are regarded to be higher level programming langugages.

Programming langugages provide solutions to the problems above. From this point onwards, I shall
use C for examples most of the time as it's neither too high level nor loo low level. The C compiler
is a special program which enables one to generate low level machine dependent code from machine
independent C code.

* Programming languages can be implemented differently on different CPUs. For example, the C compiler
is implemented differently for an Intel i5 processor, compared to an i7 processor because the
instruction sets for these CPUs differ.
* The developer no longer needs to care about the CPU on which the code is to be executed.
The implementation of the programming langugage (in the case of C, the C compiler) for that
particular machine (architecture) will take care of that!

Let's see this in action!
Suppose one wants to write a program to print the text "Hello World!" onto the screen (I know this is
kind of a cliché, but its a simple enough demonstration). Here is the C source code which would
accomplish this task, stored in a file called `hello.c`:

```c
#include <stdio.h>
int main(void) {
	printf("Hello World!\n");
}
```

In order to see the equivalent assembly code (on my Dual-Core Intel Core i5 processor), we can use
the C compiler to compile it into assembly (`$` denotes a command line, `gcc` is a C compiler
program):

```bash
$ gcc -S hello.c
```

This command instructs the program `gcc` to compile the C source code in the file `hello.c` into
the corresponding assembly code. By default, this will output the assembly code in to a file called
`hello.s` (or `.asm`). If we take a look at the contents of `hello.s`, here's an example of what one
would see:

```asm
	.section	__TEXT,__text,regular,pure_instructions
	.build_version macos, 10, 15	sdk_version 10, 15, 4
	.globl	_main                   ## -- Begin function main
	.p2align	4, 0x90
_main:                                  ## @main
	.cfi_startproc
## %bb.0:
	pushq	%rbp
	.cfi_def_cfa_offset 16
	.cfi_offset %rbp, -16
	movq	%rsp, %rbp
	.cfi_def_cfa_register %rbp
	subq	$16, %rsp
	leaq	L_.str(%rip), %rdi
	movb	$0, %al
	callq	_printf
	xorl	%ecx, %ecx
	movl	%eax, -4(%rbp)          ## 4-byte Spill
	movl	%ecx, %eax
	addq	$16, %rsp
	popq	%rbp
	retq
	.cfi_endproc
                                        ## -- End function
	.section	__TEXT,__cstring,cstring_literals
L_.str:                                 ## @.str
	.asciz	"Hello World!\n"
```

Clearly, the assembly code is more intricate and requires a deeper understanding of CPU registers and
instructions in order to write- but a developer need not understand this when writing his/her source
code in C. From this example, it should be evident what "high level" means in the context of
programming langugages: with just 4 lines of C code, a developer can achieve what would take
over 20 lines of assembly code. Also, the generated assembly code is dependent on the architecture of
the machine, but the C code which produces the assembly code is NOT: the CPU has been completely
abstracted away by the programming language!
