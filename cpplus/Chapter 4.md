# Loops

## while loop

*repeat until the condition turn false*



>   be careful <font color='OrangeRed'>"infinite while loop"</font>, forget to change the key

```c++
while(true)
{
	...
}
```



*   ##### common error

```c++
i = 5;
while (i > 0) ;
{
  cout << i << " ";
  i--;
}
```

in this case, note the ";" after the condition 

the program will not terminate, and iterate checking if i > 0



```c++
i = 5;
while(i > 0)
{
  	i--;
  	int j = 5;
  	j *= 2;  
}
cout << j ;
```

in this case, it initialize the variable j in the loop, so error occur because variable j is not found.



## for loop

*fairly common used to operate num*

```c++
for(int i = 0; i < 10; i++)
{
  	...
}
```

OR

```c++
vector<int> num = {1,2,3,4,5};

for(int i : num)		//let i = num[i] respectively and iterate num.size() time
{										//not neccessary to be a vector
  	cout << i << endl;
}
```

<font color='LimeGreen'>practical way to use</font>



## other

### do while

*perform the body first before loop test*



~~~c++
do
{
  ...
}while(//condition)
~~~

<font color='LimeGreen'>not really common</font>



### sentinel value

*a value serve as a signal for termination*



```c++
while(...)
{
  cin >> salary;
  if(salary != -1)		//in this case, -1 is the sentinel value
  {
    sum = sum + salary;
    count++;
  }
}
```



*   ##### use letter to work as sentinel value



```c++
cout << "Enter values, Q to quit: ";
bool done = false;
while(!done)
{
  cin >> value;
  if(cin.fail())
  {
    done = true;
  }else
  {
    ...//process value
  }
}
```

in this case, we use bool type as the condition of while



### cin.fail() to check input



```c++
do
{
  cout<"Enter a number >= 0: ";
  cin >> value;
  
  if(cin.fail())
  {
    cin.clear();	//clear the failed state
    string item;	//read and discard the item
    cin >> item;	//set to invalid input, attempt to read input from buffer(a temporary memory storage)
    value = -1;
  }
}
while(value < -1;)
```

in this case, we use a number <font color='OrangeRed'>-1</font> to work as the sentinel value

we check if the input data type is legal, if not input it again



~~~c++
while(true)
{
  	cin >> value;
  	if(cin.fail())
    {
      break;
    }
  	...//process value
}
~~~

difficult to use cin.clear() afterward



### finding match



```c++
int spaces = 0;
for(int i = 0; i < str.length(); i++)
{
  string ch = str.substr(i,1)
    if(ch == " ")
    {
      spaces++;
    }
}
```

in this case, the code count the number of space



### random number



>   necessary to include <font color='OrangeRed'><cstlib></font> header and <ctime> header if you want to set the srand(time())
