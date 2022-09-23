## Consistent Hashing

### Prerequisite

Hashing and the need for consistent hashing

### Introduction
The **standard hashing algorithm** is inefficient while processing network queries. This traditional technique presupposes that we have a set number of servers and that all mapping locations are known in advance. This scenario is particularly troublesome in distributed systems when several users request multiple servers. **If some servers fail, then mapping the work to new servers involves a huge and intensive calculation**, which is wasteful and reduces the service's throughput while increasing the application's latency.

### Consistent Hashing

Consistent Hashing is a **distributed** **hashing** scheme that operates **independently of the number of servers or objects in a distributed hash table** by assigning them a position on an **abstract circle, or hash ring**. This allows servers and things to scale without affecting the overall system. So the hash table is independent of the number of servers available to minimize key relocation when scale changes occur.

### Assumptions for understanding the concept

1. We are considering 4 servers Server 0, Server 1, Server 2, and Server 3 with the hash value of 0, 90, 180, and 270 respectively.
2. We will be using 360 to find the position of the server in the ring. In the real world, it can be any number.

### Explanation



Consider a circle or a ring, which will have 360 deg. Now we can place the servers based on their hash value modulo 360.
So, 

- **Server 0** will be placed at hash(server 0) % 360 = 0 % 360 = 0
- **Server 1** will be placed at hash(server 1) % 360 = 90 % 360 = 90
- **Server 2** will be placed at hash(server 2) % 360 = 180 % 360 = 180
- **Server 3** will be placed at hash(server 3) % 360 = 270 % 360 = 270


Now the ring will look like this, 


![consistent hashing](https://cdn.hashnode.com/res/hashnode/image/upload/v1663148941294/qqtlVpUcX.png align="left")

#### Scenario 1 -> A Request coming in
Now considering a request R1 is coming, now we need to redirect this request to one of the available servers. The hash of the request R1 is 40. Visually we can see 40 is in between server 0 and server 1. (Technically we need to apply binary search). The next available server to 40 (hash of R1) is Server 1. So we can redirect this request to server 1. 



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663167409995/5PILHoCgV.png align="left")


Now considering a request R2 is coming, now we need to redirect this request to one of the available servers. The hash of the request R2 is 60. Visually we can see 60 is in between server 0 and server 1. (Technically we need to apply binary search). The next available server to 60 (hash of R2) is Server 1. So we can redirect this request to server 1. 


![consistent hashing](https://cdn.hashnode.com/res/hashnode/image/upload/v1663149061653/F-wjMJELR.png align="left")


#### Scenario 2 -> Adding a new Server

Now we are going to add a new server S4. Assume the hash value of this server S4 is 50, it will be placed in between S0 and S1. 


![consistent hashing](https://cdn.hashnode.com/res/hashnode/image/upload/v1663149161300/P-3G-WZw5.png align="left")

But we also need to check on one thing, (ie), in Scenario 1 we discussed about R1 (with the hash value of 40) is been placed in Server S1. Since we are going to introduce S4, the Request R1 (hash value of 40) needs to be placed in Server S4 - based on binary insertion. 


![consistent hashing](https://cdn.hashnode.com/res/hashnode/image/upload/v1663149224785/MGpbnb_Pv.png align="left")

Server 4 will need to query the next available server, whether any request less than the hash value is present. If it's present we need to move the data related to the request. 


![consistent hashing](https://cdn.hashnode.com/res/hashnode/image/upload/v1663149281038/onwWP6CKt.png align="left")

So this is how it goes, 

1. S4 will query S1, Do you have any requests with my range?
2. If there are any requests they would be shared from S1 to S4. 

After data transfer, 


![consistent hashing](https://cdn.hashnode.com/res/hashnode/image/upload/v1663149318500/zcbjj30PR.png align="left")

#### Scenario 3 -> Deleting a server. 

Currently, the hash ring with servers will look like this, 

![consistent hashing](https://cdn.hashnode.com/res/hashnode/image/upload/v1663149390475/airEc_v99.png align="left")

Server 1 is to be deleted and the contents of the server will be moved to the next available server; in our case it's S2. 

![consistent hashing](https://cdn.hashnode.com/res/hashnode/image/upload/v1663149488773/qQLml5juz.png align="left")

Now we can see the request details of R2 (with the hash value of 60) are present in the S1, So this value is to be moved to S2. 

After deletion, 

![consistent hashing](https://cdn.hashnode.com/res/hashnode/image/upload/v1663149547257/hjn9KqmhL.png align="left")


### Final Thoughts

This is how consistent hashing works at a basic level.  In this blog post, we haven't considered the scenarios of a server crash. That's a whole different topic. 

Subscribe to my [newsletter](https://makereading.com/newsletter). 







