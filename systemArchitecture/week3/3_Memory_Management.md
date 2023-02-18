# Memory Management

## Virtual Memory
* Each process has its own private address space that is translated to the machine's physical address.
* This translation is defined in a page table.
* Translations are simplified by assuming locality, dividing space into pages and not single words. (Each entry in the page table refers to many addresses)

## Page Tables
* Page Tables and Translation Look Aside Buffer Explanation: [[operatingSystems/content/week3]]

## Memory Management Unit 
![[Pasted image 20230218124000.png]]
* Protects areas of memory from unauthorised access by causing an exception such as segmentation faults.
* Translates virtual addresses to physical addresses using page table look ups.