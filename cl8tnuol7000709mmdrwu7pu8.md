## Bash Script to categorize files into batches

Consider we are having this set of files, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1664701942301/cX9NAZy7g.png align="left")

```bash

#!/bin/sh
declare -A dictionary
FILES=`ls *.xml`
for FILE in ${FILES}
do
  IFS='_' read -r -a array <<< "$FILE"
  if [ ! -v dictionary[${array[1]}${array[3]}] ];
  then
    dictionary[${array[1]}${array[3]}]=$FILE
  else
    dictionary[${array[1]}${array[3]}]+=","$FILE
  fi
done

index=1
for key in "${!dictionary[@]}"; do
    echo "Batch $index - ${dictionary[$key]}"
    index=$(($index + 1))
done


```

**Output:**


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1664701998535/XXAyuGhVM.png align="left")
