# 4 Ways to Center that <div/>

### 1. Using Flex Box

```javascript
.parent {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

### 2. Using Margin

```javascript
.child {
    margin: auto;
}
```


### 3. Using Grid

```javascript
.parent {
   display: grid;
   place-content: center;
}
```


### 4. Using Positions

```javascript
.parent {
    position: relative;
}

.child {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate (-50%, -50%);
}
``` 