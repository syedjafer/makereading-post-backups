# Need of Consistent Hashing

### Introduction

Have you ever thought of what is that ? when developers discuss like add a server; we need to scale up; we can scale down; implement a load balancer to equally share the request. In this blog post, we can go from basic methodologies in designing a solution where we equally distribute the request to the **n servers** in a distributed system. 

### What is Hash Function ?

A hash function is a function that maps one piece of data typically describing some kind of object, often of arbitrary size to another piece of data, typically an integer, known as **hash code**, or simply **hash**.


Lets create a simple hash function to take ip and give an integer back, 

```
def hash_the_value(value):
	value = value.replace(".", "")
	value = int(value)
	return value % 12 # This can be any constant number
	
sample_ips = [
	'192.168.0.18',
	'192.168.0.19',
	'192.168.3.38'
]
for sample_ip in sample_ips:
	hash_value = hash_the_value(sample_ip)
	print(sample_ip, hash_value)
```


![simple hash function](https://cdn.hashnode.com/res/hashnode/image/upload/v1663070532931/lKLQmxwVq.png align="left")


Till now, we have seen what is an hash function. Now let's see the problem. 

### Problem Description

Consider we are having our application installed in 4 servers. Now we want to split the requests between these 4 servers almost equally, so that every servers are equally loaded (more efficient). 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663070592870/tLif1MOIs.png align="left")



### Naive Solution
We need to split the request to different servers; so we need to have some distribution logic
We can define the distribution logic (Load Balancer) like below, 

Logic: <br>
> hash_of_ip = hash_the_value(ip) # our python function at top <br>
> total_server = 4 <br>
> server_no_to_hit = hash_of_ip % total_server <br>

Now let's see with a single request, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663070677699/bbRUdCkJZ.png align="left")

Now lets see with multiple requests, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663070759912/gADcvCeRe.png align="left")


### Problems

This seems to be solve the problem right. Do you see any problem here ?

- What will happen if i removed a server ?
- What will happen if i added one server ?

At both of the scenarios, our hash value for a particular will be changing which may lead to hoping to another server. Let's witness the change. 



### Adding a new server 

Initially we had 4 servers, now we add one more. So now totally we will have 5 servers. 


![adding a new server](https://cdn.hashnode.com/res/hashnode/image/upload/v1663070982348/NxuOnMtEC.png align="left")

#### IP: 192.168.0.18

<u>Previous</u>

total_server = 4<br>
hash_of_ip = 6<br>
server_to_hit = hash_of_ip % total_server = 6 % 4 = 2<br>

<u>After adding one server</u>

total_server = 5<br>
hash_of_ip = 6<br>
server_to_hit = hash_of_ip % total_server = 6 % 5 = 1<br>

It changed from **server 2** to **server 1**. 

#### IP: 192.168.0.19

<u>Previous</u>

total_server = 4<br>
hash_of_ip = 7<br>
server_to_hit = hash_of_ip % total_server = 7 % 4 = 3<br>

<u>After adding one server</u>

total_server = 5<br>
hash_of_ip = 7<br>
server_to_hit = hash_of_ip % total_server = 7 % 5 = 2<br>

It changed from **server 3** to **server 1**.

#### IP: 192.168.3.38

<u>Previous</u>

total_server = 4<br>
hash_of_ip = 2<br>
server_to_hit = hash_of_ip % total_server = 2 % 4 = 2<br>

<u>After adding one server</u>

total_server = 5<br>
hash_of_ip = 2<br>
server_to_hit = hash_of_ip % total_server = 2 % 5 = 2<br>

It remains same. 



### When simple hashing breaks 

- When we add or removed a server we need to do a lot of shuffling and data transfers. 
- The cost of shuffling the data is huge and its not efficient with auto scaling. 

### The Need of stable solution

Now we need to think about a hash algorithm which is consistent at almost all the time. So the birth of consistent hashing evolved. We will see more about consistent hashing in upcoming posts. 

