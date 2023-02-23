#Module2 #VideoNotes
# 9.3 - The Relationship between Arrays and Pointers 
## The Relationship between Arrays and Pointers 
### (1 of 2)
- Array name is starting address of array
![[Pointers and Arrays - The Relationship between Arrays and Pointers 1.png]]
```c++
// This program shows an array name being dereferenced with the *
// operator.

int main()
{
	short numbers[] = {10,20,30,40,50};
	cout << "The first element of the array is ";
	cout << numbers << endl; // referenced
	cout << *numbers << endl; // dereferenced
}
```
### (2 of 2)
- Array name can be used as a pointer constant:
```c++
int vals[] = {4,7,11};
cout << *vals; // displays 4
```
- Pointer can be used as an array name:
```c++
int *valptr = vals;
cout << valptr[1]; // displays 7
```

```c++
int main()
{
	int numbers[] = {10,20,30,40,50};
	int *numPtr = numbers;  // still outputs array even though no
							// array parameter
	
	cout << "The first element of the array is ";
	cout << *numbers << endl; // dereferenced

	cout << numPtr[0] << endl;
	cout << numPtr[1] << endl;
	cout << numPtr[2] << endl;
	cout << numPtr[3] << endl;
	cout << numPtr[4] << endl;
}
```

## Pointers in Expressions
Given:
```c++
int vals[] = {4,7,11};
valptr = vals;
```
What is `valptr + 1`? It means (address in `valptr`) + (1 * size of an int)
```c++
cout << *valptr + 1; // displays 7
cout << *valptr + 2; // displays 7
```
`cout << *valptr + 1; // displays 7`
`cout << *valptr + 2; // displays 11`
Must use `( )` as shown in the expressions.
```c++
int main()
{
	int numbers[] = {10,20,30,40,50};
	int *numPtr = numbers; 
	
	cout << numPtr + 1 << " numbers " << *numPtr[1] << endl;
	cout << numPtr + 1 << " numbers " << *(numPtr + 1) << endl;
	// These two do the same thing
}
```

## Array Access
### (1 of 2)
- Array elements can be accessed in many ways:
| Array Access Method                       | Example             |
| ----------------------------------------- | ------------------- |
| Array name and [ ]                         | vals[2] = 17;       |
| Pointer to array and []                   | valptr[2] = 17;     |
| Array name and subscript arithmetic       | \*(vals + 2) = 17   |
| Pointer to array and subscript arithmetic | \*(valptr + 2) = 17 |
### (2 of 2)
- Conversion: `vals[i]` is equivalent to `*(vals + i)`
- No bounds checking performed on array access, whether using array name or pointer
```C++
int main()
{
	int numbers[] = {10,20,30,40,50};
	int *numPtr = numbers;  
	
	cout << numPtr + 5 << " contains " << *(numPtr + 5) << endl;
	cout << numPtr + 6 << " contains " << *(numPtr + 6) << endl;
}
```

## Pointer Arithmetic
- Operations on Pointer Variables:
| Operation                  | Example                               |
| -------------------------- | ------------------------------------- |
|                            | int vals[]={4,7,11};                  |
|                            | int \*valptr = vals;                  |
| ++, --                     | valptr++; // points at 7              |
|                            | valptr--; // now points at 4          |
| +, - (pointer and `int`)   | cout << \*(valptr + 2); // 11         |
| +=, -= (pointer and `int`) | valptr = vals; // points at 4         |
|                            | valptr +=2; // points at 11           |
| - (pointer from pointer)   | cout << valptr-val;                   |
|                            | //difference between (number of ints) |
|                            | //between valptr and val              |

# 9.5 - Initializing Pointers
- Can initialized at definition time:
```c++
int num, *numptr = &num;
int val[3], *valptr = val;
```
- Cannot mix data types:
```c++
double cost;
int *ptr = &cost; // wont work
```
- Can test for an invalid address for `ptr` with: `if (!ptr) ...`