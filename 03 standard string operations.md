# Use Standard String Operations

## String Manipulation

*String manipulation includes changes like making all letters in your string capital, lowercase, or creating a title. Strings are immutable, so modifying a string makes a new object and does not change the original object.*

*Methods to manipulate strings include the following:*

- ```capitalize()```: Returns a copy of the original string and converts the string’s first character to an uppercase letter while making all other characters in the string lowercase letters. If the first character is a number, no letters will be capitalized. The command is ```str.capitalize()```.

- ```title()```: Converts the first character in each word to uppercase, the remaining characters to lowercase, and returns a new string. If the first character of a word is a number, the next letter will be changed to uppercase. The command is ```str.title()```.

- ```upper()```: Converts the given string into uppercase and returns the string. The command is ```str.upper()```.

- ```lower()```: Converts the given string into lowercase and returns the string. The command is ```str.lower()```.

- ```swapcase()```: Converts all uppercase characters to lowercase, all lowercase letters to uppercase, and returns the string.

## String Splitting

*The ```split()``` method allows you to break a string into list elements by specifying where you want the separation to happen. The following code shows how to use the split method:*

```
>>> str.split(separator, maxsplit)
```

*To use a method, you will take your string (str) and attach the method you want to use. Linking the method is achieved by using a "```.```" followed by the method ```(str.split())```. After the method, you will include any parameters the method needs for operation. The split method has two parameters:*

- **Separator**: The character that the method will use to split the string. The character has to be placed in quotes (```" "```) and could be a colon ("```:```"), a comma ("```,```"), a blank (```" "```), or any other character you would like to use.

- **Maxsplit**: The number of times the string will be split. If this parameter is not included, there will not be a limit.

*Here are some examples so that you can get an idea of how this method works.*

*The first example is splitting a string at the whitespaces. You will notice that you do not have to enter a parameter to split the string at each whitespace.*

```
>>> router = "cisco 3800 IOS-XE"
>>> router.split()
['cisco', '3800', 'IOS-XE']
```

*The second example splits the string at each colon (:).*

```
>>> mac_address = "bc67:98c7:77d4"
>>> mac_address.split(':')
['bc67', '98c7', '77d4']
```

## Modifying Strings

*Another way to get specific information from a string is to use the **slice** indexing. Unlike the ```split()``` method that splits strings into a list, slice indexing grabs specific characters and then returns them.*

*There are two ways to use a slice function. The first way is to use it to grab just one character of the string. To get the character, use the following command: ```str[index]```. Shown is an example of how this works. Notice that you want to get the 2 (in 192), which is the third character in the string, but because you start with 0, the index value is actually [2].*

```
>>> ip = "192.168.5.5"
>>> ip[2]
'2'
```

*You can also slice the string starting at the end.*

```
>>> ip = "192.168.5.5"
>>> ip[-3]
'5'
```

*In this example, if you want to grab 5, you would use –3 as the index.*

*The second way to use a slice is to use a range slice. The range slice allows you to grab more than one character at a time. The command to use is ```str[beginning index, ending index, step]```.*

- **Beginning index**: Where the slice of the strings starts.

- **Ending index**: Where the slice of the object ends. Know that the ending index value is not included in the returned string.

- **Step**: Optional parameter that determines the increment between each index.

*An example of the range index is shown here, where the number 168 is being returned from the string.*

```
>>> ip = "192.168.5.5"
>>> ip[4:7]
'168'
```

*To get 168, use a beginning index of 4. Use 4 because the first character starts with an index of 0 and the ending index is 7. Notice that the 7 index is the ".", but it is not included in the returned string.*

*If you want to slice a string starting from the beginning or end to grab certain characters, you can also use the following syntax.*

```
>>> ip = "192.168.5.5"
>>> ip[:3]
'192'
```

*The example is grabbing the characters “192”. Because you are starting at the beginning of the string and grabbing all characters to index 3, you do not have to put a value in the beginning index; it is automatically assumed to be 0.*

```
>>> ip = "192.168.5.5"
>>> ip[-3:]
'5.5'
```

*The same applies to the ending index if you have a value in the starting index, such as –3 in the example; if you do not put a value in the ending index, it is automatically assumed to be the end of the string.*

*Also, if you were to do ```ip[::]``` it would grab the whole string.*

*There is also an optional step parameter. The step parameter allows you to grab every second, third, or fourth (etc.) character in between the beginning index and ending index. Here is an example.*

```
>>> ip = "192.168.5.5"
>>> ip[0:11:2]
'121855'
```

*With this example, the starting index is 0, and the ending index is 11. The index 11 is used to access the whole string. The step index is set to 2, so the result is to grab the first index value and every second index value after that.*

## String Concatenation

*At some point in time, you will need to merge two strings. It could be that you are joining the string of an IP address and the string of a mask. The process of joining two or more strings is known as concatenation. You can also join more than strings. You can join a string with a variable, but the variable’s object must also be a string.*

*To join two or more strings, you will use the addition sign (```+```), and the concatenated string will become a new object. Look at the following examples to see how you can achieve this. The first example is adding two strings.*

```
>>> "192.168.5.5 " + "255.255.255.0"
'192.168.5.5 255.255.255.0'
```

*You will notice that after the 5 in the first string, there is whitespace. The reason for this is when strings are concatenated together; you explicitly add in where you want the whitespaces to be; otherwise, it becomes one long string. The second example shows the result of no explicitly added white space.*

```
>>> "192.168.5.5" + "255.255.255.0"
'192.168.5.5255.255.255.0'
```

*The third example is concatenating a string with a variable. For this to work, the object stored in the variable must be a string. In this example, the whitespace is before the 255.*

```
>>> ip = "192.168.5.5"
>>> ip + " 255.255.255.0"
'192.168.5.5 255.255.255.0'
```

*The fourth example illustrates how to concatenate two variables. The big difference here is that you have to add a whitespace because you cannot include it in the string itself.*

```
>>> ip = "192.168.5.5"
>>> mask = "255.255.255.0"
>>> ip + " " + mask
'192.168.5.5 255.255.255.0'
```

*The last example shows what happens if you try to concatenate a string with an integer. You will notice that you get a TypeError. TypeErrors are raised when you try to perform an operation on an unsupported object. Here, the integer is not supported for concatenation.*

```
>>> "interface" + 5
Traceback (most recent call last):
    File "<stdin">, line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

## Whitespace Stripping

*One of the most common tasks when working with strings is removing whitespaces. This is commonly used to remove extra whitespaces from user input or in information read from a file. There are three Python methods for removing whitespace:*

- *The ```strip()``` method removes whitespace from the beginning and end of a string. Example:*

```
>>> ip = "     192.168.5.5     "
>>> ipnew = ip.strip()
"192.168.5.5"
```

- *The ```lstrip()``` method removes whitespace from the beginning of the string. Example:*

```
>>> ip = "     192.168.5.5"
>>> ipnew = ip.lstrip()
"192.168.5.5"
```

- *The ```rstrip()``` method removes whitespace from the end of the string. Example:*

```
>>> ip = "192.168.5.5      "
>>> ipnew = ip.rstrip()
"192.168.5.5"
```

*Keep in mind that strings are immutable, which means they cannot be changed once created. Using one of these methods returns a new string and does not modify the original string.*

## Formatting and Templating

*Sometimes you need to add a variable into a string. Python uses string formatting to create a new formatted string. As of Python version 3.0, there is a new method of string formatting. Formatting is handled by the ```.format()``` method.*

*The following is an example of ```.format()```:*

```
"The model of {0} is {1} with os {2}".format(x, model, os)
```

*Inside the string, ```{0}```, ```{1}```, and ```{2}``` are placeholders for the variables; they reference the index locations of the variables passed to the format method. At the end of the string, the variables ```x```, ```model```, and ```os``` are located at indices ```0```, ```1```, and ```2```, respectively.*

*Inside the placeholders, you can add formatting types to format the results. For example:*

```
"{0:^20s}| {1:^20s}| {2:^20s}".format(d, ip, mask)
```

*In this example, you can see extra information in the placeholders. Look at the first place holder, ```{0:^20s}```; the “```0```” represents the index number, then the colon (```:```) and ```^20s``` indicate formatting for your variable. The ```^``` formats the data to appear in the center of the column, the ```20``` describes the column’s width, and the “```s```” states that it is a string. There are other formatting options such as ```<``` for left-aligned, ```>``` for right-aligned, or “```d```” for decimal instead of “```s```” for string.*

*In Python version 3.6, there is a new way to format strings called f-strings. The F-strings, or string literals, format is a more readable and less error-prone way to format strings. It is simpler to use than the ```.format()``` method and less verbose.*

*The following is an example of an f-string:*

```
f"The model of {x} is {model} with os {os}"
```

*The string starts with an "```f```" and then the variables use curly braces (```{}```) with the variable name inside them. In the example, ```x```, ```model```, and ```os``` are variables. Compared to the ```.format()``` method, an f-string is much easier to read.*

### Templates

*Templates give you a customizable interface for string substitution. While templates are not used as often as ```.format()``` or f-strings, templates provide additional features. With templates, you can pass any object that can be converted into a string as a parameter. The ```Template``` class will automatically convert these objects to a string before inserting them into the string.*

*To use templates, you must first import the ```Template``` class from the ```string``` module. Note that ```Template``` is capitalized.*

```
>>> from string import Template
```

*Once you have imported Template, you instantiate a Template using a string as an argument.*

```
>>> x = Template("The model of $device is $model with os $os")
```

*In the string, you used three placeholders: ```$device```, ```$model```, and ```$os```. The ```$``` indicates where a substitution should occur and the identifiers (```device```, ```model```, ```os```) map the placeholders to the objects to be inserted.*

*The last thing you need to do is use the ```substitute()``` method to map the objects that need to be inserted to the placeholders.*

```
>>> x.substitute(device = "router1", model = "3800", os="IOS-XE")
```

## Escape Characters

*After spending some time on strings, you know that strings are made by enclosing the string in either single (```'```) or double quotes (```"```). When a quote is inside quotes, it is known as a nested quote.*

*To use a single quote (') inside your string, you need to have double quotes (") on the outside; otherwise, your string will end at the first matching quote and you will receive a SyntaxError. Example 1:*

```
>>> 'This is Bill's router.'
```

*In Example 1, a single quote is nested inside single quotes. Since you are using a single quote (') to open the string, the string will end at the apostrophe in the word “Bill's”, since that is the next single quote ('). To solve this problem, use double quotes (") on the outside of the string, as in Example 2:*

```
>>> "This is Bill's router."
```

*For the string ```This is Bill's router.```, you could use single quotes (') on the outside and use a single quote (') on the inside if you proceed the inside quote with an escape character, as shown in Example 3:*

```
>>> 'This is Bill\'s router.'
```

*Example 4:*

```
 >>> 'Router1\n     Interface\n          Gi01' 
Router1
    Interface 
           Gi01
```

*If you want the string, you are printing to display on a new line; you can use (```\n```). In example 4 Router1, Interface, and Gi01 are all printed on different lines.*

*Example 5:*

```
>>> print('c:\\>python')
c:\>python
```

*“Escape” characters are useful for adding tabs, new lines, or quotes into your string. But what happens if you want to include a backslash in your string? To print a string similar to the one in example 5 (```c:\>python```), you will need to use a backslash before the backslash you want to print. This tells the print statement to print the second backslash.*

## String Methods

*In this topic, you will explore three more common methods for manipulating strings in a networking environment.*

**```count()``` Method**

*The ```count()``` method counts how many time a substring of characters appears in the original string. The following are parameters for this method: ```str.count(sub, start, end)```.*

- **sub**: sub-string of characters you want to count

- **start**: the index you want to start counting (optional)

- **stop**: the index you want to stop counting (optional)

*If you want to search the entire string for the substring, don’t use the start and stop parameters.*

```
>>> x = "123 123 123 123"
>>> x.count("1", 4, 10)
2
```

*In this example, you search the string for the substring of "1", starting at the 4th index and ending at the 10th index. Between those two indexes, there are two "1"s.*

**```find()``` Method**

*The ```find()``` method finds a substring of characters and returns the first index where the substring is seen. The following are parameters for this method: ```str.find(sub, start,end)```.*

- **sub**: the sub-string of characters you want to find

- **start**: the index where you want to start checking (optional)

- **stop**: the index where you want to stop checking (optional)

*If you want to search the entire string for the substring, don’t use the start and stop parameters.*

```
>>> x = "123 123 123 123"
>>> x.find("123", 4, 7)
4
```

*In this example, you will search the string for the substring of "123", starting at the 4th index and ending at the 7th index. Between those two indexes, the first time the substring is seen is at index 4.*

**```startswith()``` Method**

*The ```startswith()``` method takes a prefix of characters and returns the Boolean True or False if the string starts with that prefix. The following are parameters that you can use with this method: ```str.find(prefix, start,end)```*

- **prefix**: sub-string of characters

- **start**: the index you want to start looking (optional)

- **stop**: the index you want to stop looking (optional)

*If you want to look at the very beginning of the string for the prefix, don’t use the start and stop parameters.*

```
>>> ip = "192.168.5.5"
>>> ip.startswith("192", 4, 7)
False
```

*In this example, you will search the string for the prefix of "192", starting at the 4th index and ending at the 7th index. "192" is not the prefix between those two indexes, so the returned value is False.*

## string_operations.py 

In this example we are exploring the following:

- Store and Read a String

- Split a String

- Concatenate a String

- Explore Formatting Outputs with f-Strings

- Use Escape Characters to Format a String

- Use String Methods to Modify a String

```
connection_info = '10.254.0.1,cisco,cisco'

# print(connection_info)
connection_info_list = connection_info.split(',')
# print(connection_info_list)

n = 1
ip_three_octets = '10.254.0.'
# print(ip_three_octets + str(n))
# print(ip_three_octets + str(n + 1))
# print(ip_three_octets + str(n + 2))

ip = '10.254.0.1'
device_type = 'cisco_ios'
# print(f'The router at {ip} is running {device_type}')
# print(f"Connection Info\n{' '*30}\nIP:\t\t{ip}\nDevice Type:\t{device_type}")

# print(device_type.upper())
print(device_type.replace('_', ' '))
print(device_type.upper().replace('_', ' '))
```

### Split a String

Storing and reading a string is pretty self-explanatory at this point, so we'll focus on splitting a string. Here's the section demonstrating this:

```
connection_info = '10.254.0.1,cisco,cisco'

# print(connection_info)
connection_info_list = connection_info.split(',')
print(connection_info_list)
```

And here's a breakdown of this section:

1. Initial String: ```connection_info = '10.254.0.1,cisco,cisco'``` This defines a string where elements (IP address, username, and password) are separated by commas.

2. Splitting the String: ```connection_info_list = connection_info.split(',')``` The ```split(',')``` method is used here to break the string into a list of substrings wherever a comma ```,``` appears. In this case, it splits the string into three parts: the IP address ```'10.254.0.1'```, and the username and password, both ```'cisco'```.

3. Result: After the split, the output is a list:

```
['10.254.0.1', 'cisco', 'cisco']
```

Overall, this method is handy when dealing with CSV-style data or strings with a known delimiter.

### Concatenate a String

*Combining strings with the plus sign (```+```) operator is called concatenation. When you combine strings in this way, you must be sure to include all the necessary characters that should be in your string. Concatenation will not add any characters or whitespace to the string that you did not explicitly add yourself.*

```
connection_info = '10.254.0.1,cisco,cisco'

# print(connection_info)
connection_info_list = connection_info.split(',')
# print(connection_info_list)

n = 1
ip_three_octets = '10.254.0.'
print(ip_three_octets + str(n))
print(ip_three_octets + str(n + 1))
print(ip_three_octets + str(n + 2))
```

Here's a breakdown of the string concatenation section:

1. Splitting Again: You have the same initial string from before: ```connection_info = '10.254.0.1,cisco,cisco'``` And it’s split into a list: ```connection_info_list = connection_info.split(',')``` Resulting in: ```['10.254.0.1', 'cisco', 'cisco']```

2. Concatenation: Now the script is working with the variable ```ip_three_octets```: ```ip_three_octets = '10.254.0.'``` This variable holds the first three octets of an IP address (the "network" part).

3. Dynamic IP Creation: The next part of the script dynamically builds full IP addresses by concatenating ```ip_three_octets``` with different last octet values:

  - ```print(ip_three_octets + str(n))``` concatenates ```'10.254.0.'``` with the string version of ```n``` (which is ```1```), resulting in ```10.254.0.1```.

  - ```print(ip_three_octets + str(n + 1))``` does the same but adds ```1``` to ```n```, resulting in ```10.254.0.2```.
  
  - ```print(ip_three_octets + str(n + 2))``` adds ```2``` to ```n```, resulting in ```10.254.0.3```.
  
Key Concept: The ```+``` operator concatenates strings, and ```str()``` converts numbers to strings so they can be combined with other string elements. This method is commonly used to generate multiple similar IP addresses by modifying the last octet dynamically.

### Explore Formatting Outputs with f-Strings

*An f-string in Python is created by placing an f before the opening quote character of a string ```f'like this'```. An f-string is helpful for formatting a string and inserting data into the string. Inside an f-string, you can place variables or values between braces ```{ }``` and they will be inserted into the string.*

```
connection_info = '10.254.0.1,cisco,cisco'

# print(connection_info)
connection_info_list = connection_info.split(',')
# print(connection_info_list)

n = 1
ip_three_octets = '10.254.0.'
# print(ip_three_octets + str(n))
# print(ip_three_octets + str(n + 1))
# print(ip_three_octets + str(n + 2))

ip = '10.254.0.1'
device_type = 'cisco_ios'
print(f'The router at {ip} is running {device_type}')
```

Here's the breakdown of the Formatting Outputs with f-Strings section:

1. Initial Setup: The same ```connection_info``` string is split into a list again: ```connection_info = '10.254.0.1,cisco,cisco'``` And split into: ```['10.254.0.1', 'cisco', 'cisco']``` This is commented out since it’s not needed for the current part of the task.

2. f-Strings for Output: The key focus here is the f-string:

```
ip = '10.254.0.1'
device_type = 'cisco_ios'
print(f'The router at {ip} is running {device_type}')
```

  - f-string (formatted string) allows embedding expressions inside string literals, prefixed with ```f```.
  
  - Inside the curly braces ```{}```, the variables ```ip``` and ```device_type``` are evaluated and inserted into the string.
  
Result: This prints:

```
The router at 10.254.0.1 is running cisco_ios
```

  - The f-string substitutes the value of ```ip``` (```'10.254.0.1'```) and ```device_type``` (```'cisco_ios'```) directly into the output without having to concatenate manually.
  
Key Concept: f-Strings make your code cleaner and more readable by allowing you to format output in an intuitive and efficient way. They’re also faster than older string formatting methods.

### Use Escape Characters to Format a String

*Within a Python string, the backslash ‘\’ is an escape character. Escape characters change how Python looks at the character following the ‘\’ in a sequence of characters. If you add a backslash before a single or double quote character, that character will no longer have the capability of ending the string. When you see \' or \" in a string in Python, you know it is simply the single or double quote character and has no special behavior. You can also add a backslash before the letters "t" or "n" (```\t``` or ```\n```) to create a tab or newline character. These characters will change the whitespace you see when you print the string or write it to a file.*

```
connection_info = '10.254.0.1,cisco,cisco'

# print(connection_info)
connection_info_list = connection_info.split(',')
# print(connection_info_list)

n = 1
ip_three_octets = '10.254.0.'
# print(ip_three_octets + str(n))
# print(ip_three_octets + str(n + 1))
# print(ip_three_octets + str(n + 2))

ip = '10.254.0.1'
device_type = 'cisco_ios'
# print(f'The router at {ip} is running {device_type}')
print(f"Connection Info\n{' '*30}\nIP:\t\t{ip}\nDevice Type:\t{device_type}")
```

Here's the breakdown of the Escape Characters to Format a String section:

1. Initial Setup: The earlier ```connection_info``` is still split into a list but this section focuses on formatting the output with escape characters and whitespace, so it's not used directly here.

2. Escape Characters in the f-String:

```
ip = '10.254.0.1'
device_type = 'cisco_ios'
print(f"Connection Info\n{' '*30}\nIP:\t\t{ip}\nDevice Type:\t{device_type}")
```

This part of the script demonstrates escape characters and whitespace manipulation:

  - ```\n``` is the newline escape character, which moves the output to a new line.
  
  - ```' '*30``` adds 30 spaces, creating an indentation or gap after "Connection Info".
  
  - ```\t``` is the tab escape character, which adds a horizontal tab (typically equal to 4 or 8 spaces), allowing you to align text more easily.
  
3. Result: The output looks like this:

```
Connection Info
                             
IP:        10.254.0.1
Device Type:    cisco_ios
```

  - ```"Connection Info\n"``` prints "Connection Info" on one line and the ```\n``` moves to a new line.
  
  - ```{' '*30}``` adds 30 spaces for formatting, creating a blank line with a specific gap.
  
  - ```\t\t``` before the IP value and the device type ensures alignment of the labels (IP, Device Type) and their corresponding values.
  
4. Purpose: This example shows how escape characters like ```\n``` and ```\t``` can be used to format string outputs neatly. It is particularly useful when you want your output to be more structured, like for displaying connection info in a CLI tool or log file.

Key Concept: Escape characters are essential for controlling formatting in string outputs, making text more readable by adding spacing, newlines, or tabs. Using them within f-strings makes the output dynamic and clean, especially for console-based applications.

### Use String Methods to Modify a String

*Python strings are objects, which means they have methods. Different types of objects have unique methods; those methods will only work with those objects. If you try to use a string method with a file or list, it will not work. Python objects have an intended use and when you try to use them in a way that does not conform to that intended use, they will fail.*

```
connection_info = '10.254.0.1,cisco,cisco'

# print(connection_info)
connection_info_list = connection_info.split(',')
# print(connection_info_list)

n = 1
ip_three_octets = '10.254.0.'
# print(ip_three_octets + str(n))
# print(ip_three_octets + str(n + 1))
# print(ip_three_octets + str(n + 2))

ip = '10.254.0.1'
device_type = 'cisco_ios'
# print(f'The router at {ip} is running {device_type}')
# print(f"Connection Info\n{' '*30}\nIP:\t\t{ip}\nDevice Type:\t{device_type}")

print(device_type.upper())
```

Here's the breakdown of the String Methods to Modify a String section:

1. Initial Setup: The familiar ```connection_info``` string is split into a list again, but in this section, the focus shifts to modifying strings using built-in string methods.

2. Uppercase Conversion:

```
print(device_type.upper())
```

This line of code demonstrates the use of the ```.upper()``` method on the string ```device_type```. Here's what's happening:

  - ```.upper()```: This is a built-in string method that converts all the characters in the string to uppercase. It does not modify the original string but returns a new one.
  
    - In this case, ```device_type``` has the value ```'cisco_ios'```.
	
	- By applying ```.upper()```, it transforms it into ```'CISCO_IOS'```.
	
3. Key Concept:

- String methods like ```.upper()``` allow you to manipulate and modify strings in Python without changing the original value. Python strings are immutable, meaning once a string is created, it cannot be altered in place. Any modification (like changing case) returns a new string.

-  Uppercasing (or lowercasing) can be useful when you need to standardize text for comparison, search, or logging purposes. For example, ensuring device types are always represented in a consistent case can prevent errors or mismatches when dealing with case-sensitive systems.

**Another example:**

```
connection_info = '10.254.0.1,cisco,cisco'

# print(connection_info)
connection_info_list = connection_info.split(',')
# print(connection_info_list)

n = 1
ip_three_octets = '10.254.0.'
# print(ip_three_octets + str(n))
# print(ip_three_octets + str(n + 1))
# print(ip_three_octets + str(n + 2))

ip = '10.254.0.1'
device_type = 'cisco_ios'
# print(f'The router at {ip} is running {device_type}')
# print(f"Connection Info\n{' '*30}\nIP:\t\t{ip}\nDevice Type:\t{device_type}")

# print(device_type.upper())
print(device_type.replace('_', ' '))
print(device_type.upper().replace('_', ' '))
```

This example is a variation that introduces ```.replace()``` in combination with other string methods. Let's break it down focusing on what's new:

1. Replace Method: The new line:

```
print(device_type.replace('_', ' '))
```

- The ```.replace(old, new)``` method is used to substitute a substring within a string with another substring.

- In this case, it replaces the underscore (```_```) in ```'cisco_ios'``` with a space (```' '```), effectively transforming it into ```'cisco ios'```.

- ```.replace('_', ' ')``` is saying: "Find every underscore in this string and replace it with a space."

2. Combining Uppercase and Replace: The next line:

```
print(device_type.upper().replace('_', ' '))
```

- This is a chained method call, where two string methods are applied one after the other.

- First, the ```.upper()``` method converts the entire string ```'cisco_ios'``` to uppercase, resulting in ```'CISCO_IOS'```.

- Next, ```.replace('_', ' ')``` replaces the underscore (```_```) in ```'CISCO_IOS'``` with a space (```' '```), producing the final result ```'CISCO IOS'```.

- So, the output here is the uppercase version of the device type with the underscore replaced by a space: ```'CISCO IOS'```.

In short:

- ```.replace('_', ' ')``` modifies the string by swapping underscores for spaces. The second print statement demonstrates how string methods can be chained, first converting the string to uppercase and then replacing characters, showcasing Python's flexibility in string manipulation.
