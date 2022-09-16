## 1D1C - bunzip2

**bunzip2** - a block-sorting file compressor

### 1. To compress file input.txt it deletes original

$ ```bzip2 -z input.txt```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662819371685/AKb0fk2HG.png align="left")

will give **input.txt.bz2** (Refer image).

### 2. To decompress the **input.txt.bz2**

$ ```bzip2 -d input.txt.bz2```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662819541275/I2f1OIsWk.png align="left")

### 3. To compress file input.txt but does not deletes the original file.

$ ```bzip2 -k input.txt```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662819600750/YD3oaX-AR.png align="left")

### 4. To check the integrity of file and to check file is corrupt or not

$ ```bzip2 -t input.txt.bz2```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662819871678/CEtuwp4WB.png align="left")

### 5. To show the compression ratio for each file processed in verbose mode

$ ```bzip2 -v input.txt```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662819832892/wxEPZ21vN.png align="left")

