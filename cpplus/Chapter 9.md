# Classes

## class

*a gather of function*



[public] we usually put functions in public interface

[private] we usually put data member in private interface

##### example

```c++
class CashRegister
{
  public: //public interface
  	void clear();
  	void add_item(double price);
  
  	double get_total() const;
	  int get_count() const; // mark accessor as const
  
  private:
  	int item_count; // data members should always be private
  	double total_price;
};
```

>   be sure to include this semicolon



### member function

```c++
void Counter::count() //:: denote that it is a member function from a class
{
  	value++;
}
```



### mutators and accessor

*there are two category of member function*



*   mutators

*change the value of the data members*

```c++
void Counter::clear() // doing a clear action
```



*   accessor

*don't modify the value, ask for info*

```c++
return value
```



<font color=#12b312>we usually do constant behind accessors</font>

```c++
double get_value() const;
```



### calling member function from member function

```c++
void object::add_term(){}
void object::add_value()
{
  	add_term(); // when calling a member function in a member function don't need to write object name
}
```



### implicit parameter and explicit parameter



```c++
void CashRegister::add_item(double price) // in this case, price is a explicit parameter
{
  	item_count++; // in this case, item_count is a implicit function, which is defined in the class
  	total_price = total_price + price;
}

int CashRegister::get_count() const
{
  	return item_count;
}
```



### constructor

*initialize the data member of an object, automatically called when the object is created*



##### define a constructor

```c++
class CashRegister
{
 	public:
  	CashRegister(); // the name of constructor is identical to the name of its class
}

CashRegister::CashRegister() // no need to add void in front of the constructor
{
  item_count = 0;
}
```



##### types of constructor

*   default constructor

*the constructor with no argument*

```c++
CashRegister();
```



*   other constructor

```c++
CashRegister::CashRegister(double initial_balance) //same name with argument
```



>   constructors need to pay attention to data number that are pointers or numbers because they need to initialize,not for string(string itself is a class which have its own constructor)



##### COMMON ERROR

*   ==CAN'T== invoke the constructor(for an existed class)
*   ==CAN== alternatively assign a new class to the old one



### initializer list

*a way to initialize the member variable of a class and to set the initial values of class members directly within the constructor's declaration rather than using assignment statements inside the constructor's body*



##### example

```c++
class Myclass
{
  public:
  //constructor with an initializer list
  	Myclass(int x, double y) : intValue(x), doubleValue(y){
      //constructor body if needed
      // you can perform additional initialization here if necessary
    }
  private:
  	int intValue;
  	double doubleValue;
};
```

we have a class called `Myclass` with 2 private member variables `intValue` and `doubleValue`

*   the constructor of `Myclass` takes 2 parameter, `int x` and `double y` and uses an initializer list to initialize `intValue` and `doubleValue` with the values of `x` and `y`



##### other scenarios you can use initializer list

*   initialize from constructor parameter
*   initialize constant
*   initialize reference members
*   initialize non-default constructors
*   initialize performance optimization
*   complex initialization logic



### universal and uniform initialization syntax

*c++ 11 introduce a uniform syntax using braces and no equal sign*

| before                                     | after                                         |
| ------------------------------------------ | --------------------------------------------- |
| `double` price = 19.25;                    | `double` price { 19,25 };                     |
| `int` squares[] = {1, 4, 9, 16};           | `int` squares[] { 1, 4, 9, 16 };              |
| `BankAccount` lisas_account(499.95);       | `BankAccount` lisas_account { 499.95 };       |
| double* price_pointer = new double(19.15); | double* price_pointer = new double { 19.15 }; |







### separate compilation

*separate the content to header and source file*

<font color='LimeGreen'>here we take the example of CashRegister in the textbook</font>



*   header file
    *   definitions of classes
    *   definitions of constants
    *   declarations of nonmember functions



```c++
#ifndef CASHREGISTER_H //to have a double check if the header file is encountered the second time
#define CASHREGISTER_H // if it is, it will skip

class CashRegister
{
  public:
  /**
  	Constructor
  	*/
  	CashRegister();
  /**
  	clears the items count and the total
  	*/
  	void clear();
  
  /**
  	Adds an item to this cash register
  	@param price the price of the item
  	*/
  	void add_item(double price);
  
  /**
  	@return the total amount of the current sale
  	*/
  	double get_total() const;
  
  /**
  	@return the item count of the current sale
  	*/
  	int get_count() const;
  	
  private:
  	int item_count;
  	double total_price;
};

#endif //close if
```

>   you include this header file like this
>
>   >   #include "cashregister.h" //because this is not a standard header file
>
>   >a header file should include all headers that are necessary for defining the class



the function comment is in the header file because it is a part of the interface



*   source file
    *   definitions of member functions
    *   definitions of nonmember functions

```c++
#include "CashRegister.h"

CashRegister::CashRegister()
{
  	clear();
}

void CashRegister::clear()
{
  	item_count = 0;
  	total_price = 0;
}

void CashRegister::add_item(double price)
{
  	item_count++;
  	total_price = total_price + price;
}

double CashRegister::get_total() const
{
  	return total_price;
}

int CashRegister::get_count() const
{
  	return item_count;
}
```





##### to conclude

>   to build the complete program, you need to compile both the cpp source file and another file which use the header

```c++
g++ -o registerdemo registerdemo2.cpp cashregister.cpp
```



### pointers to object

##### the -> operator

*a symbol to abbreviate the action calling a member function*

```c++
CashRegister* register_pointer = new CashRegister;// define a pointer point to the class
// to invoke a member function on that object, you may call
(*register_pointer).add_item(1.95);//the parenthesis is necessary
*register_pointer.add_item(1.95); // ERROR
//you can use -> to abbreviate the calling action
register_pointer -> add_item(1.95);

```

>   this call means: when invoking the add_item member function, set the implicit parameter to *register_pointer and the explicit parameter to 1.95



```c++
//if you want to access a member function of a structure in a vector
vecPtr -> at(0).printData();
//or
(vecPtr)[0].printData();
```



##### this pointer

*a pointer point to the implicit parameter of a function*

```c++
class CashRegister
{
  public:
  	void add_item();
  private:
  	total_price = 0;
  	item_count = 0;
}

void CashRegister::add_item(double price)
{
  	this -> item_count++;
  	this -> total_price = this -> total_price + price; // the expression this -> item_count refers to the item_count data member of the implicit parameter
}
int main()
{
  CashRegister register1;
}
```

