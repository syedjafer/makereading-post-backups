# Properties of Notification API - Actions Property

### Introduction

In our previous post on Notification API, we discussed about how the API would be helpful to share notification to the user. In this post, we will see about instance properties of Notification API. 

### Properties of Notification API

1. Actions
2. Badge
3. Body
4. Data
5. Dir
6. Lang
7. Tag
8. Icon
9. Image
10. Renotify
11. RequireInteraction
12. Silent
13. Timestamp
14. Title
15. Vibrate

### Actions
Actions allow you to create another level of interaction with your users by just clicking the notification. Also, these **actions** properties will be only working with **service worker**. 

Consider the below service worker ```serviceWorker.js```, 

```javascript
self.addEventListener('notificationclick', (event) => {
    console.log("Clicked event action - ", event.action);
}, false);
```

Now the HTML code, 

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>Notification API</title>
	<script type="text/javascript">
		const notificationsProperties = {
		  "title": "Picture Time",
		  "body": "Time to look at some random pictures",
		  "icon": "https://picsum.photos/200",
		  "image": "https://picsum.photos/400",
		  // A badge is an image we display
		  // when there is not enough space to display the notification
		  "badge": "https://picsum.photos/300/200",
		  // Direction decides if the notification goes
		  // from left to right, right to left or let the browser decide
		  "dir": "ltr",
		  // As part of the direct user experience we also have 
		  // Audio- ....
		  "silent": "",
		  // ... sensorial
		  "vibrate": [200, 100, 200],
		  "actions":[{
  title: 'Show More',
  action: 'show_more'}
,{
  title: 'Close',
  action: 'close'}
]
		}
		
		Notification.requestPermission().then(res=> {
			console.log(res);
			
			if (res === 'granted'){
				if('serviceWorker' in navigator) {
		  			navigator.serviceWorker.register('serviceWorker2.js')
		    		.then(serviceWorkerRegistration => {
					      serviceWorkerRegistration.showNotification(
							'Stop Working', notificationsProperties);
		    		});
				} else {
					console.log('Not Present');
				}
			}
		})
		
	</script>
</head>
<body>

</body>
</html>
```

Here the Notification properties will look like, 

```javascript
const notificationsProperties = {
		  "title": "Picture Time",
		  "body": "Time to look at some random pictures",
		  "icon": "https://picsum.photos/200",
		  "image": "https://picsum.photos/400",
		  // A badge is an image we display
		  // when there is not enough space to display the notification
		  "badge": "https://picsum.photos/300/200",
		  // Direction decides if the notification goes
		  // from left to right, right to left or let the browser decide
		  "dir": "ltr",
		  // As part of the direct user experience we also have 
		  // Audio- ....
		  "silent": "",
		  // ... sensorial
		  "vibrate": [200, 100, 200],
		  "actions":[{
			title: 'Show More',
			action: 'show_more'}
			,{
			title: 'Close',
			action: 'close'}
			]
		}
```


Below is the image, captured in chrome with the notification API - actions. 


![Notification API - Actions](https://cdn.hashnode.com/res/hashnode/image/upload/v1666422140712/nFiKgvAhr.png align="left")

On clicking on the options, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666422191500/Z3D0QRqYS.png align="left")

So based on this we can interact with the user through notification api








