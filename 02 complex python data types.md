# Explore Complex Python Data Types

## Experiment with Lists

*A list is surrounded by brackets, and the items in a list can be any data type. A list can contain and number of items separated by commas and each item in a list can be found using its index value. The following is an example of a list of IP addresses:*

```
ip_list = ['10.254.0.1', '10.254.0.2', '10.254.0.3']
```

*Objects stored in a list can have different data types from one another; data-type consistency within a list makes it easier to work with that list's contents. Lists are mutable, meaning that you can add or remove items to or from a list that exists. It is common to initialize an empty list and programmatically populate the list with data.*

*The index assigns a number to each object in the list. The first object is assigned a zero (0), the next is assigned one (1), continuing until you reach the end of the list. Lists also have reverse indices that start at the end of the list and work backwards to the beginning. The last object in the list is assigned an index of negative one (-1), next to the last is a negative two (-2), continuing until you reach the first object in the list.*

*Since each object in a list has an index, you can retrieve an object from a specific location. The code to retrieve an object from an index is simple.*

```
>>> devices = ["router1", "router2", "switch1", 5]
>>> devices[2]
'switch1'
```

*This first example above shows how to retrieve an object using the index from left to right, starting from the front of the list. You use index 2 to retrieve "switch1". Keep in mind that the index system starts with 0.*

```
>>> devices = ["router1", "router2", "switch1", 5]
>>> devices[-3]
'router2'
```

*The second example shows how to retrieve an object using the index from right to left, starting from the end of the list. You use index -3 to retrieve "router2".*

### Common List Methods

*To add an object to the end of the list, use the append method. The syntax is ```list_name.append(object_name)```. For example:*

```
>>> devices = ["router1", "router2", "router3"]
>>> devices.append("switch1")
>>> devices
["router1", "router2", "router3", "switch1"]
```

*To add an object at a specific location in the list, use the insert method. The insert method has two parameters; the first is the index location where you want to add to the object and the second is the object you want to add. The syntax is: ```list_name.insert(index_number, object_name)```. For example:*

```
>>> devices = ["router1", "router2", "router3", "switch1"]
>>> devices.insert(3, "router4")
>>> devices
["router1", "router2", "router3", "router4", "switch1"]
```

*Removing objects from a list can be achieved in three different ways. You can remove the last object in the list, remove an object at a specific index, or remove a specific object. To remove the last object in the list, use the pop method:*

```
>>> devices = ["router1", "router2", "router3", "router4", "switch1"]
>>> devices.pop()
'switch1'
>>> devices
["router1", "router2", "router3",  "router4"]
```

*To remove an object at a specific index, use the pop method with the index number as a parameter. The syntax is: ```pop(index_number)```:*

```
>>> devices = ["router1", "router2", "router3", "router4", "switch1"]
>>> devices.pop(3)
'router4'
>>> devices
["router1", "router2", "router3", "switch1"]
```

*To remove an object itself from a list, use the remove method. The remove method has one parameter specifying the object you want to remove. The syntax is: ```remove(object_name)```:*

```
>>> devices = ["router1", "router2", "router3", "router4", "switch1", "router1"]
>>> devices.remove("switch1")
>>> devices
["router1", "router2", "router3", "router4",  "router1"]
```

*Finally, the count method returns the number of times a specified element appears in a list. The count method has one parameter, the object you want to count. The syntax is: ```count(object_name):```*

```
>>> devices = ["router1", "router2", "router3", "router4", "switch1", "router1"]
>>> devices.count("router1")
2
```

*To check the total number of items in a list, use the ```len()``` function. The ```len()``` function shows the total number of items in a list, tuple, or set, the total number of characters in a string, or the total number of key-value pairs in a dictionary.*

```
>>> len(devices)
6
```

### lists.py

```
import netmiko

ip_list = [
    '10.254.0.1' ,
    '10.254.0.2' ,
    '10.254.0.3' ,
]
#print(ip_list[0])
#print(ip_list[-1])

username = 'cisco' 
password = 'cisco' 
device_type = 'cisco_ios' 
port = 22

output_list = []
for ip in ip_list:
    net_connect = netmiko.ConnectHandler(ip=ip, device_type=device_type, 
        username=username, password=password, port=port)
    output = net_connect.send_command('show ip interface brief')
    output_list.append(output)

for output in output_list:
    print(output)
```

Here’s a quick breakdown of how lists operate within the script:

1. ip_list Definition:

  - ```ip_list``` is defined as a list of IP addresses. Each IP is stored as a string in this list. The list is useful for managing multiple devices (or items) at once. You can access individual items with indexing (e.g., ```ip_list[0]``` for the first IP, or ```ip_list[-1]``` for the last one).
	
2. output_list:

  - An empty list ```output_list``` is created to store the outputs from each device interaction. This shows how lists are dynamic; you can start with an empty list and append items to it using the ```append()``` method.
	
3. For Loop Iteration:

  - The script loops over each IP in the ```ip_list``` using ```for ip in ip_list```. In every iteration, it connects to the respective IP and runs the command ```'show ip interface brief'```.
	
  - The output of each command is stored in output, and then ```output_list.append(output)``` adds it to the ```output_list```. This demonstrates how you can easily work with lists to iterate over multiple elements and store results.
	
4. Output Printing:

  - Finally, the second ```for``` loop iterates over ```output_list``` to print out the results. This shows how lists can store multiple outputs, which can then be accessed and manipulated later.
	
In summary, lists in this script are used to store and process multiple IP addresses and network outputs in a structured way. We can see how lists can be dynamically updated and iterated through easily.

## Experiment with Tuples

*Tuples contain a series of ordered comma-separated-values like lists, but they are surrounded by parentheses. Tuples are immutable, meaning you cannot change a tuple once it is created in memory. In other words, you cannot add items to or remove items from a tuple once it is defined. Therefore, it is illogical to declare an empty tuple. One great thing about lists and tuples is that they can hold a bunch of different data-types, including other arrays. The following is an example of a tuple containing IP address strings:*

```
ip_tuple = ('10.254.0.1', '10.254.0.2', '10.254.0.3')
```

*Like lists, tuples are indexed, allowing you to retrieve items from a specific location in the tuple. Since tuples can't be changed, they are used to store values that you don't want to be modified or overwritten. The examples show how to retrieve objects from a tuple:*

```
>>> os_type = ("IOS", "IOS-XE", "IOS-XR", "NX-OS")
>>> os_type[2]
'IOS-XR'

>>> os_type = ("IOS", "IOS-XE", "IOS-XR", "NX-OS")
>>> os_type[-4]
'IOS'
```

### Common Tuple Methods

*There are two methods to use with tuples. The first is a count method; this method counts the number of times an item appears in the tuple. The example shows a tuple named os_type that includes four items. To count the number of times IOS appears in the tuple, use the command ```os_type.count("IOS")```:*

```
>>> os_type.count("IOS")
1
```

*The second method is an index method. The index method returns the index location of a specific item. To check the index for "IOS-XR", use the command ```os_type.index("IOS-XR")```:*

```
>>> os_type.index("IOS-XR")
2
```

### tuples.py

```
import netmiko
import pprint

username = 'cisco' 
password = 'cisco' 
device_type = 'cisco_ios' 
port = 22 

ip_tuple = (
    '10.254.0.1' ,
    '10.254.0.2' ,
    '10.254.0.3'
)

output_list = []
for ip in ip_tuple:
    net_connect = netmiko.ConnectHandler(ip=ip, device_type=device_type, 
        username=username, password=password, port=port) 
    hostname = net_connect.send_command(
        'sh run | include hostname'
    ).strip() 
    ios_xe_version = net_connect.send_command(
        'sh version | section Cisco IOS XE Software, Version'
    ).strip()
    output_tuple = (hostname, ios_xe_version)
    output_list.append(output_tuple)

pprint.pprint(output_list)
```

Focus on Tuples:

  - ip_tuple: The tuple ```ip_tuple``` stores the IP addresses of network devices you want to connect to. Tuples are immutable, meaning their values can't be changed after being assigned. In this case, it ensures that the IP addresses remain constant throughout the script.

  - output_tuple: For each device, the script retrieves two pieces of information: the hostname and the IOS XE version. These two values are stored together as a tuple ```output_tuple``` before being added to the ```output_list```. By using tuples here, you efficiently pair the hostname and version for each device.

Key Details:

  - for loop: Iterates through ```ip_tuple```, connecting to each device using the ```netmiko.ConnectHandler``` method. It leverages the data in the tuple to avoid repetition in code when defining the list of devices.
	
  - Commands: It sends two commands to each device:
	
    1. ```'sh run | include hostname'```: Grabs the hostname from the running config.
		
	2. ```'sh version | section Cisco IOS XE Software, Version'```: Extracts the IOS XE version.
	
The ```.strip()``` method is used to remove any leading or trailing whitespace (including spaces, tabs, and newlines) from a string. In this loop, we're using ```.strip()``` on the outputs of two commands:

1. ```'sh run | include hostname'```: This command extracts the hostname from the router's configuration. The result might have some extra spaces or newlines around the hostname. Using ```.strip()``` ensures that only the hostname itself is stored in the variable without unnecessary whitespace.

2. ```'sh version | section Cisco IOS XE Software, Version'```: Similar to the hostname command, this extracts the version information. Again, ```.strip()``` cleans up any unwanted spaces or line breaks from the output, leaving only the essential information.

New Command: **pprint**

  - ```pprint.pprint()```: Pretty print is used to format the ```output_list``` in a more readable manner. Instead of printing the raw list, ```pprint``` neatly arranges the tuples of hostnames and IOS versions, which is especially useful when displaying complex data structures like lists of tuples.
	
This example is a practical showcase of using tuples to handle related data (like hostnames and versions) in an organized and immutable format. Also, the ```pprint``` module helps visualize that structure clearly.

## Experiment with Sets

*A set is another data type that contains a series of items. Python sets do not maintain order and cannot have duplicate values. Sets are written with curly brackets, similar to dictionaries, but they do not include key:value pairs, just objects. Sets are also mutable, so you can add or remove objects from a set. Sets help remove duplicate values from an existing sequence or perform operations such as union, intersection, difference, and symmetrical difference. The following is an example of a set of IP addresses:*

```
ip_set = {'10.254.0.1', '10.254.0.2', '10.254.0.3'}
```

*As stated above, sets are useful if you want to remove duplicate data from a list or to perform the union or intersection of two groups of data. A union is the joining of two sets, while an intersection defines what is common in the two sets. This example shows a union:*

```
>>> Router_1 = {"R1", "IOS-XE"}
>>> Router_2 = {"R2", "IOS-XE"}
>>> Router_1.union(Router_2)
{"R1", "R2", "IOS-XE"}
```

*In this union example, you combine the sets Router_1 and Router_2. When you combine sets, the values of both sets will be combined, but there will be no duplicate values. The second example shows an intersection:*

```
>>> Router_1 = {"R1", "IOS-XE"}
>>> Router_2 = {"R2", "IOS-XE"}
>>> Router_1.intersection(Router_2)
{'IOS-XE'}
```

*In this intersection example, you are looking for what is common in both sets. The intersection method can be useful if you have a list of devices with their corresponding operating systems, and, from that list, you wanted to know the different types of operating systems in the network without having to look at the entire list.*

### sets.py

```
import netmiko 
 
ip_addrs = [ 
    '10.254.0.1', 
    '10.254.0.2', 
    '10.254.0.1', 
    '10.254.0.3', 
    '10.254.0.2', 
    '10.254.0.3', 
    '10.254.0.3', 
    '10.254.0.2', 
    '10.254.0.3', 
]

ip_addrs_unique = set(ip_addrs)
print(sorted(ip_addrs_unique))
```

Here's a brief breakdown of this example:

1. List with duplicates: ```ip_addrs``` contains a list of IP addresses, but some of them are repeated multiple times.

2. Converting the list to a set: The ```set(ip_addrs)``` line converts the list into a set, which automatically removes all the duplicate entries. Sets can only hold unique values, so any repeated IPs are discarded.

3. Sorting the set: The ```sorted()``` function is used to take the unique set of IP addresses and return them in ascending (in this case, numerical) order. The ```sorted()``` function converts the set back into a sorted list, since sets themselves are unordered.

4. Output: The script prints the sorted list of unique IP addresses in ascending order. So we get rid of duplicates and organize them nicely!

## Experiment with Dictionaries

*A Python dictionary consists of an unordered series of key-value pairs separated by commas. Dictionaries can be used as a namespace for a series of named values. The key is usually a string that is descriptively named based on its value. You use the keys of a dictionary to access the values, such as how you use a variable's name to access its value. The following is a basic python dictionary:*

```
my_first_dictionary = { 

    'letter': 'a', 

    'number': 1, 

    'word': 'apple'

}
```

*Some characteristics of a dictionary are they are mutable, can grow and shrink as needed, and can be nested. To define a dictionary, you use curly braces ```{}``` to open and close the dictionary and the information inside the dictionary is represented by a key and value separated by a colon (```:```). A key can be any immutable object, such as a string, integer, float or Boolean, but it cannot be a list or another dictionary because they are mutable. The value of each key value pair is mutable, so it can be any object type.*

*Let's discuss how to access and modify a dictionary’s keys and values. To access or modify values, you use their keys. To access the value for the key "vendor", use the following command:*

```
>>> router["vendor"]
'Cisco'
```

*Using the dictionary name with the key inside square brackets (```[]```) will retrieve that key's value. If you use a key that is not in the dictionary, the dictionary will return a KeyError error. The following example shows how to add a new key:value pair to a dictionary:*

```
>>> router['OS'] = 'IOS-XE'
```

*Place the key you want to add inside the square brackets and the value of that key after the equal sign. Note that the new key:value pair ```'OS':'IOS-XE'``` was added to the end of the dictionary:*

```
{'vendor':'Cisco', 'DeviceID':'3800', 'Location':'San Jose', 'OS':'IOS-XE'}
```

*The last example shows how to change the value of a key:*

```
>>> router['Location'] = 'Dallas'
```

*This command is similar to adding a key:value pair except that it uses a key that already exists; therefore, it just changes the value:*

```
{'vendor':'Cisco', 'DeviceID':'3800', 'Location':'Dallas'}
```

### Common Dictionary Methods

*Let’s examine the methods you can use on dictionaries. Remember, methods are functions that are available for a given object.*

- ```.get()```: Retrieves the value of a given key. Recall the earlier KeyError when attempting to access the value of a key not in the dictionary. The get() method will return a value of ‘None’ instead of an error.

- ```.items()```: Returns the keys and values in a tuple form in a list

- ```.keys()```: Returns all the keys in a list format

- ```.values()```: Returns all the values in a list format

*The last dictionary methods you will cover are ```pop()```, ```update()``` and ```clear()```.*

- ```.pop()```: Removes a specified key from a dictionary and returns that key’s value. If the key is not found and no default value is given, a KeyError is raised.

- ```.update()```: Merges two dictionaries. In the example, dictionary switch1 is merged into switch. If a key in switch1 is not in switch, it will be created. If both dictionaries have the same key, the key value in switch will be updated to the new value. A dictionary cannot contain multiples of the same key.

- ```.clear()```: Clears the dictionary and makes it empty.

### dictionaries.py

```
import netmiko 

csr1kv1_connection_info = {
    'ip' : '10.254.0.1',
    'device_type' : 'cisco_ios',
    'username' : 'cisco',
    'password' : 'cisco',
    'port' : 22
}

# net_connect = netmiko.ConnectHandler( 
#     ip=csr1kv1_connection_info['ip'],  
#     device_type=csr1kv1_connection_info['device_type'], 
#     username=csr1kv1_connection_info['username'],  
#     password=csr1kv1_connection_info['password'],  
#     port=csr1kv1_connection_info['port']) 

net_connect = netmiko.ConnectHandler(**csr1kv1_connection_info)

print(net_connect.send_command('show run'))
```

Let's make another breakdown:

1. Dictionary for connection info: The script defines a dictionary ```csr1kv1_connection_info```, which contains all the necessary details (IP, device type, credentials, and port) for establishing a connection to a Cisco device using Netmiko. This dictionary holds key-value pairs, where the key represents the parameter name (like ip, device_type, etc.), and the value is the specific data for that connection.

2. Connection establishment:

  - Initially, the code commented out shows how you could individually pass these parameters to ```netmiko.ConnectHandler()```. Each argument (IP, device type, etc.) is manually passed one by one from the dictionary.
  
  - The important part is the line here:
  
```
net_connect = netmiko.ConnectHandler(**csr1kv1_connection_info)
```

  - Here, the ```**``` is dictionary unpacking. It essentially unpacks the dictionary and passes each key-value pair from ```csr1kv1_connection_info``` as individual arguments to the ```ConnectHandler``` function. This way, you don't need to type out each argument separately—it's a shortcut that makes the code cleaner and more flexible.

3. Sending a command:

After establishing the connection with ```net_connect```, the script runs a command ```show run``` on the remote device using the ```send_command()``` method. This retrieves the running configuration from the router or switch and prints it out.

**About ```**``` (dictionary unpacking):**

The ```**``` operator in Python is used to unpack dictionaries. It converts the keys of the dictionary into named arguments for a function. In this case, it converts:

```
'ip': '10.254.0.1',
'device_type': 'cisco_ios',
'username': 'cisco',
'password': 'cisco',
'port': 22
```

into:

```
ip='10.254.0.1', device_type='cisco_ios', username='cisco', password='cisco', port=22
```

making the code more concise and easier to read, especially when dealing with a lot of parameters.
