## 1D1C - HOST

**host** - DNS lookup utility used for performing DNS lookups. It is normally used to convert names to IP addresses and vice versa


**1. **To print the IP address details of the specified domain

$ ```host makereading.com```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663676637193/4yTigc9rG.png align="left")

**2. **To display the domain details of the specified IP Address

$ ```host 8.8.8.8```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663676694275/mb-Xj6uWy.png align="left")

**3. **To specify the query type or enables the verbose output

$ ```host -a makereading.com```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663676737307/Yr6S4n-3o.png align="left")

**4. ** To specify the type of query

$ ```host -t ns makereading.com```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663676773974/nP_MIm6Ag.png align="left")

**5. **To print SOA record

$ ```host -t SOA makereading.com```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663676810873/Ps00Lf3cC.png align="left")

**6. **To print txt record

$ ```host -t txt google.com```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663676868790/rtwd06bBB.png align="left")

**7. **To compare the SOA records on authoritative nameservers

$ ``` host -t SOA makereading.com```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663676908379/wOwDIVtBA.png align="left")

**8. **To specify the number of retries you can do in case one try fails

$ ```host -R 3 makereading.com```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663676942133/f2dzqzutX.png align="left")
