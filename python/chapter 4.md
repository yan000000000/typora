# list and dictionary

## list

### basic syntax

*a container in python that can store different data types*

```python
my_list = []
number = [1, 2, 3]
fruits = ["apple", "pear", "banana", "orange"]
mixed_list = [1, "apple", True, 3.14]
```

### calculate the length of list

```python
print(len(fruits))
# 4
```



### read from the list

```python
# Read from List
print(numbers[0])  # Output: 1
print(numbers[-1])  # Output: 5
print(numbers[1:4])  # Output: [2, 3, 4]
```



### insert list

```python
fruits.insert(1, "kiwi")
```

1 stands for the index you want to insert into



### delete list

```python
fruits.remove("banana")

# equivalent to

del fruits[3]
```



### shallow copy

```python
original_list = [1, 2, 3, 4]
shallow_copy_list = original_list
original_list[0] = 10
print(original_list)
print(shallow_copy_list)

# [10, 2, 3, 4]
# [10, 2, 3, 4]
```

shallow copy copy the address of the data



### deep copy

```python
original_list = [1, 2, 3, 4]
deep_copy_list = original_list.copy()
original_list[0] = 10
print(original_list)
print(deep_copy_list)

# [10, 2, 3, 4]
# [1, 2, 3, 4]
```

copy the template of the original list



## dictionary

### basic syntax

```python
my_dict = {}
classmate_dic = {"name" : "junliang H", "age" : 18, "city" : "DG"}
print(classmate_dic["city"])
# DG
```



### update dictionary

```python
classmate_dic["major"] = "artificial intelligence"
print(classmate_dic)
# {"name": "junliang H", "age": 18, "city": "DG", "major": "artificial intelligence"}
```



### delete element

```python
del person["age"]
print(classmate_dic)
```



### iterate through dict

```python
classmate_dic = {"name" : "junliang H", "age" : 18, "city" : "DG"}
# print out the key and value
print(classmate_dic.items())
# print out only the value
print(classmate_dic.values())
# print out only the key
for key in classmate_dic:
    print(key, end=" ")
    
# 2 ways to print out them together
for key, value in classmate_dic.items():
    print(key, value)
for key, value in zip(classmate_dic, classmate_dic.values()):
  	print(key, value)
```

