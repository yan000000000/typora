# string

## string operation

### string combine

```python
str1 = "Hello"
str2 = "World"
result_concatenate = str1 + "." + str2
print("String Concatenation:", result_concatenate)
# Hello.world
```



### string replication

```python
# String replication
original_string = "Python"
copied_string = (original_string+" ") * 3
print("String Replication:", copied_string)

# String Replication: Python Python Python
```



### del

*delete function*

```python
number = 3
del number
print(number)
# NameError: name 'number' is not defined
```



### len

a function getting the length of a string

```python
sentence = "do you know how to go to the library?"
number = len(sentence)
print(number)
# 37
```



### string slicing

```python
original_string = "This is a test string"
substring = original_string[-1]
print(substring)
# g
```

