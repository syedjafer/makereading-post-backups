# Just - A Simple Command Runner

### Introduction

**Just** is a handy way to save and run project-specific commands. Commands are stored in a file called justfile or Justfile with syntax inspired by make:


- Official Website: https://just.systems/
- Official Documentation: https://just.systems/man/en
- Git Reposity: https://github.com/casey/just
- Examples: https://github.com/casey/just/tree/master/examples

### How it works: 

1. We just need to create a file named ```justfile``` or ```JustFile```. 
2. Then we need to add command(s) in a groupwise manner under a name, as given below.

```
hello: # <- Group Name
    # List of commands to be executed in order.
    echo "Hello !"
    echo "This will be executed next"
```
3. Execute the file using ```just```.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662877192733/wmHjpq7yH.png align="left")

### Some cool features

**1.** We can have a default group, which would be executed when we aren't specifying the group name. 

```
default:
    echo "Default !!"

hello: # <- Group Name
    # List of commands to be executed in order.
    echo "Hello !"
    echo "This will be executed next"

```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662877609391/aQR0677Ev.png align="left")

**2.** Each group is called as recipe's. We can have multiple recipe's name in the default recipe to execute them in order. 

```
default: hello greet


hello: # <- Group Name
    # List of commands to be executed in order.
    echo "Hello !"
    echo "This will be excuted next"

greet:
    echo "Hi How are you"

```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662877800430/6qYf88gKN.png align="left")

**3.** We can also use **[dotenv](https://just.systems/man/en/chapter_24.html#dotenv-load)** files with justfile. 

<u>.env</u>
```
# a comment, will be ignored
POSTGRES=localhost:6379
PORT=5004
```

<u>justfile</u>
```
set dotenv-load

serve:
    echo "Starting the server with database $POSTGRES on port $PORT"
```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662878283203/b_Rygexzz.png align="left")

**4.** Usually when an error happens in a sequence of commands, the next commands will not run. But with justfile we can ignore the errors using hypen as  a prefix (```-cat```).

```
foo:
    -cat foo
    echo "Done"
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662878474156/xW7VfCDdP.png align="left")

**5.** We can also use [conditional expressions](https://just.systems/man/en/chapter_32.html) with just. 
**6.** Changing variable values from [command line](https://just.systems/man/en/chapter_34.html) itself. 
**7.** Remember that each line will be executed in a fresh shell, so if you are changing directory in a line, it won't affect the other line. 
**8.** By using @ symbol it won't echo the commands that we wrote. 

```
hello:
    @echo "Done"

```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662879172071/FffEu6zhU.png align="left")

Checkout this [link](https://just.systems/man/en/chapter_20.html) for more features. Hope you liked it. 