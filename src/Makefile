all: starter example

PIE_FLAG = -fpie
#PIE_FLAG = -fno-pie

starter: starter.o  asm64_io.o driver64.o
	gcc ${PIE_FLAG} driver64.o asm64_io.o starter.o -o starter	
	
starter.o: starter.asm 
	nasm -f elf64 $< -o $@


asm64_io.o: asm64_io.asm
	nasm -f elf64 asm64_io.asm -o asm64_io.o
	
driver64.o: driver64.c asm64_io.inc
	gcc ${PIE_FLAG} -c driver64.c -o driver64.o 
	
example.o: example.asm
	nasm -f elf64 example.asm  -o example.o

example: driver64.o asm64_io.o example.o
	gcc ${PIE_FLAG} driver64.o asm64_io.o example.o  -o example	
	

.PHONY: clean
clean:
	rm -f *.o starter example
