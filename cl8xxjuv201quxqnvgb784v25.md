# setInterval in Javascript

### What is javascript setInterval ?

The setInterval() method in Javascript is used to repeat a specified function at every given time interval. It evaluates an expression or calls a function at a given interval. This method continues calling the function until the window is closed or the clearInterval() method is called. 

The setInterval() method calls a function at specified intervals (milliseconds). The setInterval() method continues calling the function until clearInterval() is called, or the window is closed. 


### What is setInterval function ?

The setInterval() function is commonly used to set a delay for functions that need to be executed again and again. You can cancel the interval using clearInterval(). If you wish to have your function called once after the specified delay, use setTimeout(). 

setTimeout is a commonly used function in javascript. It sets a timer ( a countdown set in milliseconds) for the execution of a callback function, calling the function upon completion of the timer. 

```javascript
setInterval(function, milliseconds);
```
Its parameters are:
1. **function** - a function containing a block of code.
2. **milliseconds** - the time interval between the execution. (1 second = 1000 milliseconds)

### Example: Display a text once every 1 second

```
function greet() {
  console.log("Hello Makereading");
}
setInterval(greet, 1000);

```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665110744094/PVHskhH0a.png align="left")

In the above program, the setInterval() method calls the greet() function every 1000 milliseconds (1 second). Hence the program displays the text "Hello Makereading" once every 1 1 second. 

