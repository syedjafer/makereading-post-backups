# package.json and package-lock.json

### Introduction
If you work in web development, you likely use **NPM** (Node PM or New PM)  all the time. It is a free public software registry - the largest in the world - that is accessible at the type of ```npm install``` in your command prompt so long as you have node.js installed already. Whenever we try to create a new project we will see a ```package.json``` file will be created. Whenever we install any packages ```package-lock.json``` file and ```node_modules``` folder will be created. In this blog post, we will see on **SemVer**, the purpose of package.json and package-lock.json and the internal functioning of npm install. 

### What is versioning?

The Node.js ecosystem uses **SemVer**, which is not mandatory but is strongly encouraged. This feature isn't necessary for an unpublished package. It's common practice to ```increase the version number before uploading new NPM versions `` to **SemVer**. This procedure is not commonly employed when a package is not being utilized as a dependency or is not being published to npm install package-lock. Maintaining the version field of a package used as a dependency is critical to ensuring that others use the correct version of a package. 


![semversion](https://cdn.hashnode.com/res/hashnode/image/upload/v1663256464986/EXy_HyHOW.png align="left")

There are three elements to a version: 
- major (significant changes in the version)
- minor (adding new features )
- patch (a bug fix)

Let's see this w.r.t [express](https://www.npmjs.com/package/express) package,

1. Caret (^) - Allow npm to upgrade minor and patch versions if they are available.
2. Tilde (~) - Allow npm to upgrade only patch versions if they are available. 

For Example, 

Consider the package express, with version-> ^4.17.1 -> If there are any minor versions available say 4.18.0 then npm is allowed to update to 4.18.0. 

![express semver caret](https://cdn.hashnode.com/res/hashnode/image/upload/v1663256522407/VnaRLfsW-.png align="left")
	
But in the case of ~, even if the 4.18.0 version is available, npm won't upgrade to 4.18.0. 

![express semver tilde](https://cdn.hashnode.com/res/hashnode/image/upload/v1663256560339/jXkHfQaif.png align="left")

### package.json

package.json is an important file, which is been used to install the packages required for the node projects. 

#### How it is created?
 ```package.json``` is a file that gets generated when we are initializing the npm project (```npm init -y```). 

![package.json image](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257044130/PwLEJT2h1.png align="left")

 
#### What it contains?

Let's take a look 

<pre>
{
  "name": "node-projects",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.18.1"
  }
}
</pre>

1. Package.json is a list of all the dependencies of a project. This includes version info (with upgradation feasibility caret ^ and tilde ~ ) for what needs to be downloaded.
2. It keeps the minimum version an application needs.
3. It also contains details on project properties, description, author & license information, scripts to run via npm, etc.

<b>Properties inside package.json </b>

**1. name** property: Name of the module. <br>
**2. version** property: Current version of the module. <br>
**3. license** property: Licence of the project (eg. MIT, GPL-3.0, BSD-3).<br>
**4. description** property: Description of the module given by the developer. <br>
**5. keywords** property: Related keywords of the module. <br>
**6. main** property: specify the direction to the entry point to the module package.json is describing. <br>
**7. repository** property (optional): Details about the cloud repository (eg: git)<br>
**8. scripts** property: It takes an object with as many key (category)/value (commands) pairs.<br>
 ```
    "scripts": {
        "build": "node app.js",
        "test": "standard"
    }
 ``` 

**9. dependencies** property:  The other modules that this module uses - are defined. The dependencies property takes an object that has the name and version at which each dependency should be used. Do note that you'll frequently find carets (^) and tildes (~) included with package versions. (It's for production). <br>
**10. devDependencies** property: Used to define dependencies to run in development. <br>
 
The above properties are the common properties that we usually see in development. There are many other properties also available. Please check out the [docs](https://docs.npmjs.com/cli/v8/configuring-npm/package-json) for more details. 

### package-lock.json (Exact version of the installed package)

package-lock.json is an auto-generated document during installation. It looks a lot like the package.json dependencies but with more information when you open it.

![package-lock.json](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257148871/2eZ2PU_f-.png align="left")

> As you continue to work on your project, you decide to disregard it. You'll eventually run into issues if you're dependent on anything. Either it's missing, or the incorrect version is installed. It's very uncommon for users to delete the package-lock.json file and run npm install. What's the point? Who knows what this thing is meant to do? Precisely what does it do?

package-lock.json describes the **exact tree** that was generated, such that subsequent installs are able to generate identical trees, regardless of intermediate dependency updates.

As you can see in the below image, package-lock.json won't contain ^ or ~. It will have the exact version of the installed package. While package.json will have the minimum version needed to run the project. 

![package-lock.json](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257265434/KbvdzF83y.png align="left")

#### How it is created?
 ```package-lock.json``` is automatically generated for any operations where npm modifies either the node_modules tree or package.json. Eg. during npm install. 

![package-lock.json](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257148871/2eZ2PU_f-.png align="left")


#### What it contains?

Let's take a look, 


![package-lock.json](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257427593/0aAYIjBaH.png align="left")

1. package-lock.json is used to avoid differences in installed dependencies on different environments and generate the same results in every environment.
2. NPM installs exact versions of the package as saved in package-lock.json and ignores the symbol ^ and ~ from package.json so as to avoid installing the latest/updated version of the package which might break the application if the application codebase is not compatible with the updated version of packages.
3. It contains other meta information of packages to save the time of fetching that data from npm when installing any package using npm install.
4. It allows npm to skip repeated metadata resolutions for previously installed packages and hence optimizes the installation process.

<b>Properties inside package-lock.json </b>

**1. name** property: name of the module. It will match the name property in package.json. <br>
**2. version** property: The version of the package this is a package-lock for. This will match what's in package.json.<br>
**3. lockfileVersion** property: It's an integer value. Either 1, 2, or 3. <br>

- 1: The lockfile version used by npm v5 and v6.<br>
- 2: The lockfile version used by npm v7, which is backward compatible with v1 lock files.<br>
- 3: The lockfile version used by npm v7, without backward compatibility affordances. This is used for the hidden lockfile at node_modules/.package-lock.json, and will likely be used in a future version of npm, once support for npm v6 is no longer relevant.<br>
 
**4. packages** property: It is an object that maps package locations to an object containing the information about that package.

<u>Eg:</u> 

<pre>
	 "node_modules/etag": {
      "version": "1.8.1",
      "resolved": "https://registry.npmjs.org/etag/-/etag-1.8.1.tgz",
      "integrity": "sha512-aIL5Fx7mawVa300al2BnEE4iNvo1qETxLrPI/o05L7z6go7fCw1J6EQmbK4FmJ2AS7kgVF/KEZWufBfdClMcPg==",
      "engines": {
        "node": ">= 0.6"
      }
    },
</pre>

**5. dependencies** property: Its a mapping of package names to dependency objects

### How does npm install work?


So far we have seen the functionalities of two files ```package.json``` and ```package-lock.json```, and also what each of those files contains. Now let's see how this files is been used with npm install. 


![npm install.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257562104/yFAnqFBHx.jpg align="center")

Whenever someone clones a repository and does the ```npm install``` command
and if your project has both a ```package.json``` and a ```package-lock.json``` and you run ```npm install``` then the dependencies would get installed using ```package-lock.json``` and not ```package.json```.

but if there are some discrepancies (which will discuss below) between the ```package-lock.json``` and the ```package.json``` and you run ```npm install```, then npm would use the ```package.json``` file to update the ```package-lock.json``` and you might end up having a different version than what you initially installed. 

<b>Let's look at an example:</b>

Let's consider a package called 'express' and we can install it like ```npm install express```. So in your folder, you can see those 2 files package.json and package-lock.json. 


![npm install new project](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257678956/omivfpId6.png align="left")


Let's see the versions of express in both the files,


![package.json package-lock.json](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257742027/vzNeE3SZm.png align="left")

It's 4.18.1, Now we can change the minor version in the ```package.json``` file from 18 to 17. 


![package.json minor version change](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257843290/BuSDHOX5P.png align="left")

Then we can delete the **node_modules** folder. 

![node modules deletion](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257882342/xOFxiVak7.png align="left")

So now, we can install the packages using ```npm install```. Let's see whether we are having the version mentioned in **package-lock.json** or **package.json**.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257922927/gGgmOZxeQ.png align="left")


```
npm install
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663257952938/yq8_5eNBF.png align="left")


From the above image, we can see that the version value in ```package-lock.json``` is maintained. So  ```package-lock.json``` is having higher precedence. 
 
But, we can see another scenario, We can change the version value in ```package-lock.json``` from 4.18.1 to 5.0.0 and follow the same process again. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663258016410/BW44-3FVM.png align="left")

Let's delete the **node_modules** and reinstall using ```npm install```.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663258100898/WsxoAhukR.png align="left")

Now if we are checking those files, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663258145658/h42VqoBLE.png align="left")


Now we can see the precedence is been moved to ```package.json```. 

To know more about the working of ```npm install```, please refer to their github code,  https://github.com/npm/cli/blob/latest/lib/commands/install.js

### How does npm ci work?


![npm ci.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1663258226274/LlemGBemK.jpg align="center")

`npm ci` (or clean install) runs only if the project has a lock file (package-lock.json) and if there's some discrepancy between the lock file (package-lock.json) and `package.json`, then `npm ci` errors out, so it doesn't update the lock file like `npm install`. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663258294410/5waiXtBnx.png align="left")

`npm ci` simply removes the `node_modules` directory and then installs the dependencies and hence the name clean install.

So, `npm ci` is no different than `npm i` if there's no `node_modules` directory present and there are no discrepancies between `package-lock.json` and `package.json`.

So, using `npm install` is okay if you've cloned a repo because it respects the lock file, however, in CI environments you should consider using `npm ci` because it does a clean install.


### What is the discrepancy?

There are many discrepancies that may occur, now we will discuss one of those scenarios. 
For example, we can consider the same package as express, In the below image, we can see values of versions are different in package.json (^4.18.1) and package-lock.json (5.0.0).


![Screenshot from 2022-09-15 19-42-47.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663258410208/wDBrRAEMk.png align="left")


Now we can go to https://semver.npmjs.com/ to check the compatibility. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663258348656/cvf2RCYI2.png align="left")

So we can see the package express with version ^4.18.1 supports only two versions (highlighted in green), (i.e,) 4.18.0 and 4.18.1. The version mentioned in ```package-lock.json``` (5.0.0) is not present in the highlighted lists. This is the discrepancy. 

### Frequently Asked Questions

**1. Why is package-lock.json needed?**<br>
Every installed package is tracked in a package-lock.json file so that a product may be re-created exactly as it was before its maintainers make any updates. For a particular issue, this is the best way to fix it.
 
**2. What is package.json?**<br>
An application's Node.js package.json file is its brain. A project's functional characteristics are defined here, which NPM utilizes to install dependencies, execute scripts, and identify the entry point to our package. It captures vital information about a project, which is necessary before publishing it to NPM.

**3. What is the significant difference between package.json and package-lock.json?**<br>
Package.json and package.lock.json both offer basic information about the project. So that future installations will have the same tree, it defines the precise configuration used to produce it.

**4. Why does package-lock.json change?**<br>
NPM is changing the package-lock.json file appropriately to represent all the dependencies it has obtained since it may have received more up-to-date versions of some of them during the npm install. Suppose NPM modifies the package lock.

**5. Is it possible to delete package-lock.json?**<br>
Never remove the package-lock.json from your computer's hard drive. npm, install returns the identical versions for first-level dependencies when specified without ranges.


