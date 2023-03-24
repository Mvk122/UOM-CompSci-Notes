# Memory Reliability

## Soft Errors
* There are lots of bits in tiny cells, they can be changed by external forces like cosmic radiation.
* Rare but with lots of memory, there can be lost bits every hour.
* Error Correction Codes can be used to detect and correct most bit errors.

## Parity
* A cheap check to detect the presence of a single bit error.
* Can be done by having a parity bit that changes to ensure the number of bits in a set byte/word is odd/even. 
* If the number of bits is not odd/even as agreed, then one of the bits has been changed erroneously. With only 1 parity bit, we can't know which bit was changed however.

## Error Correction Codes
* Used to find single bit errors and correct them, there are multiple methods:

### Triple Modular Redundancy
* Write each value 3 times and take the most common one. 
* There is a lot of wasted memory and can be slow.

### Hamming Codes
![[Pasted image 20230324045746.png]]
![[Pasted image 20230324045808.png]]
* Far less overhead and is used in memory protection.
* As shown in the diagram where D are bits and C are parity bits, when grouping bits together for parity, it is easy to tell which bit has flipped. Eg if the parity in C1, D2 and C2 is wrong, it is only possible that D2 is erroneous and needs to be flipped.
* Hence $2^n-1$ bits can be protected with n parity bits.