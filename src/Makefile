.PHONY: all

PROGRAMS = starter example

all: $(PROGRAMS)

PIE_FLAG = -fpie
#PIE_FLAG = -fno-pie

$(PROGRAMS):%:%.o asm64_io.o
	gcc ${PIE_FLAG} $^  -o $@

%.o : asm64_io.inc

%.o : %.asm
	nasm -f elf64 $< -o $@

.PHONY: clean zip

clean:
	rm -f *.o starter example

zip:
	zip ../asm64_io.zip Makefile asm64_io.asm asm64_io.inc example.asm starter.asm
