# data

## about python

python is a latest coding language that stands for simple and easy to read. 

*   Its biggest quality is the indent rule. 
*   It is strict for indent which its result can be totally different is you get it wrong

## about data

### data assignment

```python
name = "John Doe"
age = 20
is_student = True

#print the variable
print("Name:" name)
print("Age:", age)
print("Is_student:", is_student)
```

>Name: John Doe
>
>Age: 20
>
>Is_student: True

no need to define the variable type before the variable name

<font color='#12b312'>print out a bool type will print out True or False</font>



#### end function

```python
#print the variable
print("Name:" name, end=",")
print("Age:", age, end=",")
print("Is_student:", is_student, end=".")
```

>Name:John Doe,Age:20,Is_student:True

in default, end="\n" (the new line character)

end can equal to " " "\n" "," "."



### data type

#### integer

pure number with no digit number



#### string

combination of character, no limitation of coding rule



#### float

numbers with decimal



#### boolean

True or False

```python
data_string = "Hello, world!"
data_integer = 42
data_float = 3.14
data_boolean = True

print("Data String Type:, type(data_string)")
print("Data Integer Type:, type(data_integer)")
print("Data Float Type:, type(data_float)")
print("Data Boolean Type:, type(data_boolean)")
```

>Data String Type: <class 'str'>
>
>Data Integer Type: <class 'int'>
>
>Data Float Type: <class 'float'>
>
>Data Boolean Type: <class 'boolean'>



```python
print("Print Type:", type(print))
```

>   Print Type: <'builtin_function_or_method'>



### comment

compiler just ignore the words in comment

```python
#this is a comment
```



### data type conversion

```python
#Int to Float
integer_num = 42
float_num = float(integer_num)
print(float_num) #print out 42.0

#Floar to Integer, int or round
float_num = 42.0
integer_num = int(float_num)
integer_number= round(float_num)
print(integer_num)
print(integer_number) #print out 42

#Integer to string
integer_num = 42
string_num = str(integer_num)
print(string_num) #print out 42

#String to Integer
str_value = "456"
integer_value = int(str_value)
print(integer_value)  # Output: 456

#String to Float
str_value = "3.14"
float_value = float(str_value)
print(type(float_value))  # Output: 3.14
```

<font color='OrangeRed'>you can't directly convert a string with a decimal into a integer</font>



#### a quick conversion

```python
print(type(1))
print(type(1 + 0.0))
```

>   <class 'int'>
>
>   <class 'float'>



### difference between int and round function

```python
float_num = 42.5
integer_num = int(float_num)
integer_number= round(float_num)
print(integer_num)
print(integer_number)
# 42 42

float_num = 42.5111
#42 43
```

>   Be careful the round up



### assignment operator

```python
x = 10 #define x with a initial value 10

x += 5 # equivalent to x = x + 5

x *= 2 # equivalent to x = x * 5

x ** 2 # equivalent to x to the power 2

x **= 2 # equivalent to x = x * x * x 
# x = 8
```



## input and output

### output

1.   **\+ operator**

```python
name = "alice"
age = 30
print("hello, " + name + "! You are " str(age) + " years old.")
```

<font color='OrangeRed'>counter example</font>

```python
print("hello, " + name + "! You are " + age + "years old.") #you can't put the age together with the string
```



2.   **f-string**

```python
name = "bob"
age = 25
print(f"Hello, {name}! You are {age} years old.")
```

you can include variables directly in the string using braces {}  <font color='#12b312'>common</font>



3.   .format{}

```python
name = "eve"
age = 35
message = "Hello, {}! You are {} years old.".format(name, age)
print(message)
```

use .format{} to insert variables into a string  



4.   `,` 

```python
name = "charlie"
age = 40
print("hell,", name + "! You are", age, "years old.")
```

python will automatically insert space between them



#### summary

`f-string` and `.format()` are considered more modern and flexible



### input

your can put the string you want to print out in the parenthesis

```python
#get the user's name as input
user_name = input("please enter your name: ")

#display a greeting message
print("Hello " + user_name + "!")
```

>   input function automatically convert the input to string



#### 	input int

```python
#get user's age as input (convert it into integer)
user_age = int(input("please enter your age: "))

#display your age
print("you are ", user_age, "years old!")

```



#### input float

```python
#get user's height
height = float(input("please enter your height"))

#display your height
print("Your height is ", height, "m")
```



### eval function

*short for evaluate a dynamically created python expression*

```python
#to be simple, it return a string no matter what you input after evaluating
user_age = eval(input("please enter your age: "))
height = eval(input("please enter your height(m): "))

print(type(user_age))
print(type(height))

#the output
# please enter your age: 24.5
# please enter your height(m): 111
# <class 'float'>
# <class 'int'>

x = 10
y = 20
expression = "x + y"
result = eval(expression)
print(result) # the result is 30
```

>   it is danger with untrusted input, should be used with caution