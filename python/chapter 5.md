# functions

## define and calling functions

### basic syntax

```python
def add_number(a, b):
  	result = a + b
    return result
```

`def` stands for define

`add_number` stands for the name of the function

`(a, b)` stands for the parameter, which is the variable you need in the function <font color='OrangeRed'>can be empty</font>

`return` stands for the value you want to return back to the main function <font color='OrangeRed'>not every function need a return statement</font>

> be careful the colon :



### function scope

#### global

```python
def modify():
    global global_variable
		print(global_variable)
    global_variable = 20
    
    
global_variable = 10
modify()
print(global_variable)
# 10
# 20
```

`global` used to get the outer value



#### local

```python
global_variable = 10


def modify():
  	local_variable = 1
    global_variable = 20
    print(global_variable)
    
    
modify()
print(global_variable)
# print(local_variable) # uncomment this will result in an error
# 20
# 10
```



### infinite parameter

```python
def addition(*args)
		total = 0
  	for value in args:
      	total += value
    return total
```

`args` stands for arguments, it stored the parameter in a tuple named args

> in python, *before a parameter, means the function can accept a variable number of positional arguments.
>
> > args is just convention



### set

```python
alist = [1, 2, 3, 4, 5, 4, "you", "i", "you"]
aset = set(alist)
print(aset)
print(list(aset))
print(type(set))

# it remove the duplicate value
# {1, 2, 3, 4, 5, 'i', 'you'}
# [1, 2, 3, 4, 5, 'i', 'you']
# <class 'type'>
```

