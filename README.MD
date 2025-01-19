# I like CCNA more than Network+.
Feels alot more appliciable and functional when its rooted in an acutal application. Not just all theory.  

Lets sub divide the network... aka subnetting!

## A network is something you subdivide into useful subnets. 

# Before the CCNA exam
- Write down these:
1. Power of 2
2. Masks
3. Mask Octets
4. Multiples of 8, 16, 32
5. Other charts
6. Address Class Key

| Range of first Octets | Class | number of Network Octets | number host Octets | Default Masks | 
|-----------------------|-------|---------------------|---------------|---------------|
| 1..126		|A	|1 		      |3	      | 255.0.0.0     |
| 128..191		|B	|2		      |2 	      | 255.255.0.0   |
| 192..223		|C	|3		      |1	      | 255.255.255.0 |
| 224..239		|D 	|NA		      |NA	      |NA	      |
| 240..255		|E 	|NA		      |NA	      |NA	      |

7. Multiples of 8, 16, 32

| Multiples of 16 	| 32* 	|
|-----------------------|-------|
| 0* 			| 128*	|
| 16			| 144	|
| 32*			| 160*	|
| 48			| 176	| 
| 64*			| 192*	|
| 80			| 208	| 
| 96* 			| 224*	|
| 112			| 240	| 

8. Nine DDN mask values and magic numbers

|Decimal Octet Value	|Magic Number	| Binary	| number of binary 1s	|
|-----------------------|---------------|---------------|-----------------------|
| 0			| 256		| 00000000	| 0			|
| 128			| 128		| 10000000	| 1			|
| 192			| 64		| 11000000	| 2			|
| 224			| 32		| 11100000	| 3			|
| 240			| 16		| 11110000	| 4			|
| 248			| 8		| 11111000	| 5			|
| 252			| 4 		| 11111100	| 6			|
| 254			| 2		| 11111110	| 7 			|
| 255			| 1		| 11111111	| 8			|


