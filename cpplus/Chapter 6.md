# Arrays and Vector

## array

*a container contains a sequence of value*

>   the size of array must be a constant or be initialized when defined



### defining array

| example                                      | explanation                                                  |
| -------------------------------------------- | ------------------------------------------------------------ |
| int numbers[10];                             | an array of ten integers                                     |
| const int size = 10;<br />int numbers[size]; | it is a good idea to use a named constant for the size       |
| int size = 10;<br />int numbers[size];       | the size must be a constant. this array definition will not work with all compilers |
| int squares[5] = { 0, 1, 4, 9, 16};          | an array of 5 integers, with initial values                  |
| int squares[] = { 0, 1, 4, 9, 16};           | you can omit the array size if you supply initial values. the size is set to the number of initial values |
| int squares[5] = { 0, 1, 4};                 | if you supply fewer initial values than the size, the remaining values are set to 0. the array contains 0, 1, 4, 0, 0 |
| string names[3];                             | an array of three strings                                    |



##### a simple example

```c++
double values[5] = { 32, 54, 67.5, 29, 34.5};
values[i] = 0; //use bracket to access an element
							 //i < the size of array and i >= 0
```

<font color='OrangeRed'>double</font> --> element type

<font color='OrangeRed'>values</font> --> array name

<font color='OrangeRed'>[5]</font> --> size of array

>   the index of array start from 0



### bounds error

*the error which the index of array is not within the valid index*





```c++
int num[10] = {...};
int a = num[10]; //there's no variable of index 10 in the array
```
>   the compiler and program don't catch this error

to avoid this error and to make the array more flexible, usually we will define a partially filled array

<font color='LimeGreen'>e.g. we need an array filled with 10 values, we define it into 15</font>



### copying array

*to copy an array from one to another*



```c++
int value[5] = {...};
int num[5];
num = square; //ERROR

for(int i = 0; i < 5; i++)  //correct way to copy
{
  	num[i] = value[i];
}
```

>   you can't directly assign array from one to another



### insert to particular position

*move the value behind that position one index backward*



```c++
if(current_size < CAPACITY)
{
  	current_size++;
  	for(int i = current_size - 1; i > pos; i--)
    {
      	values[i] = values[i - 1];
    }
  values[pos] = new_element;
}
```

same with remove



### binary search

*search the target from the middle index*



```c++
bool found = false;
int low = 0;
int high = size - 1;
int pos = 0;
while(low <= high && !found)
{
  	pos = (low + high) / 2; //pos = midpoint of the array
  	if(values[pos] == searched_value)
    {
      found = true;
    }else if（value[pos] < searched_value)
    {
      low = pos + 1;	//look into the second half
    }else
    {
      high = pos - 1; //look into the first half
    }
}
```



### array parameter

*give the whole array as a parameter to a function*



>   array parameter is always a reference parameter, no & is needed (you will know when you learn pointer)

```c++
int plus_one(int value[], int size)
{
  	...
}

int main()
{
  	int size = 5;
  	int num[size] = { 1, 2, 3, 4, 5};
	  plus_one(num[], size);
  	return 0;
}
```

*   place an empty <font color='OrangeRed'>[]</font> behind the parameter name
*   when calling the function, supply it with the <font color='OrangeRed'>name</font> and the <font color='OrangeRed'>size</font> of the array



##### constant array parameter

*when you don't modify the array, use <font color='OrangeRed'>const</font> to ensure it*



```c++
int plus_one(const int value[], int size);
```



### 2 dimensional array

*an array filled with multiple arrays as element*



```c++
int count[countries][medal] = 
{
  { 0, 3, 3}
  { 1, 2, 1}  
  { 1, 1, 1}
}
```

<font color='OrangeRed'>count</font> --> the name of array

<font color='OrangeRed'>countries</font> --> the rows of the array

<font color='OrangeRed'>medal</font> --> the columns of the array

>you can't change the size of individual array



##### accessing element

*just like the point in the 2 dimensional coordinate system you need to use 2 value to define the position of a element*



```c++
value = counts[1][2]
```



## vector

*the container similar to array but its size can change*



### defining a vector



>   need to include <font color='OrangeRed'>\<vector></font> header 

```c++
vector<double> values(10);

vector<double> values(10,1) //short cut to initialize the vector,(a,b) a for element size and b for value

vector<double> values = { 1, 2, 3, 4, 5}; //no need to provide the size if you specify the initial values

values[i] = 0;
```

<font color='OrangeRed'>\<double></font> --> data type of vector

<font color='OrangeRed'>values</font> --> name of vector

<font color='OrangeRed'>(10)</font> --> the element size of vector



##### example of vector



| example                                                      | description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| vector\<double> values();                                    | **ERROR**: Does not define a vector, it declares a function returning a vector |
| vector\<int> numbers;<br />for(int i = 1; i < 10; i++)<br />{<br />    numbers.push_back(i);<br />} | define a vector with no value and add value one by one       |
| vector\<int> numbers(10);<br />for(int i = 1; i < 10; i++)<br />{<br />    numbers[i] = i + 1;<br />} | another way of defining a vector of ten integers and filling it with 1,2,3...10 |



### size member function

*return the size of a function*



```c++
vector<int> value = {...};
int num = value.size();
```



### growing and shrinking vector

*add or substract a element of the vector*



##### push_back()

*add a element at the end of the vector*

```c++
vector<int> value(4);
value.push_back(2);
```



##### pop_back()

*remove an element at the end of the vector*

```c++
vector<int> value();
value.pop_back();
```



### vector as a function argument



```c++
double sum(vector<double> values)
```

```c++
double sum(vector<double>$ values); //vector as a reference parameter
```

```c++
double sum(const vector<double>& values); //vector as a constant reference parameter
```



### copying for vector



>   simply you can assign from one to another

```c++
vector<int> squares = { 1, 2, 3, 4, 5};
vector<int> lucky_numbers;
lucky_numbers = squares;
```



### 2 dimensional vector



```c++
vector<vector<int>> counts	//unlike array, no constant for column is needed
{
  	for(int i = 0; i < countries; i++)
    {
				vector<int> rows(medal);	//need to initialize the element of the 2d vector before you push_back
          counts.push_back(row);	//push_back empty vector in 2d vector before push_back element into it
    }
}

vector<vector<int>> counts(5, vector<int>(5,1));	//short cut to initialize the 2d vector
```



##### finding numbers of rows and columns

```c++
vector<vector<int>> values(5,vector<int>(5,1));
int rows = values.size();
int columns = values[0].size();
```



##### accessing the value of a 2d vector

```c++
vector<vector<int>> values(5, vector<int>(5,1));
int num = values[1][1]; //similar to 2d array
```

