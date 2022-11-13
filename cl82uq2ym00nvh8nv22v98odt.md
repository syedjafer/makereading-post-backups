# 1D1C - groupadd

**groupadd** - create a new group.

### 1. To create a new Linux group.

$ ```sudo groupadd webadmin```

### 2. To check

$ ```sudo grep webadmin /etc/group```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662818346559/5ZXCHQ_0U.png align="left")

### 3. To Create new group with a specific groupid

$ ```sudo groupadd webadmin2 -g 1030```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662818495552/8Euh0_FhX.png align="left")

### 4. To check

$ ```sudo grep 1030 /etc/group```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662818551612/6JRyuoQAH.png align="left")

### 5. To create group with group id with certain range of id

$ ```sudo groupadd webadmin3 -K GID_MIN=1500 -K GID_MAX=2000```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662818648322/zdADZi0uY.png align="left")
