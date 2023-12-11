# Fundamental Data Types

## variable

 *a storage location in a computer program*



### integer

*a whole number without fractional part*



* integer can be negative, zero is an integer

* 1e6 or 1E6 = 1 * 10^6 or 1000000 --> <font color='OrangeRed'>double</font>

* no comma in numbers, eg 100,000

  

### <u>variable name</u>

* <font color='OrangeRed'>case sensitive</font>

* can't start with <font color='OrangeRed'>number</font>

* can't contain <font color='OrangeRed'>space</font>

* can't use reserved word

* can't use <font color='OrangeRed'>'.' '/' $ '%'</font>

  

### <u>constant</u>

*its value never change,often use capital letter to distinguish*



```c++
const double NAME
```





#### <u>comment</u>

  *to let computer ignore some words to make it easier to read*



   ```
   // for single line
   /* */ for multiple line
   ```



### magic number

   *a numeric constant operator in the code without explanation*



```c++
int num, bottle;
num = bottle * 2;  //in this case, 2 is the magic number
```



### number type

| Type           |                        Typical Range                         | Typical Size |
| -------------- | :----------------------------------------------------------: | ------------ |
| int            |       -2,147,483,648...2,147,483,648(about 2 billion)        | 4 bytes      |
| unsigned       |                      0...4,294,967,295                       | 4 bytes      |
| short          |                       -32,768...32,767                       | 2 bytes      |
| unsigned short |                          0...65,535                          | 2 bytes      |
| long long      |    -9,223,372,036,854,775,808...9,223,372,036,854,775,807    | 8 bytes      |
| long           |   depending on the compiler, the same as int or long long    | 4 or 8 bytes |
| double         | the double precision floating-point type, with a range of about 15 significant decimal digits | 8 bytes      |
| float          | the single precision floating-point type, with a range of about 7 significant decimal digits | 4 bytes      |

 

### <u>auto</u>

   *automatically give the variable type*

```c++
auto can = 6; //then it has int type
```



## operator

### <u>operator</u>

| the result of int and double | result |
| ---------------------------- | ------ |
| int operate with int         | int    |
| int operate with double      | double |
| double operate with double   | double |



### increment & decrement



```c++
counter ++ //adding itself by 1
counter -- //subtracting itself by 1
a += b //a = a + b
a -= b //a = a - b
```



### more operator

| expression(eg n = 1729) | value | comment                                      |
| ----------------------- | ----- | -------------------------------------------- |
| n % 10                  | 9     | n % 10 is the last digit of n                |
| n / 10                  | 172   | n without the last digit                     |
| n / 10.0                | 172.9 |                                              |
| n % 2                   | 1     | n % 2 is 0 if n is even, 1 or -1 if n is odd |



### math symbol



> need to add <font color='OrangeRed'><cmath></font> as header



| symbol   |                        description                        |
| -------- | :-------------------------------------------------------: |
| log(x)   | (<font color='OrangeRed'>natural log</font>) ln(x), x > 0 |
| log10(x) |                        decimal log                        |
| abs(x)   |                      absolute value                       |
| sin(x)   |  sine of x(<font color='OrangeRed'>x in radians</font>)   |
| pow(x,n) |                            x^n                            |
| sqrt(x)  |                          x^(1/2)                          |



```c++
pow(x,n) == x^n
 sqrt(x) == x^(1/2)
```



### round



```c++
double price = 2.9;
int dollar = price; //dollor = 2, might issue unsafe

//if you want to do a round up, add 0.5 and then convert
```



### round off error



> computer represent numbers in <font color='OrangeRed'>binary</font>, not in exactly equal

```c++
int main()
{
  	double price = 4.35;
  	int cents = 100 * price; // should be 435
  	cout << cents << endl; // prints 434!
}
```



### cast

   <font color='12b312'>used when compiler issue wrong when converting double to int </font>



```c++
int cents = static_cast<int>(100*price+0.5)
```



### input & output



>using fixed and setprecision function must include <font color='OrangeRed'><iomanip></font> header

```c++
std::cin>> a >> b ; // input 2 variable at the same time
std::cout << ""
  
//formatted output
std::cout << fixed << setprecision(2); //round to 2 significant digit
std::cout << std::setw(8) << ... // controlling the width of words/num to line up
```



| statement                                | output  | comment                                                      |
| ---------------------------------------- | ------- | ------------------------------------------------------------ |
| cout << 12.345678                        | 12.3456 | by default, a number is printed with <font color='OrangeRed'>6 significant digit</font> |
| cout << fixed << setprecision(2) << 12.3 | 12.30   | control the number of digit after the decimal point          |
| cout << ":" << setw(6) << 12             | :   12  | 4 space are printed before the number, for a total width of 6 character |
| cout << setw(2) << 1234                  | 1234    | if the width is not sufficient, it is ignored                |



### string

  * ##### rule

    ```c++
    string a = "hi,";
    string b = " steve!";
    string c = a + b; //c = "hi, steve!"
    
    string c = "hi," + " steve!"; // ERROR!!
    string c = "hi,"s + " steve!"; // a method in lately c++
    ```

  * ##### function

    * .length() <font color=#12b312>used to check how many letter of a string</font>

      ```c++
      std::string name = "steve";
      int n = name.length(); // n = 5
      ```

    * .substr(start, length) <font color=#12b312>return a string that's made from original variable</font>

      ```
      std::string name = "steve";
      std::string remainder = name.substr(2,2); //remainder = "ev"
      ```

      

