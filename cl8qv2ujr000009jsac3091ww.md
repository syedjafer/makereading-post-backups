## Type any in Typescript

### Introduction

In this blog, we will learn about **any** type in TypeScript. The **any** type is TypeScript allows us to assign a value of any type to a variable. This means, with **any** type, a type of a variable's value can be changed.

### When to use **any** type ?

There are some cases where **strict type checking** may not be an ideal option. When you want to store a value in a variable but do not know the type at the time of writing the program. For example, the variable with the unknown type may come from user input or from a third-party library or API.

The syntax for assigning any type in TypeScript is as follows.

```typescript
let newVariable: any = "text value";
newVariable = 23;
```

Ordinarily, we can't change the type of a variable in TypeScript. However, with the assignment of ```any``` type, it is possible to update the value of **newVariable** from **someValue** which is a string to ```23```   which is a number.

With ```any``` type, ```newVariable``` is essentially working like a variable declared in Javascript.

### Conclusion

Using ```any``` type in TypeScript indicates to the compiler to skip type checking on the particular variable. It is appropriate for situations when you aren't sure of what type to expect, for example, user input or data from a third-party library or API.

