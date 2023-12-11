# Streams

### file stream

>   must use \<fstream> header



### category

*   `ifstream` --> named for input fstream
*   `ofstream` --> named for output fstream
*   `fstream` --> named for both input & output fstream



### opening stream

##### example

```c++
ifstream in_file //define a fstream type 
in_file.open("input.dat"); //open the file
```

<font color='LimeGreen'>in window system if the name contain backslash "\\" use "\\\\" to denote "\\" cause "\\" represent "escape char"</font>



##### older version

```c++
filename.c_str();
```

in older version, we need to change variable in c++ string into c string



##### failed state

*if it is not able to read from the stream it will set stream variable into failed state*

```c++
if(in_file.fail()) //.fail() function used to check the state of input
 
```



##### recover from fail state

```c++
if(in_file.fail())
{
	cin.clear; //clear used to clean the fail state
	cin.ignore(std::numeric_limits<std::streamsize>::max(),'\n'); //ignore used to clear the input buffer
	//if you write cin.ignore(), it will only ignore one character
  //writing the words in the parenthesis will ignore all of them
}
```

to further explain(<font color='LimeGreen'>this part is unnecessary for beginer</font>) 

`std::numeric_limitss\<std::streamsize>::max()` is an expression that return the maximum representable value of the `std::streamsize` type

##### close

>   remember to close the file once you finish operate it

```c++
in_file.close()
```



### read & write from a file



##### same with cin

```c++
int num1, num2;
ifstream in_file;
in_file.open("input.dat");
in_file >> num1 >> num2;
```



##### .fail() function to check for invalid input

```c++
//reading from a file
ifstream in_file;
in_file.open("input.dat");
in_file >> name >> value;

//writting to a file
ofstream out_file;
out_file.open("c:\\output.txt");
out_file << name << " " << value << endl;
```



### get

*a function to read one character at a time*



*   get function return "not failed condition"

*   read <font color='OrangeRed'>white space character</font>

<font color='OrangeRed'>white space character</font> --> "space" "tab" "newline"



### unget

*a function to put the character back*



>   can only unget the last character

```c++
char ch;
in_file.get(ch);
if(isdigit(ch))
{
  	in_file.unget();
  	int n;
  	in_file >> n;
}
```



### cctype



>   must include `<cctype>` header

| function | accepted characters                                          |
| -------- | ------------------------------------------------------------ |
| isdigit  | 0 - 9                                                        |
| isalpha  | a - z, A - Z                                                 |
| islower  | a - z                                                        |
| isupper  | A - Z                                                        |
| isalnum  | a - z, A - Z, 0 - 9                                          |
| isspace  | White space(space, tab, newline, carriage return(\r), form feed(\f), vertical tab(\v)) |

<font color='OrangeRed'>carriage return </font>--> move part of sentence to the beginning of the line which will overwrite some words

<font color='OrangeRed'>form feed</font> --> used to advance to the top of the next page

<font color='OrangeRed'>vertical tab</font> --> used to move to the next vertical tabulation



### getline

*get a line of input*



*   return "not failed"



```c++
getline(cin, note);
```

*   first argument require a stream like `cin`, `ifstream`
*   second argument write the variable you want to store in



### COMMON ERROR -mixing >> & getline



| symbol    | function                                                  |
| --------- | --------------------------------------------------------- |
| `getline` | read the whole line include new line \n                   |
| >>        | read only the necessary, not include the new line char \n |

```c++
//pretend we have a file with the underneath line
"hello" //for the computer, it is hello\n
  
//in cstring, it is like hello\n
ifstream in_file;
in_file.open("...")
getline(in_file, prompt) //read from h --> \n
in_file >> prompt	//read from h --> o, so the next variable to be read is \n which will cause error
```



##### solution

```c++
string remainder;
getline(in_file, remainder);
```



### stream failure check



*   `infile.fail()`

*act as a bool type in condition*

```c++
if(in_file.fail())
```




*   `infile` itself

*can be returned in condition*

```c++
if(in_file)
```




*   `cin` >> value 

*can return Boolean type*

```c++
while(cin >> value)
```



*   in_file >> name >>type 

*can return Boolean type*

```c++
while(in_file >> name >> type)
```



*   `getline` & get

```c++
getline(in_file, line);
in_file.get(ch);

//you can put it into while or if statement
```



### writing text output



##### put

*put a character into stream*



```c++
out_file.put(ch) // only char type are allowed to put into the bracket
```



##### setfill

*to pad numbers with leading 0*



```c++
out_file << std::setfill('') << std::setw(2) << hours << ":"<<
  std::setw(2) << minutes << std::setfill(''); // std::setfill('') --> this is for reset the setfill
```

In this case, setfill is used for time, it print 09:01. <font color='LimeGreen'>usually come together with setw</font>



##### left and right alignment

*to make it come close to left or right*



```c++
out_file << left << setw(10) << word << right << setw(10) << number;
//fine
//        12
```





##### other functions

>   need to add \<iomanip> header



| manipulator  | function                                                     | example                                                      | output                   |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------ |
| setw         | set the field width of the next item only                    | out_file << setw(6) << 123 << endl<br /><< 123 << endl<br /><<setw(6) << 123456 | 123<br />123<br />123456 |
| setfill      | set the fill character for padding a field<br />(the default character is a space) | out_file << setfill('0') << setw(6) << 123                   | 000123                   |
| left         | select left alignment                                        | out_file << left << setw(6) << 123                           | 123                      |
| right        | select right alignment                                       | out_file << right << setw(6) << 234                          | 234                      |
| fixed        | select fixed format for floating-point numbers<br />defaultly when we use fixed, it set the precision to 6 digit after the decimal point | double x = 123.4567<br />out_file << x << endl << fixed << x; | 123.457<br />123.456700  |
| setprecision | set the number of significant digits for the default floating-point format, the number of digits after the decimal point for fixed format | double x = 123.4567;<br />out_file << setprecision(2) << x;  | 123.46                   |
| scientific   | select scientific floating-point format, with one digit before the decimal point and an exponent | out_file << scientific << setprecision(3) << 123.4567        | 1.235e+02                |
| defaultfloat | (since c++ 11) switch back to the default floating-point format | double x = 123.4567;<br />out_file << fixed << x << endl<br /><< defaultfloat << x | 123.456700<br />123.457  |



### utf-8 & unicode



*   utf-8 is a modern data storage method. it store the most common word with least byte and rare word with longer, <font color='LimeGreen'>widely use on Internet & data tansmitment</font>

*   unicode mean giving every symbol and language character a data symbol



### istringstream & ostringstream

>   include sstream

*read and write numbers from and to string*



```c++
istringstream strm;
strm.str("January 24, 1973");

string month;
int day;
string comma;
int year;
strm >> month >> day >> comma >> year;
```

in this way, we can get integer seperately



### to_string

*change integer into string*



```c++
to_string(day)
```



### command line argument

*define additional method to execute command*

```c++
// e.g. you input
// prog -v input.dat

```

<font color='OrangeRed'>-v input.dat</font> --> command line argument

*   usually the argument start with - work as option
*   start with string work as filename



##### how to use it



```c++
int main(int argc, char* argv[])
```

argc --> argument count <font color='LimeGreen'>argc at least one</font>

argv --> argument value <font color='LimeGreen'>argv[0] is always the program name</font>



##### example

*here is an example of using command line argument to encrypt a file*



```c++
void encrypt_file(ifstream & in, ofstream& out, int k)
{
  	char ch;
  	while(in.get(ch))
    {
      	out.put(ch + k);
    }
}

int main(int argc, char* argv[])
{
  	int key = 3;
  	int file_count = 0; // the number of files specified
  	ifstream in_file;
  	ofstream out_file;
  
  	for(int i = 1; i < argc; i++) // process all command line arguments
    {
      	string arg = argv[i]; // the currently processed argument
      	if(arg == "-d") //the decryption option
        {
          	key = -3;
        }else // it is a file name
        {
          	file_count++
              if(file_count == 1) // the first file name
              {
                in_file.open(arg);
                if(in_file.fail()) // exit the program if opening failed
                {
                  cout << "ERROR opening input file" << arg << endl;
                  return 1;
                }
              }else if(file_count == 2) // the second file name
              {
                out_file.open(arg)
                  if(out_file.fail())
                  {
                    cout << "ERROR opening output file" << arg << endl;
                    return 1;
                  }
              }
        }
    }
  
  if(file_count != 2) // exit if the user didn't specify 2 files
  {
    cout << "Usage: " << argv[0] << " [-d] infile outfile" << endl;
    return 1;
  }
  
  encrypt_file(in_file, out_file, key);
  return 0;
}
```

in this example, it define '-d' as the decryption



### random access

*nothing random about "random" access, it means you can read and modify any item stored at any location in the file*



>   only file stream support random access, cin & cout don't

every file stream has 2 special positions:

*   get position
*   put position



##### example

```c++
strm.seekg(position); //move the get and put position to a given value
strm.seekp(position); //counted from the beginning of the stream
position = strm.tellg(); //determine the current values of the get and put position
position = strm.tellp(); //counted from the beginning of the file
```

whenever you put data to the stream, the get position becomes undefined. 

*   call `seekp` when you switch from writing to reading
*   call `seekg` when you switch from reading to writing 



### binary files

*many files particularly those containing images and sounds store information as binary numbers*



##### opening a binary file

```c++
fstream strm;
strm.open(filename, ios::in | ios::out | ios::binary);
int input = strm.get(); //you read a byte with this call
```

