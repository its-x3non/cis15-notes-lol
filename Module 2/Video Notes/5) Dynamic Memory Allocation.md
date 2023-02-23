#Module2 #VideoNotes 
# 9.8 - Dynamic Memory Allocation
## Dynamic Memory Allocation
### (1 of 2)
- Can allocate storage for a variable while program is running
- computer returns address of newly allocated variable
- Uses `new` operator to allocate memory:
```c++
double *dptr = nullptr;
dptr = new double;
```
- `new` returns address of memory location

### (2 of 2)
- Can also use `new` to allocate array:
```c++
const int SIZE = 25;
arrayPtr = new double[SIZE];
```
- Can then use `[ ]` or pointer arithmetic to access array:
```c++
for(i = 0; i < SIZE; i++)
	*arrayPtr[i] = i * i;
```
	or
```c++
for(i = 0; i < SIZE; i++)
	*(arrayPtr + i) = i * i;
```
- Program will terminate if not enough memory available to allocate

## Releasing Dynamic Memory
- Use `delete` to free dynamic memory:
`delete fptr;`
- Use `[ ]` to free dynamic array:
`delete [] arrayptr;`
- Only use `delete` with dynamic memory

# 9.9 - Returning Pointers from Functions
## Returning Pointers from Functions
- Pointer can be the return type of a function:
`int* newNum();`
- The function must not return a pointer to a local variable in the function.
- A function should only return a pointer:
	- To data that was passed to the function as an argument
	- To dynamically allocated memory.