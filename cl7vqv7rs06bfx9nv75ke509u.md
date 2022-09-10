## 1D1C - date

**date** - print or set the system date and time

### 1. date command displays the current date and time
$ ```date```
![date](https://cdn.hashnode.com/res/hashnode/image/upload/v1662458564478/V-b1MVDN1.png align="left")

### 2. To display the time in GMT/UTC time zone
$ ```date -u```

![date -u](https://cdn.hashnode.com/res/hashnode/image/upload/v1662458657850/E39aro8A3.png align="left")

### 3. To display the given date string in the format of date (MM DD YYY)
- $ ```date --date="1/04/2020"``` 

![date --date="1/04/2020"](https://cdn.hashnode.com/res/hashnode/image/upload/v1662458804686/loHe8-KWQ.png align="left")

- $ ```date --date="June 3 2000"```

![date --date="June 3 2000"](https://cdn.hashnode.com/res/hashnode/image/upload/v1662458937780/fqq78eygG.png align="left")

### 4. To display past dates

- $ ```date --date="3 year ago"```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459018994/NM7Y6U_Kp.png align="left")

- $ ```date --date="5 hours ago"```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459047108/PirRsTMzo.png align="left")

- $ ```date --date="1 month ago"```
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459064581/zBmr39TN8.png align="left")

- $ ```date --date="2 week ago"```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459101068/NmS_vCdLm.png align="left")

- $ ```date --date="10 day ago"```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459123153/RuMiLevJL.png align="left")

### To display future date

- $ ```date --date="next wed"```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459160145/DNNfrsRSC.png align="left")

- $ ```date --date="next month"```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459196027/JgQt6TnHm.png align="left")

- $ ```date -date="2 day"```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459234881/FU5aynpx3.png align="left")

- $ ```date --date="1 year"```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459281284/YD68ehjmJ.png align="left")

### To set the system date and time 
- $ ```date --set="Wed Apr 27 14:20:55 PDT 2022"```

### To display the date string present at each line of file in the date and time format
<pre>
$ cat >> datefile
May 07 2022
Apr 03 2022
$ date --file=datefile
</pre>

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459417285/fMd4bLUhC.png align="left")

###  Date format options
- %D: Display date as mm/dd/yy.      
- %d: Display the day of the month (01 to 31).      
- %a: Displays the abbreviated name for weekdays (Sun to Sat).
- %A: Displays full weekdays (Sunday to Saturday).
- %h: Displays abbreviated month name (Jan to Dec).
- %b: Displays abbreviated month name (Jan to Dec).
- %B: Displays full month name(January to December).
- %m: Displays the month of year (01 to 12).
- %y: Displays last two digits of the year(00 to 99).
- %Y: Display four-digit year.
- %T: Display the time in 24 hour format as HH:MM:SS.
- %H: Display the hour.
- %M: Display the minute.
- %S: Display the seconds.

<pre>
$ date +%[format-option]

$ date "+%D"
$ date "+%D %T"
$ date "+%A %B %d %T %y"
$ date "+%Y/%m/%d"
$ date "+%Y-%m-%d"
</pre>


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662459564794/Inq4DJWbK.png align="left")

Credits: tkdhanasekar@gmail.com