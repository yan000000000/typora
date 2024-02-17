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
substring = original_string[0:5]
print(substring)
# This
substring = original_string[0:-1]
print(substring)
# This is a test strin
substring = original_string[5:0:-1]
print(substring)
# i sih
substring = original_string[::-1]
print(substring)
#gnirts tset a si siht
#print out all the word in reversed order
```

*   `first colon` -> stands for start

if you omit the **start** value, it default to 0, the beginning of the sequence

*   `second colon` -> stands for stop

if you omit the **stop** value, it default to the length of the sequence

*   `third colon` -> stands for step

if you omit the **step** value, it default to 1, <font color='OrangeRed'>it can be negative</font>

### index find & replace

```python
text = "i will go to france in summer"
index = text.find("france")
print(index)
# 13

text = "i will go to france in summer"
print(text)
#replace france to british
text = text.replace("france", "british")
print(text)
# i will go to france in summer
# i will go to british in summer
```

### judge whether the string contain some char

```python
text = "i will go to france in summer"
print(text)
print('france' in text)
text = text.replace("france", "british")
print(text)
print('france' in text)

# i will go to france in summer
# True
# i will go to british in summer
# False
```

### string + loops

```python
word = "python"
for index in word:
  print(index)
  
# p
# y
# t
# h
# o
```

### zip

*used to tie 2 sequence element together*

#### basic syntax

```python
list1 = [1, 2, 3]
list2 = ['a', 'b', 'c']

zipped = zip(list1, list2)

for item in zipped:
    print(item)
# (1, 'a')
# (2, 'b')
# (3, 'c')
```

>   in this case, zipped is in zip type, which is complicated, you can use list(zipped) turn it into a list to use



#### additional use

```python
word = "python"
for char, index in zip(word, range(len(word))):
  print(index, end=" ")
  print(char)
0 'p'
1 'y'
2 't'
3 'h'
4 'o'
5 'n'
```



#### noting

```python
list1 = [1, 2, 3]
list2 = ['a', 'b']

zipped = zip(list1, list2)

for item in zipped:
    print(item)

# (1, 'a')
# (2, 'b')
```

>   if input variable is in different length, zip will stop in the length of the shortest 



#### unzip

you can use the * to unzip a zipped iterable

```python
zipped = [(1, 'a'), (2, 'b'), (3, 'c')]
list1, list2 = zip(*zipped)

```

>   in this case, list1 and list2 and tuple



### reversed

#### reverse a string

```python
# Reversing a string using a for loop
word = "python"
reversed_string = ""
for char in reversed(word):
    reversed_string += char
print("Reversed String:", reversed_string)

# Reversed String: nohtyp
```

#### reverse a container

```python
list1 = [1, 2, 3]
reversed_list1 = list(reversed(list1))
for item in reversed_list1:
  print(item, end=" ")
  #1 2 3
```



## break, continue and pass

### break

```python
list1 = [1, 2, 3]
for item in list1:
    if item == 2:
        print("there is a break")
        break
    print(item)
# 1
# there is a break
```



### continue

```python
list1 = [1, 2, 3]
for item in list1:
    if item == 2:
        print("there is a break")
        continue
    print(item)
# 1
# there is a break
# 3
```



### pass

```python
list1 = [1, 2, 3]
for item in list1:
    if item == 2:
        print("there is a break")
        pass
    print(item)
# 1
# there is a break
```



### difference between continue and pass

```python
# Example using pass
for i in range(4):
    if i == 2:
        print("Using pass when i is 2")
        pass
    print("Processing i =", i)
    
# processing i = 0
# processing i = 1
# using pass when i is 2
# processing i = 2
# processing i = 3
```

```python
# Example using pass
for i in range(4):
    if i == 2:
        print("Using pass when i is 2")
        continue
    print("Processing i =", i)
    
# processing i = 0
# processing i = 1
# using continue when i is 2
# processing i = 2
# processing i = 3
```

*   **continue** skip the rest of the code in the loop
*   **pass** does nothing and allow the code to continue
