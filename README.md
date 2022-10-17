# dynamic_allocation_simulator (Memory Allocator)

A program which maintains a heap, allowing a user to allocate memory, free memory, and see the current state of the heap. Your program will accept user
commands and execute them.

The heap is 64 bytes long and memory is byte-addressable. The first address of the heap is address 0, so the last address of the heap is address 63.

Operations:

1. malloc <int size>

>malloc 10 // Comment: header at 0, payload from 1-10, footer at 11
  
1
>malloc 5 // Comment: header at 12, payload from 13-17, footer at 18
 
13
>malloc 2 // Comment: header at 19, payload from 20-21, footer at 22
 
20

2. free <int index>

>malloc 10
1
>malloc 5
13
>free 13
>free 1

3. blocklist
>malloc 10
1
>malloc 5
13

>blocklist
1, 10, allocated.
13, 5, allocated.
20, 43, free.

4. writemem <int index>, <char * str> 

>writemem 5 ABC
>printmem 5 3
41 42 43
Notice that the values 41, 42, and 43 are the hexadecimal representations of the ASCII values of the characters ‘A’, ‘B’, and ‘C’.
6. quit – This quits your program

Sample Execution
>malloc 10
1
>malloc 5
13
>blocklist
1, 10, allocated.
13, 5, allocated.
20, 43, free.
>free 1
>blocklist
1, 10, free.
13, 5, allocated.
20, 43, free.
>malloc 5
1
>blocklist
1, 5, allocated.
8, 3, free.
13, 5, allocated.
20, 43, free.
>writemem 1 HELLO
>printmem 1 5
48 45 4C 4C 4F
>free 13
>blocklist // Comment: You can see here that there was a
block allocated between 2 free blocks, on freeing that allocated
block, both the free blocks were coalesced into one free block.
1, 5, allocated.
8, 55, free.
>quit
$ <- back to bash prompt.
