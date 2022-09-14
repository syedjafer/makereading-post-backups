## wget: download an entire website

Wget is the non-interactive network downloader which is used to download files from the server even when the user has not logged on to the system and it can work in the background without hindering the current process.

In this blog post we will see how to download an entire website using wget. Only that functionality. 

```bash
wget --recursive --html-extension --no-clobber -k --page-requisites <http url>
```

Lets download the content of **https://www.fsftn.org,**

```
wget --recursive --html-extension --no-clobber --k --page-requisites https://www.fsftn.org
```

**During the process:**

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662651863451/CbUR1rC_4.png align="left")

**After completion:**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662651879604/Ie2l0URGk.png align="left")

**Folder directory:**

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662652312811/rPvyMO2I4.png align="left")

**Serving it on localhost:**

Using ```python3 -m http.server```,

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662652363257/u564YU3j3.png align="left")

We can view it in localhost now, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662652406623/gTbpLsPt_.png align="left")

By this we are able to download the entire website.  