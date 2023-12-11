# Inheritance

## inheritance

### inheritance hierarchies

*relationship between general class (`base class`) and specialized class (`derived class`)*



*   share <font color='OrangeRed'>"is a"</font> relationship 

*   derived class inherit from the base class

##### example

class Car inherit from class Vehicle. Every car is a vehicle



### basic structure

```c++
class ChoiceQuestion : public Question // : symbol denotes inheritance 
{																			 // public is necessary for basicly all inheritance
  public:
  	//new and changed member function
  private:
  	//addtional data members
}; //important ;
```

*   class `ChoiceQuestion` inherit from class `Question`

`ChoiceQestion` -> derived class

`Question` -> based class



>   remember the public reserved word and ; after the whole curly bracket

*   member function in derived class can't access private interface in the based class



### COMMON ERROR

#### private inheritance

*must type the public reserved word following the colon*



*   if no `public`, the derived class will inherit privately, that is, only the member functions of `ChoiceQuestion` get to call member functions of `Question`. Whenever another function invokes a `Question` member function on a `ChoiceQuestion` object, the compiler will flag this as an error



###### example

```c++
int main()
{
  ChoiceQuestion q;
  //...
  cout << q.check_answer(response); //ERROR check_answer is a function in the base class
}
```

### calling the base-class constructor

*when you construct a derived class object, you need to initialize the base class data member to access them*



you use an initializer list

```c++
ChoiceQuestion::ChoiceQuestion(string question_text)
  :Question(question_text) // if you omit the base-class constructor call, the default constructor is invoked
    // the base class constructor is called first
  {
}
```



### overriding member function

*override a function inherit from the base class if you are not satisfied with it*



```c++
// for example you have class BasedClass and a derived class DerivedClass

class BasedClass()
{
	public:
  void display();
    
  private:
  std::string text;
};


void BasedClass::display()
{
	std::cout << text; // in display function in the based class just print out one line at a time
}

//override the function display
void DerivedClass::display()
{
 	//you want to print out text but for multiple time
  //but the text is in the private interface
  
  display(); //ERROR you invoke the DerivedClass::display instead of BasedClass::display
  
  //in this case, you need to be specific which display you want to call
  BasedClass::display(); //OK
} 
```

*   if you want to extend the functionality of the base-class version, you need to use the `Base-class:function` notation

>   remember to specify which function you want to call



normally, to override a function needs the same function type, parameter and same const.



##### insurance - override

*   if the member function does not actually override a `virtual` function, the compiler generates an error
*   if you forget to declare the base class member function as `virtual`, the compiler also generates an error

```c++
class BasedClass{
  public:
  	BasedClass();
  	virtual void print()

}

class DerivedClass : public BasedClass{
  public:
  	DerivedClass() ;
  	virtual void print() override;
} 
```





## virtual functions and polymorphism

### slicing problem

when we assign or pass a derived class into a base class type or a base type collection, the extra member function of the derived class will be sliced away



```c++
class BasedClass{
  public:
  	BasedClass();
  	void print();

class DerivedClass : public BasedClass{
  public:
  	DerivedClass();
  	void print();
} 

int main()
{
  	BasedClass Based;
  	DerivedClass Derived;
  	Based = Derived; // the compiler realize that Derived is a special case of Based so it don't error
  	Based.print();  // this will only call the Base class's print function
}
```



##### slicing problem in function parameter

```c++
void ask(question q) //ERROR
{
  q.display();
  cout << "Your answer:";
  getline(cin,response);
  cout << q.check_answer(response) << endl;
}

```

in this case, if you call this function with a ChoiceQuestion(a derived class of class question ) object, then the parameter q is initialized with a copy of that object but being sliced away the derived part.



use a reference instead

```c++
void ask(const Question& q) //reference is really a pointer in disguise
```



### solution-- pointer to base and derived class

*if we define and assign pointer, we won't encounter slicing*

```c++
int main() 
{
  	BasedClass Based;
  	Base* baseptr = &Based; // no slicing here
  
  	baseptr ->print(); // this will call the derived class print function
}
```



### polymorphism

*literally, " of multiple shapes" a collection collects a mixture of similar kind of object*



```c++
Based* quiz[2];
quiz[0] = new Based;
quiz[1] = new Derived;
```



in the above case, the `quiz` array is a polymorphism, have some commonality but are not necessarily of the same type



### virtual function

*a identification to let the compiler choose the suitable member function for the different type in polymorphism*



from the above

```c++
quiz[i] -> print();
```

this statement always calls `Based::print()` because the type of `quiz[i]` is `Based*`



use `virtual`

>   the virtual reserved word must be used in base class. All functions with the same name and parameter variable types in derived classes are then automatically virtual. 
>
>   >   usually supply the virtual reserved word for the derived-class functions as well



```c++
class Based
  public:
    Based();
    virtual void print() const;
	private:
. . .
};
```

whenever a virtual function is called, the compiler determines the type of the implicit parameter in the particular call at run time

```c++
quiz[i] -> print();
```

always calls the function belonging to the actual type of the object to which `quiz[i]` points





