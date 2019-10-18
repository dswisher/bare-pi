#
# Based on https://github.com/bztsrc/raspi3-tutorial
#

SRCS     = $(wildcard *.c)
OBJS     = $(SRCS:.c=.o)

LLVM_BIN = /usr/local/opt/llvm/bin

CC       = $(LLVM_BIN)/clang
LLD      = $(LLVM_BIN)/ld.lld
OBJCOPY  = $(LLVM_BIN)/llvm-objcopy

CFLAGS   = -Wall -O2 -ffreestanding -nostdinc -nostdlib


all: clean kernel8.img

start.o: start.S
	$(CC) --target=aarch64-elf $(CFLAGS) -c start.S -o start.o

%.o: %.c
	clang --target=aarch64-elf $(CFLAGS) -c $< -o $@

kernel8.elf: start.o $(OBJS)
	$(LLD) -m aarch64elf -nostdlib start.o $(OBJS) -T link.ld -o kernel8.elf

kernel8.img: kernel8.elf
	$(OBJCOPY) --input-target aarch64-elf --output-target binary kernel8.elf kernel8.img

clean:
	rm -rf kernel8.elf *.o

run:
	qemu-system-aarch64 -M raspi3 -kernel kernel8.img -d in_asm

