## 1D1C - cksum

**cksum** - checksum and count the bytes in a file.

cksum command in Linux is used to display a cyclic redundancy check (CRC) value. CRC is unique for each file and only changes if the file is edited

$ ```cksum package.json```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663493096074/BkQmAzAom.png align="left")

after transfer of package.json to other device or location, we can confirm with with cksum

$ ```cksum package.json```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663493096074/BkQmAzAom.png align="left")

CRC value is same hence the file is not corrupted or edited
