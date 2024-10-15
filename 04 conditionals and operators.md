# Describing Conditionals and Operators

## Conditionals

*Control flow tools allow you to execute a line or multiple lines of code when specific criteria are met. The first line in your control structure is an expression that is evaluated for Boolean True or False. Suppose that the expression is evaluated to be True. In that case, the code inside the control structure is executed. If it is evaluated to be false, it skips the code inside and runs the following lines of code in your script.*

*The most basic type of control structure is an “if” statement. "If" statements evaluate an expression and execute the line or lines of code grouped under it if it is true. To write the first line of your if statement, you need the expression to be evaluated, followed by a colon (```:```). To group your lines of code that follow the expression, indent each statement by 4 spaces. Indentation is how Python groups code together.*

Example 1:

```
x = True
if x:
    print("x is True")
print("This code is outside the if")
```

And the output for this should be:

```
C:\PRNE>python if.py
x is True
This code is outside the if
```

Example 2:

```
x = False
if x:
    print("x is True")
print("This code is outside the if")
```

The output:

```
C:\PRNE>python if.py
This code is outside the if
```

*The shows how an if statement works. The first example shows how code is evaluated when a condition is True; the second example shows when the condition is False.*

*Looking at the first example, you will see that the variable x is set to True. The if statement evaluates x to determine if it is True. Since x is equal to True, the statement evaluates to True and the code inside the if statement is executed. The output below the code shows that both the code inside the if statement and outside the if statement ran.*

*The second example has x set to False. When the if statement is evaluated, the code inside the if statement doesn't run. Looking at the output, you will see that only the code outside the if statement ran.*

*The "if" statement by itself gives you one expression to evaluate and one path to take if the expression is True. What if you have multiple paths your script could take? In these cases, use the "else" or "elif" statements.*

*Let's first look at using else with the if statement. First, the if statement is evaluated and if it is True, it executes the block of code underneath it. If the expression evaluates to False, it skips to the else statement and runs the code block under it. This gives you two paths, one if the expression is True and one if the expression is False.*

*An elif statement can give you more than two paths to take. The "if" statement is evaluated first. If it is True, the code block under it is executed. If it is False, it goes to the first "elif" statement and evaluates it. If it is True, the code block under it is executed, and if it is False, it goes to the next "elif." When a conditional evaluates to True, no other statements will be evaluated. Therefore, it is important that you order your statements correctly for correct functioning of your code. If no elif statements evaluate to True, the statements under the "else" statement will execute.*

*An example of elif and else follows:*

Example 3:

```
x = False
y = True

if x:
    print("x is True")
elif y:
    print("y is True")
else:
    print("x and y are not True")
```

The output:

```
C:\PRNE>python if.py
y is True
```

Example 4:

```
x = False
y = False

if x:
    print("x is True")
elif y:
    print("y is True")
else:
    print("x and y are not True")
```

The output:

```
C:\PRNE>python if.py
x and y are not True
```

*In the example, there is an if statement that is evaluating x. If x is True, then the code will print "x as True." If x is False, it will evaluate the elif statement to see if y is True. If y is True, the code will print "y as True." If y is False, then the code under the else statement will run and print "x and y as not True."*

*The third example shows an example of when x = False and y = True. The output here is "y is True." The fourth example is an example of when x = False and y = False. The output here is "x and y are not True."*

## Operators

*Operators are special symbols in Python that are used to perform operations on variables and values. These variables and values are also known as operands. Operators are divided into the following groups:*

- Arithmetic

- Assignment

- Comparison

- Logical

- Identity

- Membership

### Arithmetic Operators

*Arithmetic operators include addition, subtraction, multiplication, division, and exponentiation.*

![Arithmetic Operators](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/arithmetic_operators.png)

*The addition operator gives you the sum of two operands. The example adds x and y together. The “+” is the operator, and “x” and “y” are the operands. Adding these operands together will give you the output of 15 when x = 10 and y = 5. Not only can you add variables together, but you can also add variables and numbers if the variable is an integer, float, or Boolean. An example of adding a variable to a float follows.*

```
>>> x = 5.5
>>> y = x + 10
>>> print(y)
15.5
```

*The subtraction operator (```-```) subtracts two operands. The subtraction operator can subtract variables or numbers from variables if the variable is an integer, float, or Boolean. The example is subtracting two variables, x and y. When x = 10 and y = 5, the output will be 5.*

*The multiplication operator (```*```) is used to multiply two operands. The multiplication operator can multiply variables or a number and a variable if the variable is an integer, float, or Boolean. The example shows the multiplication of two variables, x and y, where x = 10 and y = 5. The output for this multiplication will be 50.*

*The division operator (```/```) is used to divide two operands. The division operator can divide variables or a number and a variable if the variable is an integer, float, or Boolean. The example shows the division of two variables, x and y, where x = 10 and y = 5. The output for this will be 2.*

*The exponential operator (```**```) is used to raise one operand to the power of the other. The exponential operator can use variables or a number and a variable if the variable is an integer, float, or Boolean. The operand on the right side of the operator is the power. The example shows raising x by the power of y. When x = 10 and y = 5, the output will be 100000.*

*The modulo operator (```%```) returns the remainder of dividing the left-hand operand by the right-hand operand. The example will return the remainder when x is divided by y. If x = 11 and y = 5, the remainder will be 1.*

Note: To calculate the remainder using the modulo operator (```%```), we divide the left operand by the right operand and then determine what remains after subtracting the largest possible multiple of the divisor from the dividend. Here's a breakdown of our example with x = 11 and y = 5:

1. Divide x by y:

```
11 ÷ 5 = 2.2
```

2. Multiply the integer part by y:

```
2 × 5 = 10
```

3. Subtract this result from x:

```
11 − 10 = 1
```

So, the remainder when 11 is divided by 5 is 1. Thus, ```11 % 5 = 1```.

*The floor division operator (```//```) returns the smallest possible integer after dividing the left-hand operand by the right-hand operand. The example above will return the quotient (whole number) when x is divided by y. If x = 11 and y = 5, you will get a result of 2. In the example above where x = 11 and y = 5, the result of dividing x by y would be 2.2 but the floor would be 2 because it is the smallest possible integer from the result 2.2. Let’s look at performing floor division on a negative number. If x = -11 and y = 5 the result if you divide x by y would be -2.2, but the floor would be -3 because it is the smallest integer from the result.*

## Assignment Operators

*Assignment operators are used to assign values to variables.*

![Assigment Operators](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/assigment_operators.png)

*The most common assignment operator is the equal sign (```=```). The equal is used to assign a value or expression on the right side to the operand on the left. You will use this throughout your coding for assignments to variables.*

*Besides the equal operator, there are augmented assignment operators. Augmented assignment operators perform some arithmetic operation on the left side variable and then reassign the results to the variable. The arithmetic operators that can be used are as follows.*

- ```+=```: *Adds the operand on the right with the operand on the left.*

- ```-=```: *Subtracts the operand on the right from the operand on the left.*

- ```*=```: *Multiplies the operand on the left with the operand on the right and assigns it to the operand on the left.*

- ```/=```: *Divides the operand on the left by the operand on the right.*

- ``` %=```: *Returns the remainder of dividing the left-hand operand by right-hand operand. The remainder is then assigned to the left operand.*

- ```//=```: *Divides the left operand by the right operand and returns the integer and assigns it to the left operand.*

- ```**=```: *Raises the operand on the left to the power of the operand on the right. The result is assigned to the operand on the left.*

## Comparison Operators

*Comparison operators are used to compare values and return either a Boolean True or False.*

![Comparison Operators](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/comparison_operators.png)

*Comparison operators determine if the operand on the left side and the operand on the right side are equal, not equal, greater than, less than, greater than or equal to, or less than or equal to each other.*

- **Equal**: *The equal operator (```==```) checks to see if the operands on the left and right sides are the same. If they are the same, the result will be True; if they are not equal, the result will be False. The example determines if x is equal to y. Since x = 5 and y = 3, the result will be False. Note that to check if two values are equal, you don’t use one equal (```=```) but two (```==```).*

- **Not Equal**: *The not equal operator (```!=```) checks to see if the operand on the left and right sides are different. If they are different, the result will be True, but if they are the same, the result will be False. The example determines if x is not equal to y. Since x = 5 and y = 3, the result will be True.*

- **Greater Than**: *The greater than operator (```>```) checks to see if the operand on the left side is greater than the operator on the right side; if it is, the result will be True; otherwise, the result will be False. The example checks to see if x is greater than y. Since x = 5 and y = 3, the result will be True.*

- **Less Than**: *The less than operator (```<```) checks to see if the operand on the left side of the operator is less than the operand on the right. If it is less, the result will be True; otherwise, the result will be False. The example checks if x is less than y. Since x = 5 and y = 3, the result will be False.*

- **Greater Than or Equal To**: *The greater than or equal to operator (```>=```) checks to see if the operand on the left side of the operator is greater than or equal to the operand on the right. The example checks to see if x is greater than or equal to y. Since x = 5 and y = 3, the result will be True.*

- **Less Than or Equal To**: *The less than or equal to operator (```<=```) checks to see if the operand on the left side of the operator is less than or equal to the operand on the right. The example checks to see if the operand on the left side of the operator is less than or equal to y. Since x = 5 and y = 3, the result will be False.*

## Logical Operators

*Logical operators are “and,” “or,” and “not” and return a Boolean True or False once the expression is evaluated.*

![Logical Operators](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/logical_operators.png)

*The meaning of each logical operator follows.*

- **and**: *If the operands on both the left and right sides of the logical operator are True, the result will be True, but if either or both are False, the result will be False. In the example, x is equal to 4; therefore, the operand on the left side (x >3) is True, but the operand on the right side (x>6) is False. Since both are not True, the result will be False.*

- **or**: *If either the operand on the left or the right side of the logical or operator is True, the result will be True. In the example, x is equal to 4; therefore, the operand on the left side is True, and the operand on the right side is False. Since one of the two operands is True, the result will be True.*

- **not**: *The logical operator not will return the opposite of a Boolean value. In the example above, the expression x > 3 or x >6 is evaluated when x = 4. The result of this expression is True, however if you use the not operator, the result will be False.*

## Identity Operators

*Identity operators check to see if two values are located in the same part of memory.*

*Identity operators are not looking to see if the two variables have the same value but if the two variables point to the same memory location. Let’s take a closer look at the identity operators is and is not.*

![Identity Operators](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/identity_operators.png)

*The identity operator is looks to see if two variables point to the same memory location. The example has three variables x, y, and z. Even though x and y have similar lists, they are in different memory locations. Z has the same memory location as x because z = x. When using the is operator, x is z is true because both z and x point to the same memory location. However, x is y is False because they point to different memory locations.*

*The identity operator does not look to see if two variables are not located at the same memory location. Looking at the same example, x is not z would be False because x and z are located at the same memory location. However, x is not y and would be True because they are not located at the same memory location.*

## Membership Operators

*Membership operators check to see if a variable or value is found in a string, list, tuple, set, or dictionary.*

![Membership Operators](https://raw.githubusercontent.com/PurityControl7/PRNE/refs/heads/root/images/membership_operators.png)

*The in membership operator checks to see if a variable is found inside a string, list, tuple, set, or dictionary. The example checks to see if router1 is in the list x. If it is found in list x, it will return a Boolean value of True. If the variable had not been found in the list, the Boolean value of False would have been returned.*

*The not in membership operator is checking to see if a variable is not in a string, list, tuple, set, or dictionary. The example checks to see if router3 is in list x. If it is not found in list x, the Boolean value of True is returned. If it had been found in the list, the Boolean value of False would have been returned.*

## Use the if-else Construct

*Conditional statements are how you can control the flow of a script based on a Boolean value. The statements that make up an if-else block are if, elif, and else. Beginning on the following line of code, there should be an indented block of code that will run if the condition evaluates to True. In this discovery, you will use the if-else construct to control the flow of a script.*

### conditionals.py

Here is the preview of the entire script before delving into specifics:

```
ip = '192.168.0.1'
subnet = '255.255.255.252'

if subnet.endswith('.0'):
    subnet_slash_notation = '/24'
#     print(ip + subnet_slash_notation)
elif subnet.endswith('.128'):
    subnet_slash_notation = '/25'
elif subnet.endswith('.192'):
    subnet_slash_notation = '/26'
elif subnet.endswith('.224'):
    subnet_slash_notation = '/27'
elif subnet.endswith('.240'):
    subnet_slash_notation = '/28'
elif subnet.endswith('.248'):
    subnet_slash_notation = '/29'
elif subnet.endswith('.252'):
    subnet_slash_notation = '/30'
elif subnet.endswith('.255'):
    subnet_slash_notation = '/32'
else:
    print('Subnet slash notation could not be determined.')

print(ip + subnet_slash_notation)
```

### Create a Simple Conditional Block Using if and else

```
ip = '192.168.0.1'
subnet = '255.255.255.0'

if subnet.endswith('.0'):
    subnet_slash_notation = '/24'
    print(ip + subnet_slash_notation)
else:
    print('Subnet slash notation could not be determined.')

```

The Breakdown:

1. Variables Declaration:

  - ```ip = '192.168.0.1'```: This is assigning the IP address ```'192.168.0.1'``` to the variable ```ip```.
  
  - ```subnet = '255.255.255.0'```: Here, the subnet mask ```'255.255.255.0'``` is assigned to the variable ```subnet```.
  
2. The Conditional Block:

  - ```if subnet.endswith('.0'):```: This is the **if-statement**. The function ```.endswith()``` checks if the string stored in ```subnet``` ends with the string ```'.0'```. If this condition is true, the code inside the if block will be executed.
  
3. If the condition is true:

  - ```subnet_slash_notation = '/24'```: If the subnet ends with ```'.0'```, it assigns the string ```'/24'``` to ```subnet_slash_notation```.
  
  - ```print(ip + subnet_slash_notation)```: It then concatenates the ```ip``` variable and the ```subnet_slash_notation``` (so something like ```'192.168.0.1/24'```) and prints it.
  
4. Else Block:

  - ```else:```: If the **if-statement** is not true (i.e., the subnet does not end with ```'.0'```), the code in this block will run.
  
  - ```print('Subnet slash notation could not be determined.')```: It prints a message that the slash notation could not be determined.
  
The Core:

The key here is the **if-else** block that checks if the subnet ends with ```'.0'```. Depending on that, it either appends the slash notation ```'/24'``` to the IP and prints it, or it prints the message saying it couldn't determine the slash notation.

### Create a Simple Conditional Block Using if, elif, and else Statements

```
ip = '192.168.0.1'
subnet = '255.255.255.252'

if subnet.endswith('.0'):
    subnet_slash_notation = '/24'
#     print(ip + subnet_slash_notation)
elif subnet.endswith('.128'):
    subnet_slash_notation = '/25'
elif subnet.endswith('.192'):
    subnet_slash_notation = '/26'
elif subnet.endswith('.224'):
    subnet_slash_notation = '/27'
elif subnet.endswith('.240'):
    subnet_slash_notation = '/28'
elif subnet.endswith('.248'):
    subnet_slash_notation = '/29'
elif subnet.endswith('.252'):
    subnet_slash_notation = '/30'
elif subnet.endswith('.255'):
    subnet_slash_notation = '/32'
else:
    print('Subnet slash notation could not be determined.')

print(ip + subnet_slash_notation)
```

Breakdown:

- Conditional Block Structure:

  - The script checks the ```subnet``` value by examining its last portion using ```.endswith()``` and applies the appropriate slash notation-
  
  - The ```if``` block checks if the subnet ends with ```.0``` and assigns ```/24``` to ```subnet_slash_notation``` if true.
  
  - If the first condition is false, the script proceeds to the series of ```elif``` statements, checking for other subnet endings like ```.128```, ```.192```, etc., and assigns the corresponding slash notation.
  
- Flow Control:

  - If none of the conditions in the ```if``` or ```elif``` blocks match, the else block executes, printing *"Subnet slash notation could not be determined."*
  
  - This ensures that something happens regardless of which conditions are met, providing a fallback if no subnet pattern is recognized.
  
Final Output:

  - After the conditions are checked and the correct slash notation is set, the script prints the IP address concatenated with the ```subnet_slash_notation```.
  
In this specific case, since the ```subnet``` ends with ```.252```, the script will assign ```/30``` and print:

```
192.168.0.1/30
```
