---
title: C 是如何工作的
mermaid: true
---

C 语言从代码到可执行文件需要经过以下过程

<div class="mermaid">
flowchart LR
  A[预处理] -.-> B(编译) -.-> C(汇编) -.-> D[链接]
</div>

以 `hello.c` 为例，本文讲讲 C 语言的编译过程。

```c
#include <stdio.h>

int main() {
    printf("hello world!\n");
    return 0;
}
```

## 1. 预处理

预处理过程（Preprocessing）包含两项工作：引入头文件（Include Header）和拓展宏（Expand Macro）。

通过调用如下命令对 `hello.c` 进行预处理：

```bash
gcc -E hello.c > hello.i
```

该命令会在 `hello.c` 所在目录下生成一个 `hello.i` 文件，该文件显然比 `hello.c` 大了不少，可以用文本编辑器打开。

## 2. 编译

编译过程将预处理后的文本转换成汇编代码（Assembly Code）。

通过调用如下命令对 `hello.i` 进行编译：

```bash
gcc -S hello.i
```

该命令会在 `hello.i` 所在目录下生成一个 `hello.s` 文件，点开后可以发现文本里的内容如下：

```bash
	.section	__TEXT,__text,regular,pure_instructions
	.build_version macos, 13, 0	sdk_version 13, 1
## -- Begin function main
	.globl	_main                
	.p2align	4, 0x90
_main: ## @main
	.cfi_startproc
## %bb.0:
	pushq	%rbp
	.cfi_def_cfa_offset 16
	.cfi_offset %rbp, -16
	movq	%rsp, %rbp
	.cfi_def_cfa_register %rbp
	subq	$16, %rsp
	movl	$0, -4(%rbp)
	leaq	L_.str(%rip), %rdi
	movb	$0, %al
	callq	_printf
	xorl	%eax, %eax
	addq	$16, %rsp
	popq	%rbp
	retq
	.cfi_endproc
## -- End function
	.section	__TEXT,__cstring,cstring_literals
L_.str: ## @.str
	.asciz	"hello world!\n"

.subsections_via_symbols
```

汇编代码是机器代码的助记形式，每条汇编都有其对应的机器代码。

## 3. 汇编

汇编（Assemble）过程将 `hello.s` 文件中的汇编代码转换成机器码（Machine Code）。

通过调用如下命令对 `hello.s` 进行汇编：

```bash
gcc -c hello.s
```

该命令会在 `hello.i` 所在目录下生成一个 `hello.o` 文件，此文件称为目标文件，里面的内容全是二进制数字。

## 4. 链接

每个 `.c` 文件都会生成一个 `.o` 文件，同时有些项目还需要系统库的支持，最后一步就是将这些文件链接（Linking）在一起，形成一个可执行文件。

执行如下命令：

```bash
gcc hello.o -o hello
```

该命令会在 `hello.o` 所在目录下生成一个 `hello` 文件，该文件就是最后的可执行文件，可以直接点击执行。