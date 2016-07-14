# Control Flow

You can consider any program as series of instructions.

But with control flow, the program can choose order of instructions to run.

It is a good idea to think about control flow as making decisions(flow control statements) with information that you have.

Due to the fact that Boolean has only two values:True and False. They come  handy to make decisions in instructions.

The Boolean expressions could be considered conditions. Conditions always evaluate down to a Boolean value.

A flow control statement decides what to do based on whether its condition is True or False.

Also it's important to note that any lines of code can be grouped in blocks.

Python implements idea of block through the indentation of the lines of code.

You need to be consistent with your style of indentation.

***
Flow Control Statements is shown below and they are the actual decisions your programs can make.

Before we dive in to structure and logic of every control flow statement it is important to note that any code has equal to some plain English sentence.

If you can make some plain simple statement in English you probably just can translate it to code.

*if else elif*

Plain English : "If condition is true, execute the code in the block".
```python
z = 5
if z == 5:
    s = "Python Code"
    print (s)
```
It says that if variable z equal to 5, print s variable whatever it has.

Be careful to the colon and indentation style.

Also, an **if** condition can be followed by an **elif** and **else** statement.

**elif** means an additional condition, **else** means if no our conditions are not satisfied, do this.

Let's look to our example:

```python

print ("who are you?")
name = input()
if name =="jon snow":
  print('the north remembers!')
elif name =="ramsy bolton":
  print('what do you want bastard?')
else:
  print('I don know who you are. You can go home')

```

*while*

If you do our previous code , you can noticed that code executed only once. So what if you want to execute some code many times. In this case you need **while** clause.

In plain English it means, till something is true(some expression) do this staff(block of code).

Let's rewrite our previous code and you easily noticed difference.

```python
name = ""
while name != "tirion":

   print ("who are you?")
   name = input()
   if name =="jon snow":
       print('the north remembers!')
   elif name =="ramsy bolton":
       print('what do you want bastard?')
   else:
      print('I don know who you are. You can go home')
```

If it is difficult , I can show you more simple example, but idea behind the code is same.
```python
hello = 0
while hello < 4:
  print ("Hello")
  hello = hello + 1
```

In both examples, you need to care about not only True statements, but also take care of case about False or you code will execute forever.

Or you can use **break** Statements

This statement automatically done executing flow statement.

Let's think we ask a secret number from you to enter the home. You have infinite number to try till you are right.

```python
while True:
  print("Type your access code.")
  password = input()
  if password == "777":
    break
print("Welcome to home")
```

If you run the code above you can notice that you loop done automatically, what exactly we want.

But if we want to have some additional checking for our circumstance, in this case come in hande **continue Statements**
Difference between "break" and "continue" is that "continue" statements jump flow of code to the begining of the loop.

Let's consider our next example and everything become clear.

```python
while True:
  print ("Who are you?")
  name = input()
  if name != "Arya Stark":
    continue  
  print("What is the password?")
  password = input()
  if password == "volar morgulis":
    break
print("Welcome to Bravos")
```
Notice the difference in **if statement** we use counter logic, we continue to ask for name for any wrong case, but if user input right name he goes to the next section of the code. **contunie**  allow you to continue executing the loop code, **break** statement stop your code at all.

*for*

We use **for** loops with **range** method when we know how many times we want to execute our specific block of code.

```python
for num in range(5):
    print(num)
```
If you run this code, you notice that our code executes 5 times, but started through 0 to 4.
And word **num** works as alias for every number in range between 0 and 5, except last one.

Power is **for..in** structure is that it can be used almost in any type of same structure like list, string, set and dictionaries.
You just need to make alias to every object and can use it as regular variable in your block of code in loop.


```python

s = "Python Code"
for letter in s:
    print (letter)
```

*range argements*
Range() can be passed with different arguments, which indicate your desires to your script. You can pass specific **starting**, **stoping** and **step** arguments to range.

Example makes things clear. For example we look for even number from 0 to 100, we can easily obtain all of this number with 2 lines
```python
for i in range(0, 100, 2):
    print(i)
```
Also we can make pass negatives numbers which make our printing statement reversed.
```python
for i in range(100, -1, -2):
    print(i)
```
***
In conclusion, with properly using flow control statements you can implement any ideas in your code, all things will be depenednt on your imagination.
