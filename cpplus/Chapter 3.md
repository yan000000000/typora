# Decisions

## if statement

### basic structure

```c++
if(//often use "!=" ">=" "<=" "==")   // no semicolon behind the argument
{
	
}else if()
{

}else
{

}
  
OR  //if only one statement
if()
  ...			//you can omit the curly bracket
else if()		// but it is recommended to put bracket anytime
...
```

 

### tab

*use tab to make the structure clear, in some programming language like python, tabs are strictly required*



```c++
int main()
{
  	if()
    {
      	...
    }else
    {
      	...
    }
  	return 0;
}
```



### conditional comparing



#### conditional operator



```c++
actual_floor = (floor > 13) ? (floor - 1) : floor
```

// in this case
// if the condition floor > 13 is <font color='OrangeRed'>true</font>, then <font color='OrangeRed'>actual_floor = floor - 1</font>
// if the condition floor > 13 is <font color='OrangeRed'>false</font>, then <font color='OrangeRed'>actual_floor = floor</font>

#### comparing num & string



| c++    | math notation | description           |
| ------ | ------------- | --------------------- |
| >      | >             | Greater than          |
| ">""=" | >=            | Greater than or equal |
| <      | <             | Less than             |
| "<""=" | <=            | Less than or equal    |
| "=""=" | ==            | Equal                 |
| "!""=" | !=            | Not equal             |



#### example

| expression            | value     | comment                                                 |
| --------------------- | --------- | ------------------------------------------------------- |
| 4 < 4                 | false     | the left part must strictly smaller than the right part |
| 1.0 / 3.0 == 0.333333 | false     | they are not exactly equal                              |
| "10" > 5              | **ERROR** | can't compare a string to a number                      |

> by default, 0 denote false & non-0 digit denote true



* compare floating point number

​	<font color='LimeGreen'>because of round off issue, many of them are not the same</font>



​		|x - y| < a            a = 1E-14

### lexicographic order of string

*used when comparing different string*

| rules                                                | example   |
| ---------------------------------------------------- | --------- |
| all uppercase come before lowercase                  | coL < col |
| space character come before all printable characters | c o < co  |
| numbers come before letter                           | 21 < le   |



###  switch



```c++
switch(digit)
{
	case 1:digit_name = "one"; break;  //switch(1) means to execute from case 1 until break appear
  case 2:digit_name = "two"; break;  //if you want to execute one line, break is neccessary
 	//etc
  default:digit_name = " "; break;   //default take action when case other than the above appear
}
```



### nested branch

*loop inside a loop*



```c++
for(int i = 0; i < 3; i++)
{
  	for(int j = 0; j < 3; j++)
    {
      ...
    }
}
```



### dangling else

*miss match of if & else, it is fixed in lately version of c++*



```c++
if()  //if(a)
{
  if()  //if(b)
  {
    
  }
}else{
  
}
```

<font color='OrangeRed'>in the older version of c++</font>, the compiler will match the nearest if & else together

in this case, what we want is match the if(a) with the else

but actually it will match the if(b) with else



### boolean variable and operator

*true & false*



* ##### boolean operators

| operator | description                                  |
| -------- | -------------------------------------------- |
| * / %    | multiplication division remainder            |
| \|\|     | boolean <font color='OrangeRed'>"or"</font>  |
| &&       | boolean <font color='OrangeRed'>"and"</font> |



* ##### boolean argument(<font color='OrangeRed'>common error</font>)

| expression                    | value                           | comment                                                      |
| ----------------------------- | ------------------------------- | ------------------------------------------------------------ |
| 0 < 200 < 100                 | true                            | ERROR: never write this argument<br />0 < 100 is true which will <font color='OrangeRed'>convert to 1</font><br />1 < 100 is true so the value is true |
| -10 && 10 > 0                 | true                            | ERROR: never write this argument<br />-10 is non zero, it is converted to <font color='OrangeRed'>true</font> |
| 0 < x && x < 100 \|\| x == -1 | (0 < x && x < 100) \|\| x == -1 | && operator has a higher precedence than the \|\| operator   |

> in boolean, true denote 1 & false denote 0



### de morgan's law



!(A && B) is the same as !A || !B

!(A || B) is the same as !A && !B



### input invalidation



use cin.failed() in if condition to check the type in input

explain more in ...
