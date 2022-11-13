# Cookies and Javascript

### Introduction

Cookies are small text files that the server sends to the user's web browser when visiting a web page. The browser can store them and resend them to the same server on the next request. With cookies, the web pages can remember your user preferences, keep you logged in as well as display content relevant to your region. 

Unlike local storage, cookies are designed for sending information between the server and client while local storage is only for storing information on the client. Local storage can store up to 5Mb data, while coolies can store only 4kb data in text format. 

### Set Cookie

In Javascript, we can create a cookie with the use of the document.cookie property, 

```
document.cookie="name=Syed Jafer";
document.cookie="bool=True";
```

<u>Output:</u>


![document cookie value set](https://cdn.hashnode.com/res/hashnode/image/upload/v1663478889434/8bG1N0U-0.png align="left")


With the expiration date, 

```
document.cookie="user=syed jafer; expires=Thu, 1 Aug 2022 12:00:00 UTC";

// OR

function setCookie(cName, cValue, expDays) {
    const date = new Date();
    date.setTime(date.getTime() + (expDays*24*60*60*1000));
    let expires = "expires=" + date.toUTCString();
    document.cookie = `${cName}=${cValue};${expires};`;
}

setCookie('user', 'Syed Jafer', 30);
```

<u>Output:</u>


![setCookie](https://cdn.hashnode.com/res/hashnode/image/upload/v1663479020402/tAEyq35Ot.png align="left")

 ### Read Cookie

To read the values of the cookie you can use a function like the one below and pass to it the name of the cookie. 

```
const getCookie = (name) => {
	let cookieValue = null;
	if (document.cookie && document.cookie !== ""){
		const cookies = document.cookie.split(";");
		for (let itr = 0; itr < cookies.length; itr++){
			const cookie = cookies[itr].trim();
			if (cookie.substring(0, name.length + 1) === name + "="){
				cookieValue = decodeURIComponent(cookie.substring(name.length + 1));
				break;
			}
		}
	}
	return cookieValue;
}

const user = getCookie("user");
const bool = getCookie("bool");

const val = JSON.parse(bool.toLowerCase());
console.log(user, bool);
```

<u>Output:</u>


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663479520155/kIZtFhabr.png align="left")


### Delete Cookie

In order to delete a cookie just set the expires parameter to the past date. 

```
document.cookie = "user=;expires=Thu, 01 Jan 1970 00:00:00 GMT; path=/"
```

<u>Output:</u>

![document cookie](https://cdn.hashnode.com/res/hashnode/image/upload/v1663479394837/C1uTiw1ll.png align="left")
