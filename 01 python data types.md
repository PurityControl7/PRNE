# Explore Foundational Python Data Types

## Experiment with String Data

*A string is a series of characters. Strings are surrounded by single or double quotes and can contain any characters. Some characters have special functionality within a Python string. Backslash (```\```) is an escape character used to remove functionality or add functionality to a particular character. You can also use curly braces (```{}```) to mark the point in a string where you will programmatically insert data. String methods are used to manipulate or evaluate the contents of a string. Some string data examples include URL, IP address, MAC address, username, password, phone number, email address, and text output.*

### strings.py

```
import netmiko

csr1kv1 = '10.254.0.1'
csr1kv2 = '10.254.0.2'
csr1kv3 = '10.254.0.3'

username = 'cisco'
password = 'cisco'
device_type = 'cisco_ios'
port = '22'

def get_log(ip):
    net_connect = netmiko.ConnectHandler(ip=ip, device_type=device_type,
        username=username, password=password, port=port)
    return net_connect.send_command('show log')

csr1kv1_log = get_log(csr1kv1)
csr1kv2_log = get_log(csr1kv2)
csr1kv3_log = get_log(csr1kv3)

print(csr1kv1_log)
print(csr1kv2_log)
print(csr1kv3_log)
```

Let's break down this code:

1. Importing Netmiko

```
import netmiko
```

- Netmiko is a Python library used to simplify connections to network devices (like Cisco routers/switches) over SSH. It allows you to easily automate tasks such as sending commands or retrieving output without needing to manually handle SSH connections.

2. IP Addresses for Devices

```
csr1kv1 = '10.254.0.1'
csr1kv2 = '10.254.0.2'
csr1kv3 = '10.254.0.3'
```

- These three variables hold the IP addresses of your Cisco devices. You’ve defined three separate devices (```csr1kv1```, ```csr1kv2```, and ```csr1kv3```) that you want to connect to.

- Each device corresponds to a Cisco router (CSR 1000v), and the IP addresses allow you to connect and interact with each one.

3. Login Credentials

```
username = 'cisco'
password = 'cisco'
device_type = 'cisco_ios'
port = '22'
```

- Username/Password: These are the credentials used to log into the Cisco devices. In this case, both the username and password are ```'cisco'```.

- device_type: Specifies that the devices you are connecting to run Cisco IOS, which tells Netmiko what kind of command syntax to expect.

- port: You’re connecting via SSH (port 22).

4. Defining the ```get_log()``` Function

```
def get_log(ip):
    net_connect = netmiko.ConnectHandler(ip=ip, device_type=device_type,
        username=username, password=password, port=port)
    return net_connect.send_command('show log')
```

- Function Purpose: The ```get_log()``` function is responsible for connecting to a given Cisco device and retrieving its log information.

- ```netmiko.ConnectHandler()```: This creates an SSH connection to the device using the provided IP address, device type, username, password, and port. The ```ip=ip``` argument is passed into the function to specify which device you want to connect to.

- ```send_command('show log')```: Once connected, this sends the ```show log``` command to the Cisco device. The ```show log``` command in Cisco IOS retrieves system logs, which contain information about system events, errors, and operations.

- Return Value: The function returns the output of the ```show log``` command, which will be a string representing the device’s log data.

5. Fetching Logs from Each Device

```
csr1kv1_log = get_log(csr1kv1)
csr1kv2_log = get_log(csr1kv2)
csr1kv3_log = get_log(csr1kv3)
```

- For each device (identified by its IP), you call the ```get_log()``` function. It connects to the device, runs the ```show log``` command, and stores the resulting log output in corresponding variables (```csr1kv1_log```, ```csr1kv2_log```, ```csr1kv3_log```).

6. Printing the Logs

```
print(csr1kv1_log)
print(csr1kv2_log)
print(csr1kv3_log)
```

- Finally, you print the logs retrieved from each device. The script will output the logs from ```csr1kv1```, ```csr1kv2```, and ```csr1kv3``` to the terminal or console.

To summarize, this script connects to three Cisco devices using SSH, runs the ```show log``` command on each one, and prints out the log data from each device. The function ```get_log()``` simplifies the process of connecting and retrieving logs, while the use of Netmiko ensures that the SSH connection and command execution are streamlined.

## Experiment with Integer Data

*An integer is a positive or negative whole number or a zero. In Python, integers can be used to express a numerical value, perform mathematical operations, or show incrementation.*

### integers.py

```
import netmiko

ip_3_octets = '10.254.0.'
ip_last_octet = 1

username = 'cisco'
password = 'cisco'
device_type = 'cisco_ios'
port = '22'

def get_ip_int_br(ip):
    net_connect = netmiko.ConnectHandler(ip=ip, device_type=device_type,
        username=username, password=password, port=port)
    return net_connect.send_command('show ip interface brief')

while ip_last_octet <= 3:
    ip = ip_3_octets + str(ip_last_octet)  
    ip_int_br = get_ip_int_br(ip)  
    print(ip_int_br)  
    print('_' * 80)  
    ip_last_octet += 1
```

Let's break down this code:

1. Variables Setup:

    - ```ip_3_octets``` holds the first three octets of an IP address (```10.254.0.```), and ```ip_last_octet``` starts at ```1```. This is the starting point for constructing the full IP addresses of your devices.

2. ```get_ip_int_br()``` Function:

    - This function connects to a Cisco device using its IP address, sends the command ```show ip interface brief```, and returns the output, which lists interface statuses and IP addresses.

3. ```while``` Loop:

    - The loop runs while the last octet is less than or equal to ```3```, meaning it will iterate over the IP addresses ```10.254.0.1```, ```10.254.0.2```, and ```10.254.0.3```.

    - In each iteration, the full IP is formed by combining ```ip_3_octets``` with the current ```ip_last_octet```, then the ```get_ip_int_br()``` function is called to retrieve the interface details for that IP.

    - The results are printed, followed by a separator line (```_``` * 80), and then the last octet (```ip_last_octet```) is incremented by ```1``` for the next iteration. The ```* 80``` is multiplying the underscore character (```'_'```) 80 times, which results in a string of 80 underscores being printed. It’s a simple way to create a long horizontal separator line in the output to visually distinguish the information from each device.

To summarize, this script loops through a range of three IP addresses, connects to each Cisco device, and prints out the interface statuses. It automates the process of querying multiple devices, making it easier to gather network information.

## Experiment with Float (Floating-Point Integer) Data

*A floating-point integer (known simply as a float) is used in the same way as an integer, but it contains a decimal and numbers following that decimal. A float is the numerical representation of a fraction. Floats are used to provide values that are found between two consecutive whole numbers.*

### floats.py

```
import netmiko

ip_base = '10.254.'
ip_end = 0.1

username = 'cisco'
password = 'cisco'
device_type = 'cisco_ios'
port = '22'

def get_ip_int_br(ip):
    net_connect = netmiko.ConnectHandler(ip=ip, device_type=device_type,
        username=username, password=password, port=port)
    return net_connect.send_command('show ip interface brief')

while ip_end <= 0.3:
    ip = ip_base + str(ip_end)   
    ip_int_br = get_ip_int_br(ip)   
    print(ip_int_br)   
    print('IP int from ' + ip)   
    print('_' * 80)   
    ip_end += .1
	ip_end = round(ip_end, 2)
```

Let's break down this code:

1. IP Construction:

    - The script starts with ```ip_base``` set to ```'10.254.'```, which represents the first two octets of the IP address.

    - The ```ip_end``` variable starts at ```0.1``` and will increment in the loop. This float value represents the third octet in the IP address.

2. ```get_ip_int_br()``` Function:

    - This function connects to a Cisco device using SSH, retrieves the ```show ip interface brief``` output (interface statuses and IP addresses), and returns the result.

3. ```while``` Loop:

    - The loop runs while ```ip_end``` is less than or equal to ```0.3```. In each iteration, it constructs an IP address by concatenating ```ip_base``` and ```ip_end```. This forms IPs like ```10.254.0.1```, ```10.254.0.2```, and ```10.254.0.3```.

    - The function ```get_ip_int_br()``` is called with this IP, and the results (interface details) are printed out. It also prints a custom message showing which IP was used, followed by an 80-character separator (```'_' * 80```), similar to the previous script.

4. Float Precision Adjustment:

    - After each loop iteration, ```ip_end``` is incremented by ```0.1```, which causes it to move from ```0.1``` to ```0.2``` and then to ```0.3```.

    - ```round(ip_end, 2)``` ensures that the value is rounded to two decimal places, preventing any floating-point precision issues (like ending up with ```0.3000001``` instead of ```0.3```). In other words, the line ```ip_end += .1``` is shorthand for ```ip_end = ip_end + 0.1```. This means that the value of ```ip_end``` is being incremented by 0.1 during each iteration of the loop. So, if ```ip_end``` starts at 0.1, after the first iteration it becomes 0.2, then 0.3, and so on. That small increment allows you to step through different third-octet values for the IP address. And since floats can sometimes introduce precision issues (like giving you ```0.3000000000001``` instead of ```0.3```), the ```round(ip_end, 2)``` is there to keep things clean and ensure only two decimal places.

To summarize, this script loops through three IP addresses (```10.254.0.1``` to ```10.254.0.3```), connects to each, retrieves interface statuses, and prints them out with a clean separation. The use of floats for the IP address increment is the unique twist here, with rounding ensuring correct values.

## Experiment with Boolean Data

*A Boolean is the simplest of all data types but it is extremely powerful when used correctly. A boolean can only be one of two values: True or False. When stored in memory, a boolean takes up one bit of memory because it is simply either a 0 (false) or a 1 (true). Booleans are used to evaluate circumstances in a script and have the script decide what should happen next based on that evaluation result.*

### booleans.py

```
import netmiko

ip_list = [
    #'10.254.0.1',
    '10.254.0.2',
    #'10.254.0.3',
]

username = 'cisco'
password = 'cisco'
device_type = 'cisco_ios'
port = '22'

def get_ip_int_br(ip):
    net_connect = netmiko.ConnectHandler(ip=ip, device_type=device_type,
        username=username, password=password, port=port)
    return net_connect.send_command('show ip interface brief')

ip_3_octets = '10.254.0.'
ip_last_octet = 1

while ip_last_octet <= 3:
    ip = ip_3_octets + str(ip_last_octet)
    ip_int_br = get_ip_int_br(ip)
	if len(ip_int_br) > 0: 
        contains_text = True
    if ip in ip_list and contains_text:
	    print('IP interface from ' + ip)
        print(ip_int_br)
        print('-' * 80)
    ip_last_octet += 1
```

Let's break down this code:

1. ```ip_list``` Definition:

    - ```ip_list = [...]``` is a list (or array) of IP addresses. The IPs ```'10.254.0.1'``` and ```'10.254.0.3'``` are commented out, which means they're inactive and will not be included in the list at runtime. Only ```'10.254.0.2'``` will be used in the logic.

    - The list is formatted with each item on its own line, and the square brackets (```[...]```) enclose the entire list. This is purely for readability, allowing you to easily add or remove IP addresses. Whitespace inside the list is for clarity and has no functional impact in Python. The important part is that each element is separated by commas.

2. Functionality of ```get_ip_int_br()```:

    - This function is familiar: it connects to a Cisco device using SSH and retrieves the output of ```show ip interface brief```. The IP address passed to the function is the one being tested in the loop.

3. ```while``` Loop Mechanics:

    - The loop runs as long as ```ip_last_octet``` is less than or equal to 3. It constructs IP addresses by appending the current value of ```ip_last_octet``` (as a string) to the base IP ```'10.254.0.'```, resulting in addresses like ```10.254.0.1```, ```10.254.0.2```, and ```10.254.0.3```.

- With each iteration:

    1. IP Construction: The variable ```ip``` holds the constructed IP address (```ip = ip_3_octets + str(ip_last_octet)```).
	
	2. Fetch Interface Information: The ```get_ip_int_br(ip)``` function is called to retrieve the interface details for the current IP address.
	
	3. Check if the Response Contains Data:
	
	    - The line ```if len(ip_int_br) > 0```: checks if the result from ```get_ip_int_br()``` contains any output (meaning the device responded with data). If the length of the returned string is greater than 0, it sets the ```contains_text``` variable to ```True```.
		
4. List and Boolean Conditions:

    - Condition 1: ```if ip in ip_list``` checks if the current IP address is part of the ```ip_list``` (in this case, only ```10.254.0.2``` is in the list). This ensures only specific IPs are processed further.

    - Condition 2: ```contains_text``` ensures that there was actual output returned from the ```get_ip_int_br()``` command.

    - If both conditions are ```True```, the script:

        - Prints a message saying it fetched interface details for the current IP.
	
	    - Prints the interface details and a separator line (```'-' * 80```).
	
5. Incrementing the Octet:

    - At the end of each iteration, ```ip_last_octet += 1``` increases the last octet of the IP address by 1. This moves the loop through ```10.254.0.1```, ```10.254.0.2```, and ```10.254.0.3```.

To summarize:

- The script iterates over three possible IP addresses but only prints details for the ones in ```ip_list``` (here, just ```10.254.0.2```).

- It checks if the device at each IP responded with valid interface data.

- Only valid, listed IPs with actual data are printed, along with a separator line for readability.

## Bonus: ```dir()``` and ```help()```

*This is the first Python script introduced in Cisco PRNE, and I'm including it here for posterity. While it may not be as complex as the scripts that followed (like the ones shown above), it's the foundational piece upon which everything else is built. I’ll provide it here along with a brief breakdown.*

### get_software_version.py

```
import netmiko

ip = '10.254.0.1'
username = 'cisco'
password = 'cisco'
device_type = 'cisco_ios'
port = '22'

net_connect = netmiko.ConnectHandler(ip=ip, device_type=device_type,
    username=username, password=password, port=port)
show_version = net_connect.send_command('show version')
print(show_version)
```

Here are key details:

1. ```net_connect``` Variable:

    - ```net_connect``` is an instance of the ```ConnectHandler``` class from Netmiko. It establishes an SSH connection to the device (in this case, a Cisco router or switch).
	
	- This connection lets us execute commands like ```'show version'``` through methods such as ```send_command()```.
	
2. Using ```dir()``` to Explore Attributes and Methods:

    - In an interactive Python console, running ```dir(net_connect)``` will list all the available attributes and methods for this object. This helps us see what functionality the object provides (e.g., methods like ```send_command```, ```disconnect```, etc.). For example:
		
	```
	dir(net_connect)
    ```
	
3. Using ```help()``` for Detailed Info:

    - To get more detailed information on how to use specific methods, like ```send_command```, we can use ```help()```. This gives us insight into how the method works, its parameters, and other useful info. For example:
		
	```
	help(net_connect.send_command)
    ```
	
    - This will show you details on how to pass commands, timeouts, and other useful parameters to customize its behavior.
	
4. To summarize:

    - By using ```dir()``` to get an overview and ```help()``` for in-depth details, you can learn more about the capabilities of ```net_connect``` and other Netmiko components. This way, you can explore the full range of options and functionality that the ```ConnectHandler``` object offers.

5. More examples:

    - Including variants of the ```dir()``` command is a great idea to showcase how it works with different objects, just like we discussed before. Here’s how you can incorporate it with your examples:
	
	```
    import os
    print(dir(os))  # This will list all the attributes and methods available in the 'os' module

    my_list = [1, 2, 3]
    print(dir(my_list))  # This will list all the attributes and methods available for a list object
	```
	
	Explanations:
	
	- ```dir(os)```: This lists all the attributes and methods available in the ```os``` module. It helps you see what functions you can call, such as ```os.path()```, ```os.getcwd()```, etc. Here is example output:
	
	```
	['_exit', 'abort', 'access', 'chdir', 'chmod', 'chown', 'close', 'cpu_count', 'getcwd', ... ]
    ```
	
	- ```dir(my_list)```: This shows all the methods and attributes associated with a Python list object. It lets you know what actions you can perform on the list, like ```append()```, ```extend()```, or ```pop()```. Another example output:
	
	```
	['append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
    ```
	
	By including these variants, we're demonstrating how ```dir()``` works with both built-in Python objects (like lists) and external libraries (like ```os``` or Netmiko's ```ConnectHandler```). This encourages deeper exploration of any object you come across in Python!

