# SPDX-License-Identifier: GPL-2.0
#
# Makefile for the x86 low level entry code
#

KASAN_SANITIZE := n
UBSAN_SANITIZE := n
KCOV_INSTRUMENT := n

CFLAGS_REMOVE_syscall_32.o	= $(CC_FLAGS_FTRACE)
CFLAGS_REMOVE_syscall_64.o	= $(CC_FLAGS_FTRACE)

CFLAGS_syscall_32.o		+= -fno-stack-protector
CFLAGS_syscall_64.o		+= -fno-stack-protector

obj-y				:= entry.o entry_$(BITS).o syscall_$(BITS).o

obj-y				+= vdso/
obj-y				+= vsyscall/

obj-$(CONFIG_PREEMPTION)	+= thunk.o
CFLAGS_entry_fred.o		+= -fno-stack-protector
CFLAGS_REMOVE_entry_fred.o	+= -pg $(CC_FLAGS_FTRACE)
obj-$(CONFIG_X86_FRED)		+= entry_64_fred.o entry_fred.o

obj-$(CONFIG_IA32_EMULATION)	+= entry_64_compat.o syscall_32.o
