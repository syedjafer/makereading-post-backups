# 1D1C - echo

**echo** - display a line of text.

**1. ** $ ```echo "Welcome to Linux"```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663401839405/2aYIKeTh9.png align="left")

**2. ** To enable the interpretation of backslash escapes -e option 
 **\b** To removes all the spaces in between the text

$ ```echo -e "Welcome \bto \bLinux"```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663401928880/NlY8ZZ-k5.png align="left")

**3. ** \c To suppress trailing new line with backspace interpretor ‘-e‘ to continue without emitting new line.

$ ```echo -e "Welcome \cto Linux"```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663401986521/iTEzGwT4N.png align="left")


**4. ** \n To create new line from where it is used.

$ ```echo -e "Welcome \nto \nLinux"```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663402038029/-ij4sx9Dr.png align="left")

**5. ** \t To create horizontal tab spaces

$ ```echo -e "Welcome \tto \tLinux"```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663402079339/Xk_2KK8th.png align="left")

**6. ** \r To carriage return with backspace interpretor ‘-e‘ to have specified carriage return in output

$ ```echo -e "Welcome \rto Linux"```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663402126037/4imjB9HE3.png align="left")

**7. ** \v To create vertical tab spaces

$ ```echo -e "Welcome \vto \vLinux"```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663402170817/njO0_f7H2.png align="left")


**8. ** To print all files/folders

$ ```echo *```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663402237941/CHUj5cDyT.png align="left")
