# Native Browser Notification API - Part 1

### Introduction

Notifications are vital if you want to drive traffic to your web applications. Notifications can be shown even if the user is not active on your website/webapp.  Whether you are building an e-commerce website and want to show offers to your user or you are building a chatting application and want to show the notification about new messages.

Whether you are building an e-commerce website and want to show offers to your user or you are building a chatting application and want to show the notification about new messages.  
  
Many top web applications like Slack, Facebook, WhatsApp and a lot more are using the same technology to show notifications.  

Let's dive into the 'How to Use ?' part of notification API

### Notification API is new

The Notifications API is fairly new and it may not work at older browsers. Therefore, you should explicitly verify if the API is supported by the browser or not before showing a message. You can do this by checking if the `window` object has a property called `Notification`

```javascript
if(!window.Notification) {
    console.log('Browser does not support notifications.');
} else {
    // display message here
}
```

On supported platforms, displaying a desktop notification involves two things: requesting permission and creating a new notification to display to the user.

> **Note:** The Notification API requires your website to use an SSL certificate. It does not work on insecure origins (HTTP).

### Ask for Permission
Notification API will be only working after permission is granted. We can ask for permission using `Notification.requestPermission()`

```javascript
// asking user to grant the permission on page load
// to show notifications
window.addEventListener('load', () => {
  Notification.requestPermission();
// permission cannot be asked again if the user chose
// to grant or deny the permission.
// once granted or denied, then user have to change the
// permission manually.
});
```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665716780702/N5MinLC2o.png align="left")

On clicking of `Allow`, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665716815673/MGhgPo-9P.png align="left")

### Checking if the user has granted the permission
1. `default`  Permission is not asked yet, notifications will not be shown
2. `granted` User has granted the permission to show notifications
3. `denied` User has declined the permission


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665717065099/BwXXTzfvG.png align="left")


### Showing Notification

For showing notification, we can use Notification class

```javascript
const newMsgNotification = new Notification('A new message', {
  body: 'You have got a new message, check it out!',
  icon: 'https://images.unsplash.com/photo-1611605698335-8b1569810432?ixid=MnwxMjA3fDB8MHxzZWFyY2h8N3x8aWNvbnN8ZW58MHx8MHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60',
});
```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665717145092/TH2AVDN54.png align="left")


### Interacting with notifications

Users can also interact with the notification (like `click` on the notification).  `EventListener` can be added to notification instance.

```javascript
// navigate the user to you website when
// user click on a notification
newMsgNotification.addEventListener('click', (e) => {
  e.preventDefault();
  window.open('http://yourwebappurl.com', '_blank');
});
```

In addition to `click` listener, notification can listen to 3 more events:  
  
`close`: Fired when the notification is closed.  
`error`: Fired when the notification could not be shown for some reason.  
`show`: Fired when the notification in displayed.

### Closing Notifications

If you wish to close a notification before it automatically closes, you have a few options. You can either set a timeout, call Push’s close() method, or pass around the notification’s promise object and then call close() directly. Push’s close() method will only work with newer browsers, taking in a notification’s unique tag name and closing the first notification it finds with that tag.

```javascript
function spawnNotification(theBody, theIcon, theTitle) {
  const options = {
    body: theBody,
    icon: theIcon
  };

  const n = new Notification(theTitle, options);
  document.addEventListener('visibilitychange', () => {
    if (document.visibilityState === 'visible') {
      // The tab has become visible so clear the now-stale Notification.
      n.close();
    }
  });
}
```

### What will be in part 2 ?

All the properties of the Notification API. 

### References: 
1. https://developer.mozilla.org/en-US/docs/Web/API/notification