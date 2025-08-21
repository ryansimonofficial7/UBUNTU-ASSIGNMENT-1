# UBUNTU-ASSIGNMENT-1
# PAIL-Ubantu
PAIL assignment
 # ASM code for hello world
 global _start

section .data
    hello db "Hello, World!", 10
    length equ $ - hello

section .text
_start:
    mov eax, 4
    mov ebx, 1
    mov ecx, hello
    mov edx, length
    int 0x80

    xor ebx, ebx
    mov eax, 1
    int 0x80






    # Print Name
    global _start

section .data
    firstName db "Ryan", 10
    firstLen  equ $ - firstName

    lastName  db "Simon", 10
    lastLen   equ $ - lastName

section .text
_start:
    mov eax, 4
    mov ebx, 1
    mov ecx, firstName
    mov edx, firstLen
    int 0x80

    mov eax, 4
    mov ebx, 1
    mov ecx, lastName
    mov edx, lastLen
    int 0x80

    mov eax, 1
    xor ebx, ebx
    int 0x80








# GDB use
(gdb) break _start
(gdb) run
(gdb) set disassembly-flavor intel
(gdb) disassemble _start
(gdb) layout asm
(gdb) layout regs
(gdb) nexti






#UBANTU-ASSIGNMENT-2
#ADDITION OF TWO 8 BIT NUMBER by accepting input from user and display on console

global _start

section .data
    msg1 db "Enter 1st Value:", 10
    msg1len equ $ - msg1

    msg2 db "Enter 2nd Value:", 10
    msg2len equ $ - msg2

    msg3 db "The addition is: "
    msg3len equ $ - msg3

    newline db 10

section .bss
    val1 resb 2
    val2 resb 2
    result resb 2

section .text
_start:
    mov eax, 4
    mov ebx, 1
    mov ecx, msg1
    mov edx, msg1len
    int 0x80

    mov eax, 3
    mov ebx, 0
    mov ecx, val1
    mov edx, 2
    int 0x80

    mov eax, 4
    mov ebx, 1
    mov ecx, msg2
    mov edx, msg2len
    int 0x80

    mov eax, 3
    mov ebx, 0
    mov ecx, val2
    mov edx, 2
    int 0x80

    mov al, [val1]
    sub al, '0'
    mov bl, [val2]
    sub bl, '0'

    add al, bl

    mov ah, 0
    mov bl, 10
    div bl

    add al, '0'
    mov [result], al

    add ah, '0'
    mov [result+1], ah

    mov eax, 4
    mov ebx, 1
    mov ecx, msg3
    mov edx, msg3len
    int 0x80

    mov eax, 4
    mov ebx, 1
    mov ecx, result
    mov edx, 2
    int 0x80

    mov eax, 4
    mov ebx, 1
    mov ecx, newline
    mov edx, 1
    int 0x80

    mov eax, 1
    xor ebx, ebx
    int 0x80

#UBUNTU ASSIGNMENT 3
#part 1
global _start
section .data
    val db 0
    vah db 0

section .text
_start:
    mov al,5
    mov bl,9
    mul bl

    aam
    add al,'0'
    mov [val],al
    add ah,'0'
    mov [vah],ah

    mov eax,4
    mov ebx,1
    mov ecx,vah
    mov edx,1
    int 80h

    mov eax,4
    mov ebx,1
    mov ecx,val
    mov edx,1
    int 80h

    mov eax,1
    mov ebx,0
    int 80h

#part 2 almost same code for addition and subtraction
section .text
global _start

_start:
    mov ax, 5
    mov bx, 3
    mul bx
    int 0x80
# part 3
global _start:
section .text
_start:
	mov ax , 30FAH
	MOV bx , 595BH
	add ax, bx
