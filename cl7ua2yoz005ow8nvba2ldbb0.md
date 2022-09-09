## 1D1C - dig

**dig** - DNS lookup utility

### To perform a DNS lookup
- $ ```dig ilugc.in```
![dig ilugc.in](https://cdn.hashnode.com/res/hashnode/image/upload/v1662457532329/9SLrSSTul.png align="left")


- $ ```dig @8.8.8.8 google.com```
![dig ilugc.in](https://cdn.hashnode.com/res/hashnode/image/upload/v1662457557138/TtjHCyqNz.png align="left")

### To display only the IP address associated with the domain name
- $ ```dig google.com +short```

![dig google.com +short](https://cdn.hashnode.com/res/hashnode/image/upload/v1662457894642/_5Z9lYiGV.png align="left")

- $ ```dig ilugc.in +short```

![dig ilugc.in +short](https://cdn.hashnode.com/res/hashnode/image/upload/v1662457914185/XwxYgvW6g.png align="left")

### The +trace option lists each different server the query goes through to its final destination
- $ ```dig google.com +trace```

![dig google.com +trace](https://cdn.hashnode.com/res/hashnode/image/upload/v1662458019266/gTTF9osCF.png align="left")

### To look up a domain name by its IP address

- $ ```dig -x 8.8.8.8```
![dig -x 8.8.8.8](https://cdn.hashnode.com/res/hashnode/image/upload/v1662458193851/tL5iJk_UB.png align="left")

### Batch Mode for Reading Host Names From a File store domain names in **domain.txt** and give input to dig command

- $ ```dig -f domain.txt +short```


![dig -f domain.txt +short](https://cdn.hashnode.com/res/hashnode/image/upload/v1662458317015/27JmH1QaP.png align="left")

Credits: tkdhanasekar@gmail.com
