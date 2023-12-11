# Functions

## function design concept --- black box

*No need for knowing the process, just care for the function of the black box*



```c++
double cube_volume(double side_length)  //type of function, function name, type of parameter variable, name of parameter variable
{
	double volume = side_length * side_length * side_length
    return volume;	
}

double length = 3;
double result = cube_volume(length); // result = 27
```

in this case, we use the function <font color='OrangeRed'>cube_volume</font> to get the cube of the value of a variable



### comment for function

it is fairly important to make comment either for the main statement or the function

>/**
>	Compute the volume of a cube	//the main fun
>	@param side_length the side length of the cube	//what the parameter is
>	@return the volume	//what the function return
>*/



### common error



*   ##### modify parameter value

```c++
int plus_one(int cent)
{
  cent = cent + 1;
  return cent;
}
```

same variable name might make others confuse 



*   ##### missing return value



>   when return is processed, the function exit immediately
```c++
int plus_one (int cent)
{
  if(cent == 0)
  {
    return 0;
  }else
  {
    return cent++;
  }	//may lead to error
}
```

every branch has to have a return



### function under main

*the compiler may not notice your function if you write totally under the main function, you need a prototype*




>   the semicolon is a big difference between a prototype and the body of the function
```c++
double plus_one (double cent);
```

you need a declaration above the main function, or so called prototype





### function without return --- void



>   no return at the end or write return with no value following

```c++
void print_plus_one (double cent)
{
   cout << cent++;
}
```



### function tips

*   rather keep the code in <font color='OrangeRed'>separate function</font> than all in one function

*   use a simple number to test logic in bigger program



### variable scope & global variable



*   ##### scope

*an area that variable can function*



*   ##### global variable

*have a scope in whole program*



it is written out of the functions and main function

<font color='OrangeRed'>not recommend</font>



### reference parameter

*a dynamic link between the parameter and variable, giving the memory address to the argument*



```c++
void plus_one(int cent)
{
	cent++;
}
int num = 10;
cout << plus_one(num); //10
```

in this case, I <font color='OrangeRed'>can't</font> change the value of num

if I want to make change of it, I need to assign the result of the function back to it



>   with reference parameter, we can make change directly on the value of a variable.

```c++
void plus_one (int& cent)
{
  	cent++;
}
int num = 10;
cout << plus_one(num); // 11
```

<font color='OrangeRed'>all you have to do is put a $; mark after the data type of the parameter</font>



### reminder

*   only variables are allowed for reference parameter
*   no form of calculation e.g. a + 15 is permitted for reference parameter
*   you can return value in a function with reference parameter



### other form of parameter



*   ##### constant parameter

   *a constant version, can't be modified*

*   ##### value parameter

   *make a copy of the argument passed to the function without modifying the original argument*



### recursive function

*a function call itself*



```c++
void print_triangle(int side_length)
{
  	if（side_length < 1) //key condition
    {
      return;
    }else
    {
      print_triangle(side_length - 1);
    }
  	for(int i = 0; i < side_length; i++)
    {
      cout << "[]";
    }
  	cout << endl;
}
```

in this case, side_length < 1 act like the sentinel value, it control when the function return

>   try to debug it and you will find miracle, run over all the way to the bottom and using return to go upward



*   ##### requirement for recursive function

    *   must simplify the task
    *   must be special case to handle the simplest case directly
