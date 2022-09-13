## Write minimalistic  Javascript Code - Part I

### Introduction

During our development, we might be doing some traditionally followed coding styles for some day-to-day development. In this blog post you will learn some cool minimal javascript code that could enhance you development. 

### 1. Boolean Casting (double not !!)

It converts **Object** to **boolean**. If it was falsey (e.g., 0, null, undefined, etc.), it would be **false**, otherwise, **true**.

```
!object  // Inverted Boolean
!!object // Non inverted Boolean, so true Boolean representation
```
So ```!!``` is not an operator; it's just the ```!``` operator twice.

#### Old

```javascript
const age = Boolean(input.value)
```

#### New 

```javascript
const age = !!input.value
```

![!! operator](https://cdn.hashnode.com/res/hashnode/image/upload/v1662616947377/k4ML17ZWp.png align="left")

Using this would be nicer if you are familiar with this concept and want to keep things minimal. 

### 2. Nullish Coalescing

Returns its **right-hand** side when its **left-hand** side operand is **null or undefined**. 

### Old 

```javascript
const user = { id: '' };
const addId = (user, id) => {
        user.id = id !== null && id !== undefined ? id : "Unknown";
        return user;
}
console.log(addId(user, null))
```
**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662617143858/O-NlDGuCc.png align="left")

This method is having some complexities to maintain (in the checking of whether the value is null or undefined. ). Also it's not clean. 

### New 

```javascript
const user = { id: '' };
const addId = (user, id) => {
  user.id = id ?? "Unknown";
  return user;
}
console.log(addId(user, null));
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662617302179/FYC-oRWwb.png align="left")

The above method is more cleaner than old way. 

### 3. Optional Chaining

Allows you to read the value of a deeply nested property without checking if it's a valid chain. 

#### Old
```javascript
const hasValidPostcode = u => {
          return u &&
          u.address &&
          u.address.postcode &&
          u.address.postcode.valid;}
const addressData = {
       address: {
                  postcode : {
                              valid: false
                  }
        }
}
console.log(hasValidPostcode(addressData));
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662617814561/UZ7M_OV35.png align="left")

#### New

```javascript
const hasValidPostcode = u => {return u?.address?.postcode?.valid;}
const addressData = {
       address: {
                  postcode : {
                              valid: false
                  }
        }
}
console.log(hasValidPostcode(addressData));
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662617923858/uwiOhfv7v.png align="left")

### 4. Default Parameters
Function parameters defaul to undefined, so it's useful to set a value for this eventuality. 

#### Old
```javascript
const createUser = (name, email) => {
        const user = {
                email,
                name: name ?? "Unknown",
        }
console.log(user);
//create user
}
console.log(createUser(null, 'contact.syedjafer@gmail.com'));
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662618205664/9jmmczmFs.png align="left")

#### New

```javascript
const createUser = ( name = "Unknown", email ) => {
  const user = {email, name};
  console.log(user);
  //create user
}
console.log(createUser(null, 'contact.syedjafer@gmail.com'));
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662618366225/40hjVcd8b.png align="left")


### 5. Destructuring Objects

Write less code by unpacking properties from objects into distinct variables. 

#### Old
```javascript
const params = {
  name: 'syedjafer',
  email: 'contact.syedjafer@gmail.com',
  dob:'16-08-1997'
}
const save = params => {
  console.log(params.name, params.email, params.dob);
  // some save functionality
}
save(params);
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662618566217/-VdxNEKGg.png align="left")

#### New
```javascript
const params = {
  name: 'syedjafer',
  email: 'contact.syedjafer@gmail.com',
  dob:'16-08-1997'
}
const save = ({name, email, dob}) => {
  console.log(name, email, dob);
  // some save functionality
}
save(params);
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662618634154/6QtWOqkKM.png align="left")

### 6. Destructuring Arrays

Write less code by unpacking values from arrays into distinct variables. 

#### Old
```javascript
const data = [
  ["rice", "Rs. 49/Kg"],
  ["wheat", "Rs. 35/Kg"]
];

const riceDetails = data[0];
const wheatDetails = data[1];
console.log(riceDetails, wheatDetails);
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662618951770/6_Mzqxlm7.png align="left")

#### New

```javascript
const data = [
  ["rice", "Rs. 49/Kg"],
  ["wheat", "Rs. 35/Kg"]
];

const [riceDetails, wheatDetails] = data;
console.log(riceDetails, wheatDetails);
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662619028350/v5rNW_FtS.png align="left")

### 7. Spread Operator

Merge two objects into one using this cool syntax, also very clean when cloning objects.

#### Old
```javascript
const details = { name: "Man Utd" };
const stats = { games: 7, points: 2};
const team = Object.assign(
  {},
  details,
  stats
};
console.log(team);
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662619193713/bMhdxVimr.png align="left")

#### New
```javascript
const details = { name: "Man Utd" };
const stats = { games: 7, points: 2};
const team = {
      ...details,
      ...stats
}
console.log(team);
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662619270108/7Iwn8hucD.png align="left")

### 8. For (of)

Arguably the same amount of code required but for(of) is know to be more faster than forEach (likely more than 20% faster).

#### Old
```javascript
const items = ['one', 'two', 'three', 'four', 'five', 'six'];
const array = [];
const fillArray = items => {
  items.forEach(item => array.push(item));
}
fillArray(items);
console.log(array);
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662619563054/u10vFst1X.png align="left")

#### New

```javascript
const items = ['one', 'two', 'three', 'four', 'five', 'six'];
const array = [];
const fillArray = items => {
  for (let item of items) {
    array.push(item);
  }
};
fillArray(items);
console.log(array);
```

**tryout:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662619667624/YXxdQTcL0.png align="left")


### Final Thoughts

These process will be helpful in writing clean code. My favourite minimalistic code is **Null Coalescing**. But some of the other process are arguable. It's not about right or wrong. It's about readbility and maintainability of the code. if you are feel some of the above process might hinder the readbility, please avoid it. 

We will see more comprehensions and optimizations in the upcoming posts. **[Subscribe](https://syedjaferk.hashnode.dev/newsletter)** to my newsletter **to not miss the blog. **