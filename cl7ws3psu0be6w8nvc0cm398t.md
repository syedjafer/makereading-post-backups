## Git Command Revisiting Part II - Git Reset

### Terminologies

1. **Work Tree**: Your working tree are the files that you are currently working on. Your local folder. 

2. **Git Index/Staging Area**: The git "index" is where you place files you want commit to the git repository. The index is also known as cache, directory cache, current directory cache, staging area, staged files. Before you "commit" (checkin) files to the git repository, you need to first place the files in the git "index".

The index is not the working directory: you can type a command such as git status, and git will tell you what files in your working directory have been added to the git index (for example, by using the git add filename command).

The index is not the git repository: files in the git index are files that git would commit to the git repository if you used the git commit command.

### Introduction

In simple words, git reset is to correct your mistakes. Consider a scenario, where you have mistakenly did some wrong code and commited it too. Everything started to fall apart. Now you want to go back to the previous stable state (or previous commit). This is the scenario, where git reset helps you. In this blog post you will understand the usage of git reset in 3 different ways. 

> This is a Part 2 of [Git Commands revisiting](https://syedjaferk.hashnode.dev/revisiting-git-commands-part-i). 


### Visualization of Working Folder, Staging, Local Repository
![work tree git](https://cdn.hashnode.com/res/hashnode/image/upload/v1662519374184/NTdf42nNy.png align="center")
 
### Git Reset

In general, git reset's function is to take the current branch and reset it to point somewhere else, and possibly bring the index and work tree along. Git reset helps you in two broad categories. 

1. To remove changes from staging area.
2. To undo commits at repository level. 

### To remove changes from staging area

#### Workground setup
1. Create a new folder.
2. Initialize git in the folder (```git init```)
3. Create a text file (eg: sample.txt)
4. Add some content inside it. 
5. Add the file to the staging area. ```git add sample.txt```


![git reset staging area](https://cdn.hashnode.com/res/hashnode/image/upload/v1662519622451/PLmbD64oe.png align="left")

#### Checking the stage area

Now the file is been added to the staging area (but not commited). But now you realize that you have a wrong content inside it. So inorder to remove it from the staging area, you just need to execute ```git reset <filename>```. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662519770210/8aZ2U7wSM.png align="left")

Now you can see that the file is been moved from the staging area to working directory. and the contents inside the file is preserved. 

**Some of the possible scenarios**, 
1. If there are many files in the staged area, then you can simply use ```git reset```.
2. There is also another command to unstage files, **git restore**. ```git restore --staged .```

### To undo commits at repository level

#### Workground setup

1. Create a new folder.
2. Initialize git in the folder (```git init```)
3. Create a text file (eg: file.txt)
4. Add some content inside it. 
5. Add the file to the staging area. ```git add file1.txt```
6. Create a text file (eg: file2.txt)
7. Add some content inside it. 
8. Add the file to the staging area. ```git add file2.txt```
9. Create a text file (eg: file3.txt)
10. Add some content inside it. 
11. Add the file to the staging area. ```git add file3.txt```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662519848707/nQV-ZBzNK.png align="left")

There are 3 modes to reset a commit from the local reposity. 
> Once any file or folder is committed, we won't have the concept of resetting the file. It will be resetting the commits only. 

All these 3 modes, will **move the HEAD to a specified commit**, and all the remaining recent commits will be removed. The mode will decide whether these changes are going to **remove from staging area and working directory or not.** 

#### Mixed Method (Default)

**Command**: ```git reset --mixed <commit-id>```
**Functionality**: It resets the index, but not the work tree. This means all your files are intact, but any differences between the original commit and the one you reset to will show up as local modifications (or untracked files) with git status. Use this when you realize you made some bad commits, but you want to keep all the work you've done so you can fix it up and recommit. In order to commit, you'll have to add files to the index again (git add ...).
**Hands On**:
Our working directory will look like this, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662519932426/cgPo2-tFV.png align="left")

Now we can check the log, 
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662519905478/D6ueTrrep.png align="left")


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662519965333/xS0NW6Ccx.png align="left")

We can try resetting the last commit (so we need to specify the previous commit to point it there), 

 ```git reset --mixed 002aa06```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662519992831/-VvxmvBpj.png align="left")

Now we can see the HEAD moved to the commit which we specified. And the file3.txt is removed from the local repository and staging. But the contents inside the file is preserved in the working directory. We can check using the git status to see the file under Untracked files. 


#### Soft Method

**Command**: ```git reset --soft <commit-id>```
**Functionality**: All your files are intact as with --mixed, but all the changes show up as changes to be committed with git status (i.e. checked in in preparation for committing). Use this when you realize you've made some bad commits, but the work's all good - all you need to do is recommit it differently. The index is untouched, so you can commit immediately if you want - the resulting commit will have all the same content as where you were before you reset.

**Hands On**:
Our working directory will look like this, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662520034695/-7EismZp0.png align="left")
Now we can check the log, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662520054489/NIM3eV2dr.png align="left")

We can try resetting the last commit (so we need to specify the previous commit to point it there), 

 ```git reset --soft f8d7c74```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662520562986/KNRBTQede.png align="left")

Now we can see the HEAD moved to the commit which we specified. And the file2.txt is removed from the commit, but staging. The contents in the file are preserved and its already present in the staging. We can check this using the git status to see the file under Added files.


#### Hard Method

**Command**: ```git reset --hard <commit-id>```
**Functionality**: This is the easiest to understand, probably. All of your local changes get clobbered. One primary use is blowing away your work but not switching commits: git reset --hard means git reset --hard HEAD, i.e. don't change the branch but get rid of all local changes. The other is simply moving a branch from one place to another, and keeping index/work tree in sync. This is the one that can really make you lose work, because it modifies your work tree. Be very very sure you want to throw away local work before you run any reset --hard.

**Hands On**:

Our working directory will look like this, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662520603365/8_ZcVz1IN.png align="left")

We can add one more commit (so that we will have some commits to test). 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662520620774/X-__m3ipw.png align="left")

so now we have 2 files in commit, and one file in working directory (untracked file - file3.txt). 
We can try resetting the last commit (so we need to specify the previous commit to point it there), 

 ```git reset --hard f8d7c74```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662520647247/zHvy6jRtc.png align="left")

Now we can see the HEAD moved to the commit which we specified. Also the file2.txt is been removed from the local repository, staging and the working directory. It removed the files that were present in the commit.  This is the one that can really make you lose work, because it modifies your work tree.



### The Strange Notation

When you are searching for the working for git reset, you might noticed people using HEAD^ and HEAD~1. These are just the shorthand or specifying commits, without having to use a hash name like f8d7c74. It's fully documented in the "specifying revisions" section of the man page for git-rev-parse, with lots of examples and related syntax. The caret and the tilde actually mean different things:

- HEAD~ is short for HEAD~1 and means the commit's first parent. HEAD~2 means the commit's first parent's first parent. Think of HEAD~n as "n commits before HEAD" or "the nth generation ancestor of HEAD".
- HEAD^ (or HEAD^1) also means the commit's first parent. HEAD^2 means the commit's second parent. Remember, a normal merge commit has two parents - the first parent is the merged-into commit, and the second parent is the commit that was merged. In general, merges can actually have arbitrarily many parents (octopus merges).
- The ^ and ~ operators can be strung together, as in HEAD~3^2, the second parent of the third-generation ancestor of HEAD, HEAD^^2, the second parent of the first parent of HEAD, or even HEAD^^^, which is equivalent to HEAD~3.

### Final thoughts
In this blog post we understood the working of different ways to reset a commit. I am having one question for you. When we are resetting to a different commit, (i.e) pointing the head to a different commit, what will happen to the removed commits ? Is there any way to go back to it ? 

We will continue with this question in the next part. Subscribe to my newsletter to keep track. 


