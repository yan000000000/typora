# Pointers and Structure

## pointers

### pointer variable

*a variable point directly to the memory storage address*



```c++
double* account_pointer = &harrys_acount;
```

<font color='OrangeRed'>doulbe*</font> --> a pointer of double type

<font color='OrangeRed'>account_pointer</font> --> the name of the pointer

<font color='OrangeRed'>&harrys_account</font> --> the address of variable harrys_account

<font color='OrangeRed'>*account_pointer</font> --> the value of the address which the pointer point at

##### demonstrative example

```c++
int joint_account = 1000;
int* account_pointer = &joint_account;	//this line is the initialization of the pointer
//*account_pointer = 1000;

int balance;
balance = *account_pointer;	//balance = 1000

int bins_account = 500;
account_pointer = &bins_account; //assign the address of bins_account to account_pointer
//*account_pointer = 500;

*account_pointer = 700;	//bins_account = 700
```



### pointer syntax



assume the following 

```c++
int m = 10; //assumed to be at address 20300
int n = 20; //assumed to be at addresss 20304
in* p = &m;
```



| expression                | value                           | comment                                                      |
| ------------------------- | ------------------------------- | ------------------------------------------------------------ |
| p                         | 20300                           | the address of m                                             |
| *p                        | 10                              | the value stored at that address                             |
| &n                        | 20304                           | the address of n                                             |
| p = &n                    |                                 | set p to the address of n                                    |
| *p                        | 20                              | the value stored at the changed address                      |
| m = *p                    |                                 | store 20 into m                                              |
| m = p                     |                                 | **ERROR** m is an int value;p is an int* pointer. the types are not compatible |
| &10                       |                                 | **ERROR** you can only take the address of a pointer variable |
| &p                        | the address of p, perhaps 20308 | this is the location of a pointer variable, not the location of an integer |
| double x = 0;<br />p = &x |                                 | **ERROR** p has type int*, &x has type double*. These types are incompatible |
| double* p;                |                                 | **ERROR** if you want to initialize a pointer with no address, you should assigned it to nullptr. <font color='LimeGreen'>e.g. double* p = nullptr</font> |



### define separately

*define more than one pointer need to contain respective number of \**



```c++
double* a = &x, b = &y; //ERROR
double* a = &x, *b = &y; //correct
```



### array as pointer

*array actually is a sequence of pointer*



>   an array without bracket denote the address first element in array

```c++
double a[10] = {0, 1, 4, 9, 16, 25};
double *p = a; // which means a[0] = *a
//similarly we have a[n] = *(a + n)
```



| expression | value | comment                                                      |
| ---------- | ----- | ------------------------------------------------------------ |
| a          | 20300 | the starting address of the array, here assumed to be 20300  |
| *a         | 0     | the value stored at that address                             |
| a + 1      | 20308 | the address of the next double value in the array<br />a double type occupies 8 bytes |
| a + 3      | 20324 | the address of the element with index 3                      |
| *(a + 3)   | 9     | the value stored at address 20324                            |
| a[3]       | 9     | the same as *(a + 3)                                         |
| *a + 3     | 3     | the * only refer to a                                        |
| &a[3]      | 20324 | the address of the element with index 3, the same as a + 3   |



### cstring

*   in c programming language, strings are always represented as char array

```c++
const char* char_pointer = "Harry"; //point to 'H'
```

*   the c string contain '\0' character which work as a terminator, show where to end the string

| [0]  | [1]  | [2]  | [3]  | [4]  | [5]  |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 'H'  | 'a'  | 'r'  | 'r'  | 'y'  | '\0' |

*   by initializing the cstring with constant, you can't change the value 

    <font color='#6b9956'>if you don't want to change it, use char array</font>

*   contrast to the top, when printing out c string or assigning, you don't need to add the asterisk in the front or it will lead to compile error

```c++
cout << char_pointer;
cout << *char_pointer; //ERROR
```



### <u>converting between c and c++</u>

>   using \<cstdlib> header to use atoi function

<font color='LimeGreen'>in this case, atoi = ascII to int</font>



### <u>string --> int</u>

```c++
//cstring
char year[] = "2020";
int num = atoi(year);

//c++ string
string year = "2020"
int num = atoi(year.c_str())
```



### using [] in string

*to access a single letter in a string, you can use variable name[] with index*



```c++
string name = "steve";
cout << name[2]; //the result is e
```



### toupper and tolower

*change a letter to uppercase or lowercase*

>   defined in \<cctype> header



```c++
char A = 'a';
char B = toupper(A);
```



### functions in c string

>   adding <string.h>



in this table <font color='OrangeRed'>s</font> and <font color='OrangeRed'>t</font> are character arrays, <font color='OrangeRed'>n</font> is an integer

| function                                        | description                                                  |
| ----------------------------------------------- | ------------------------------------------------------------ |
| <font color='OrangeRed'>strlen(s)</font>        | return the length of <font color='Orangered'>s</font>        |
| <font color='OrangeRed'>strcpy(t, s)</font>     | copies the characters from <font color='Orangered'>s</font> into <font color='Orangered'>t</font> |
| <font color='OrangeRed'>strncpy(t, s, n)</font> | copies at most <font color='Orangered'>n</font> characters from <font color='Orangered'>s</font> into <font color='Orangered'>t</font> |
| <font color='OrangeRed'>strcat(t, s)</font>     | appends the characters from <font color='Orangered'>s</font> after the end of the characters in <font color='Orangered'>t</font> |
| <font color='OrangeRed'>strncat(t, s, n)</font> | appends at most <font color='Orangered'>n</font> characters from <font color='Orangered'>s</font> after the end of the characters in <font color='Orangered'>t</font> |
| <font color='OrangeRed'>strcmp(s, t)</font>     | returns 0 if <font color='Orangered'>s</font> and <font color='Orangered'>t</font> have the same contents, a negative integer if s comes before t in lexicographic order, a positive integer otherwise |



### dynamic memory allocation

*you may create a new value whenever you need them*



##### free store

*the memory to store the value*



>   new type return pointer type

```c++
double* account_pointer = new double;
double* account_array = new double[n];	//in this case, n in the array needn't be a constant
```



##### example

>   to use free store more advanced, you can assign variable in small array to bigger one, that's how vector works

```c++
int* var_ptr = new int; //the new operator yields a pointer to a memory block of the given type
//...
*var_ptr = 1000;
// ...
delete var_ptr; //delete the memory when you are done

int* array_ptr = new int[size]; //use this form to allocate an array of the given size(size needn't be a constant)

array_ptr[i] = 1000; //use the pointer as if it were an array

delete[] = array_ptr;
//remember to use delete[] when deallocating the array
//after you delete the memory block, you can no longer use it
```



##### common allocation error

| statement                                                    | error                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| int* p;<br />*p = 5;<br />delete p;                          | there is no call to new int                                  |
| int* p = new int;<br />*p = 5;<br />p = new int;             | the first allocated memory block was never deleted           |
| int* p = new int[10]<br />*p = 5;<br />delete p;             | the delete[] operator should have been used                  |
| int* p = new int [10];<br />int* q = p;<br />q[0] = 5;<br />delete p;<br />delete q; | the same memory block was deleted twice                      |
| int n = 4;<br />int* p = &n;<br />*p = 5;<br />delete p;     | you can only delete memory blocks that you obtained from calling new |



## structure

*a type to group different type of values together*



##### simple example

>   be careful of the semicolon behind the curly bracket

```c++
struct StreetAddress
{
	int house_number;
	string street_name;
};

StreetAddress home; // defining a variable named home
home.house_number = 234; //using the member function in the structure
//use a dot to access member function
```

<font color='OrangeRed'>StreetAdress</font> --> defining a new struct type named StreetAddress

<font color='OrangeRed'>house_number & street_name</font> --> defining the member function in the structure



### struct assignment and comparison

==CAN== assign structure to one another structure

```c++
destination = white house
```

==CAN NOT== compare 2 structure but the member separately

```c++
if(destination = white_house) ERROR
```



### function & structure

==CAN== set structure as parameter

```c++
int address (StreetAddress home)
```



==CAN== return a structure in a function

```c++
StreetAddress address(...)
```



### array & structure

*as well as vector*



*   **put struct into array**

```c++
StreetAddress delivery_route[route_length];
delivery[0].house_number = 123;
```

*   put array into structure

```c++
struct noon
{
  double values[12];
};

//to access
noon time;
time.values[2] = ...;
```



### nested struct

*you can put a structure into a structure itself*

```c++
struct person
{
  	string name;
  	StreetAddress work_address;
}
```



### pointer to structure



<font color=#12b312>common to allocate structure value dynamically</font>

```c++
StreetAddress* address_pointer = new streetAddress;
```



##### COMMON ERROR accessing data



```c++
*address_pointer.home_number = 1600; ERROR
*(address_pointer.home_number) = 1600; ERROR
(*address_pointer).home_number = 1600; right
address_pointer -> home_number = 1600; right
```

because in c++, the dot operator takes precedence over the * operator
