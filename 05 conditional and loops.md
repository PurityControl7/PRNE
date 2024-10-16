# Loops

*In programming, there will be times that your code needs conditional paths, but there will also be times that you want the same code to execute multiple times. Executing code multiple times is known as iteration. When iteration is implemented in code, it is known as a loop. Loops will execute while some condition is met. "For" and "while" loops are two types of control structures that can determine when and how many times a code block is executed.*

## For Loops

*In Python, some objects are known as iterables. Iterables are objects such as strings, lists, dictionaries, tuples, and sets that can return each member one at a time. If you need to iterate over an object and execute a code block on each of the object members, use a "for" loop.*

![For Loops](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/for_loop.png)

*A "for" loop is made of a "for” statement and the code block you want to execute. The layout of a "for” statement follows.*

```
for <var> in <iterable>:
```

*To build the "for” statement you start with the keyword "for" followed by a variable ```<var>```. The variable can be any name, but it is best to use something that gives meaning to what you are doing. After the variable, you add the word "in" followed by the iterable. This iterable can be a string, list, dictionary, tuple, or set.*

*The line of code takes each member of the iterable and assigns it to the variable one loop at a time. You can then execute your code block using the variable. Let's look at an example:*

```
>>> for i in "string":
>>>    print(i) 
s
t
r
i
n
g
```

*In this example, ```i``` is a variable that will hold each objects member that we iterate through to be used in the code block. The result is that each letter of "string" is stored in ```i``` and then printed. The “for” loop will exit after the last member of the iterable is reached.*

## While Loops

*A "while" loop is used to iterate over a code block as long as the test expression is True. “While” loops should be used when you don’t know how many times the code block should be executed. “While” loops are used often when a user’s input might determine if or how many times the code should execute.*

![While Loops](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/while_loop.png)

*The basic format of a “while” statement follows:*

```
while <expression>:
```

*We start the statement with the keyword "while", followed by an expression. The expression uses a variable that is set to a specific value before the loop. The expression is checked, and if it evaluates to True, the code block is executed. Typically, the variable used in the expression is modified inside the code block. After each iteration, the expression is checked, and the code block will continue to execute until the expression evaluates to False. Let's look at the example.*

```
>>> i = 4
>>> while i > 0:
>>>    print(f'The value of i is {i}')
>>>    i -= l
```

*Before the "while" loop, the variable ```i``` was assigned the value of 4. The "while" loop evaluates the expression ```i > 0```, so for as long as ```i``` is greater than 0, the loop will execute. The code block inside the "while" loop prints a string, then subtracts 1 from ```i```. As long as ```i > 0```, the loop will execute again.*

## Loops with List, Dicts, and Ranges

*Now that you understand the different loops you can use, let’s look at how to use them to iterate over a list or dictionary. This will allow you to abstract items from a list or keys, values, or key-value pairs of a dictionary. Another component of using loops is the range function, which generates a sequence of numbers based on the arguments specified.*

### Loops with Lists

![Loops with Lists](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/loop_with_list.png)

*Let’s start with how to iterate over a list using a “for” loop shown in the example:*

```
for device in devices: 
     print(device)
```

*In the example, there is a list that contains the items "router1," "router2," "router3," and "switch1". To access each of these items, you can use a “for” loop. There is a variable named device in the “for” loop to which each item will be assigned. The variable is used in the print statement to print each device in the list.*

### Loops with Dictionaries

*Looping through dictionaries is not as easy as lists. In dictionaries, you can abstract keys, values, or key-value pairs (known as an item) to use in your code block. A dictionary has methods that can be used to abstract each of these items. Let’s examine each of these, starting with keys.*

![Loop with Dictionary](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/loop_with_dictionary.png)

*To get the keys from a dictionary, use the ```keys()``` method. The ```keys()``` method saves the dictionary keys in an iterable that can then be used in a “for” loop. The example shows a “for” loop with a variable named ```keys```. The iterable used in the for loop is ```device.keys()```. You can then use the print statement to print the values stored in the keys variable.*

*To get the values from a dictionary, use the ```values()``` method. The ```values()``` method saves the value of each key in an iterable. The example shows a “for” loop with a variable named ```values```. The iterable used in the for loop is ```device.values()```. You can then use the print statement to print the values stored in the values variable.*

*To get the key-value pairs from the dictionary, you use the ```.items()``` method. The ```.items()``` method saves the key-value pairs in tuples. Tuples are similar to lists, but the items in the tuple cannot be changed.*

![Loop with Dictionary2](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/loop_with_dictionary2.png)

*The example has a dictionary with the key value pairs of "device": "router," "model": "3800," and "os": "IOS-XE". You can use a “for” loop to iterate over the items to print in the print statement. The example uses a “for” loop with the variable name item and the iterable used in the “for” loop is ```device.items()```. ```Device.items()``` takes each key-value pair and saves it in a separate tuple that you can then use to execute the code inside the “for” loop.*

### Loops with Ranges

*Up to this point, you have learned how to use a loop to iterate through all the items in a list or dictionary. What if you only want certain items in a list or dictionary? Maybe you are using an API that returns data in a JSON format. You convert the JSON format to a Python dictionary and you only want certain items. You can achieve this using the ```range()``` function. The ```range()``` function allows you to generate a series of numbers within a given range. This given range depends on how many arguments you pass to it.*

![Loop with Ranges](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/loop_with_ranges.png)

*The command for ```range()``` follows.*

```
range(start, stop, step)
```

- **start**: *number to start*

- **stop**: *number to stop. The stop number is not included in the count. So, if 1 is the start and 8 is the stop, the range will be 1-7.*

- **step**: *the difference between one number to the next*

*A simple example follows.*

```
for i in range(1, 4):
     print("router" + str(i)) 
"router1"
"router2"
"router3"
```

*In this example, the range is 1 to 4; each value is stored in the variable ```i```. It then prints "router" along with the number stored in ```i```.*

*Another way to use ```range()``` is with ```len()```. The ```len()``` function returns the total number of items in an object. This can be used as the stop number, so it will always be the last item in the object.*

```
for i in range(2, len(devices)):
    print(device[i])
```

*In this example, you want to print each item starting with index 2 through the last item. To do this, use the ```range()``` function with a starting number of 2. If you don’t know how many items are in the object, you can use the ```len()``` function to determine the stop number. If the total number of items is less than two, using the ```len()``` function will return an error.*

### Loops with Conditionals

![Loop with Conditionals](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/loop_with_conditionals.png)

*Conditionals will execute a block of code once if a condition is met and loops will continue to execute a block of code as long as a condition is met. At times you will want to combine these two. The example uses a for loop to iterate over a list with an if-statement inside the for loop checking for a specific condition.*

*Line 1 of the code is a list of routers. The code starting at line 2 uses a for loop to iterate over each item in the list (device) and execute the block of code below it. The key is that you only want part of the code to execute if a condition is met. To do this you use an if-statement.*

*For each item in the list ```device```, the if-statement is will be evaluated to see if device[i] is equal to "Router3". If this condition is False, the code block under the if-statement is skipped and the print statement in line 6 is executed. The for loop then assigns the next item in the list to ```i``` and the if statement is evaluated again. When or if the if-statement evaluates to True, the print statement in line 5 is executed and then the loop continues until there are no more items in the list.*

*You can use conditionals inside of loops to help determine when a block of code runs. When using conditionals, there might be times where, if a condition is meet inside a loop, we break completely out of the loop or want to skip executing the block of code below the loop and start the loop over. In this case, there are two statements you can use: the break and continue statements.*

![Break Statement](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/break_statement.png)

*The break statement terminates the loop containing it. Let’s look at an example.*

```
device = ["Router1", "Router2", "Router3", "Router4"]
for i in range(len(device)):
     if device[i]  == "Router3":  
          break  
     print(device[i])
```

*In the example, we are iterating over a list of devices, and when ```device[i] == "Router3"``` it will break out of the loop. This script results in only Router1 and Router2 being printed.*

![Continue Statement](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/continue_statement.png)

*The continue statement is used to skip the rest of the code inside a loop for the current iteration. The loop does not terminate but continues with the next iteration. Let’s look at an example.*

```
device = ["router1", "Router2", "Router3", "Router4"]
for i in range(len(device)):
     if device[i]  == "Router3": 
          continue  
     print(device[i])
```

*In the example, we are iterating over a list of devices, and when ```device[i] == "Router3"``` it will continue. Continue means it will skip the print statement and start the next iteration. This script results in only Router1, Router2, and Router4 being printed.*

## Use for Loops

*Python for loops are used to iterate over a sequence. You can iterate over strings, lists, tuples, sets, dictionaries, and other iterable objects. Loops will behave differently when dealing with each of these data types. When iterating over strings, the variable you use will take each character's value; over lists, sets, and tuples, each item; and for dictionaries, each key.*

### for_loops.py

```
import netmiko

ip_string = '10.254.0.1,10.254.0.2,10.254.0.3' 

for ip in ip_string.split(','):
    username = 'cisco'
    password = 'cisco'
    device_type = 'cisco_ios'

    net_connect = netmiko.ConnectHandler(ip=ip, username=username, 
                        password=password, device_type=device_type)
    sh_ip_int = net_connect.send_command('sh ip int')
    print(sh_ip_int)

```

Breakdown of the for loop:

  - Initial Setup:
  
    - The script starts by importing ```netmiko```, which is a library used for automating interaction with network devices via SSH.
	
	- Variables are set up, including ```ip_string``` containing a string of three IP addresses separated by commas.
	
  - The for Loop:
  
    - ```for ip in ip_string.split(',')```:
	
	  -  This line is crucial. It takes the ```ip_string``` and splits it into a list of IP addresses using the ```split(',')``` method. So, it breaks ```"10.254.0.1,10.254.0.2,10.254.0.3"``` into ```['10.254.0.1', '10.254.0.2', '10.254.0.3']```.
	  
	  - Then, the loop will iterate over each IP address in the list one by one.
	  
	- Inside the Loop:
	
	  - For each ```ip``` (e.g., ```10.254.0.1``` in the first iteration), the script creates a connection to the device using ```netmiko.ConnectHandler()```. The required parameters (like IP, username, password, device type) are passed.
	  
	  - Once connected, it runs the ```sh ip int``` command on the device by calling ```net_connect.send_command('sh ip int')```.
	  
	  - The result of this command is stored in the variable ```sh_ip_int``` and printed.
	  
The Flow:

1. First, it connects to ```10.254.0.1```, runs the command, and prints the result.

2. Then, it moves to ```10.254.0.2```, connects, runs the same command, and prints the output.

3. Lastly, it does the same for ```10.254.0.3```.

End Result:

- It prints the output of ```sh ip int``` for each IP in the list.

### for_loops_2.py

```
import routers

for router in routers.creds:
    print(routers.get_ip_int_br(**router))
    print('-' * 80)
```

Breakdown:

  1. Importing ```routers``` Module:
  
  - This script imports a module named ```routers``` (more on that later), which likely contains:
	
- A dictionary or list of router credentials (```routers.creds```).
	  
 - A function called ```get_ip_int_br()``` that retrieves the IP interface details of a router.
	  
  2. The for Loop:
  
  - ```for router in routers.creds:```:
	
  - This line loops over each item in ```routers.creds```.
	  
  - What is ```routers.creds```?: It is likely a list of dictionaries, where each dictionary contains the credentials (like IP, username, password, etc.) for a router. So, for each iteration, ```router``` is a dictionary.
	  
  3. Calling ```get_ip_int_br()```:
  
  - ```routers.get_ip_int_br(**router)```
	
  - The ```**router``` part is important. It unpacks the dictionary ```router``` into keyword arguments when calling ```get_ip_int_br()```. For example, if ```router = {'ip': '192.168.1.1', 'username': 'admin', 'password': 'cisco'}```, then ```get_ip_int_br()``` is called as:
	  
```
routers.get_ip_int_br(ip='192.168.1.1', username='admin', password='cisco')
```
  - This function probably connects to the router and retrieves the output of the show ip interface brief command (or a similar one) to display interface details.
	  
4. Print the Output:

 - ```print(routers.get_ip_int_br(**router))```:
  
  - This prints the result of the ```get_ip_int_br()``` function, which is likely the IP interface details of the router.
	
The Flow:

1. The script loops over each router in ```routers.creds```.

2. For each router, it unpacks the credentials into the ```get_ip_int_br()``` function.

3. It prints the IP interface details for the router.

4. It prints a line of hyphens to separate the outputs from different routers.

Example Output:

```
Interface              IP-Address      OK? Method Status                Protocol
FastEthernet0/0        192.168.1.1     YES manual up                    up
FastEthernet0/1        192.168.1.2     YES manual up                    up
...
--------------------------------------------------------------------------------
Interface              IP-Address      OK? Method Status                Protocol
FastEthernet0/0        192.168.2.1     YES manual up                    up
FastEthernet0/1        192.168.2.2     YES manual up                    up
...
--------------------------------------------------------------------------------
```

### routers.py

```
import netmiko

creds = [{
    'ip' : '10.254.0.1',
    'username' : 'cisco',
    'password' : 'cisco',
    'device_type' : 'cisco_ios'
},{
    'ip' : '10.254.0.2',
    'username' : 'cisco',
    'password' : 'cisco',
    'device_type' : 'cisco_ios'
},{
    'ip' : '10.254.0.3',
    'username' : 'cisco',
    'password' : 'cisco',
    'device_type' : 'cisco_ios'
}]

def get_ip_int_br(ip, username, password, device_type):
    username = 'cisco'
    password = 'cisco'
    device_type = 'cisco_ios'

    net_connect = netmiko.ConnectHandler(ip=ip, username=username, 
                        password=password, device_type=device_type)
    ip_int_br = net_connect.send_command('sh ip int br')
    return ip_int_br
```

Here's a very brief breakdown:

1. ```creds``` List:

  - It holds dictionaries with the login credentials (```ip```, ```username```, ```password```, and ```device_type```) for three routers. This is the list being looped through in the previous script.

2. ```get_ip_int_br()``` Function:

  - The function takes in the router's ```ip```, ```username```, ```password```, and ```device_type```.
  
  - It uses Netmiko to connect to the router (```ConnectHandler```), then sends the command ```sh ip int br``` (show IP interface brief). Finally, it returns the output of that command.
  
Assumptions Review:

- Everything aligns with what we assumed in the previous breakdown: ```creds``` holds the router credentials and the ```get_ip_int_br()``` function fetches and prints interface details from each router.

## Use while Loops

*In this discovery, you will work with a simple while loop and experiment with the statements that go hand in hand with a while loop: break and continue. This discovery aims to demonstrate what type of logic you should employ when creating a while loop.*

### while_loop.py

```
import netmiko

last_octet = 1
while last_octet <= 3:
    if last_octet == 1:
        last_octet += 1
        # continue
        print('While loop exited with break statement')
        break
    ip_address = '10.254.0.' + str(last_octet)
    # print(ip_address)
    net_connect = netmiko.ConnectHandler(
        ip=ip_address,
        device_type='cisco_ios',
        username='cisco',
        password='cisco'
    )
    print(net_connect.send_command('sh run | include hostname'))
    print('_' * 20)
    last_octet += 1
```

This example has a while loop at its core that controls the flow of the script, so let's break it down with a focus on how it operates.

Key points of the ```while``` loop:

 1. Initial ```last_octet``` setup:
  
 - The variable ```last_octet``` starts at 1.
	
 - The loop will continue to run as long as ```last_octet <= 3```.
	
 2. First condition (```if last_octet == 1```):
  
 - When ```last_octet``` is 1, the ```if``` statement triggers:
	
 - It increments ```last_octet``` by 1 (```last_octet += 1```), so now it's 2.
	  
 - Then, it breaks the loop entirely with the ```break``` statement. The code after the ```break``` inside the loop won't run, so the loop ends without going through the rest of the iterations.
	  
 - The commented ```continue``` would normally skip the rest of the current loop iteration, but it's not active here.
	
 3. Second iteration (if ```break``` didn’t happen):
  
 - In the absence of ```break```, the next ```last_octet``` would be 2, and the script would build an IP address (```'10.254.0.' + str(last_octet)```).
	
 - A connection would be established using ```netmiko``` to the device with IP ```10.254.0.2```.
	
 - The script would then execute the command ```sh run | include hostname```, fetching the hostname info from the router.
	
 - It would print a separator (```'_' * 20```), and the loop would continue until ```last_octet > 3```.
	
Conclusion:

- Since the ```break``` occurs when ```last_octet is 1```, the loop ends immediately, skipping everything else. Essentially, this script will just print ```'While loop exited with break statement'``` without even hitting the ```netmiko``` commands or further iterations, so the focus of this loop is really around that early break and conditional flow.
