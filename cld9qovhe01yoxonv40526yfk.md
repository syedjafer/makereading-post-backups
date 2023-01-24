# Adding Up the Power of Git: A Comprehensive Guide to the 'git add' Command

**GIT Series:** [https://makereading.com/series/git](https://makereading.com/series/git)

### Introduction

Git's "`add`" command is used to add changes in your working directory to the [staging area](https://makereading.com/mastering-git-understanding-the-three-stages-of-version-control). The staging area is like a holding place where you can review and prepare your changes before committing them to the repository. The "`add`" command is used to prepare your changes for commit, it is the first step in the git commit process.

### Basic Usages

The most basic use of the "`add`" command is to add all the changes in your <mark>working directory</mark> to the <mark>staging area</mark> by running the command "git add ."

However, you can also use the "`add`" command to selectively add changes. For example, if you want to add only specific file changes, you can run the command "`git add fileName.txt`" to add only the changes in that file.

For example,

Consider the below example to create the scenario (we are assuming you are already having git initialized in your folder),

1. `nano app.py` and add some content to it,
    

You can also use wildcards such as "git add \*.txt" to add changes in all .txt files.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673747876261/b6231833-cf63-4318-af93-82f31d7c8f3d.png align="center")

Now, if we are checking the status of the folder, using `git status`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673747929594/56232b5f-b510-42df-9b5b-b21fc0576877.png align="center")

You can see the folder and its content is under **Untracked files.** To add it to the **staging area** we can use `git add code`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673748058506/e9d0fc52-4e2b-4db4-a5f9-654b655aee53.png align="center")

It will be moved to the `staging area.`

### \-p --patch options

Additionally, you can also use the "`-p`" or "`--patch`" option with the "`add`" command to interactively review and select the specific changes that you want to add. This allows you to add changes line by line, hunk by hunk, and even split hunks.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673748502649/5cebdb27-450e-4ad5-9704-57088803f503.png align="center")

> Note: **\-p** or **\--patch** option will work only for files which are already added to the staging area.

In the above image, you can see some options in the last line,

**y** - stage this hunk

**n** - do not stage this hunk

**q** - quit; do not stage this hunk or any of the remaining ones

**a** - stage this hunk and all later hunks in the file

**d** - do not stage this hunk or any of the later hunks in the file

**e** - manually edit the current hunk

**?** \- print help

Here are some examples of how you can use the "git add" command:

* "`git add .`" : add all changes in the current directory to the staging area
    
* "`git add fileName.txt`" : add changes in the specified file to the staging area
    
* "`git add -p`" : interactively review and add changes
    
* "`git add --all`" : add all changes including new files
    
* "`git add -u`" : add changes in tracked files and remove deleted files
    

It is important to note that the "`add`" command only adds changes to the staging area and **does not actually commit** the changes to the repository. After you have added your changes, you can use the "`git commit`" command to commit the changes to the repository.

### Customization

In addition to the basic usage of the "`add`" command, there are some other options and attributes that you can use to customize the way it works.

1. The "`--dry-run`" option allows you to test the command without actually adding changes to the staging area. This is useful to see which changes would be added before running the command.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673749476955/d5a355ed-71db-4b51-a165-aaa8b9a03fe9.png align="center")
    
2. The "`--ignore-errors`" option allows you to continue adding files even if some of them fail to add. This is useful when dealing with large repositories with many files.
    
3. The "`--verbose`" option provides more information about the files that are being added.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673749761482/0ae2c090-80f4-4391-8902-3130cace93ab.png align="center")
    
    It will give a description of files added to the git.
    
4. The "`-b`", an attribute of the "`add`" command is the ability to add changes to a specific branch. By default, the "`add`" command adds changes to the **current branch**, but you can specify a different branch by using the "`-b`" option. For example, "`git add -b branchName`" will add changes to the specified branch.
    

It is also worth mentioning that the "`git add`" command can be used to add untracked files to the repository. By default, Git only tracks files that have been previously committed. But by using the "`git add`" command you can include new files in the repository and make them available for version control.

### Short Summary

Here are some examples of how you can use the "git add" command in real-world scenarios:

* To add all changes in the current directory to the staging area, you can use the command "`git add .`"
    
* To add changes in a specific file to the staging area, you can use the command "`git add fileName.txt`"
    
* To add changes in all .txt files to the staging area, you can use the command "`git add *.txt`"
    
* To interactively review and add changes, you can use the command "`git add -p`"
    
* To add all changes including new files, you can use the command "`git add --all`"
    
* To add changes in tracked files and remove deleted files, you can use the command "`git add -u`"
    
* To add changes to a specific branch, you can use the command "`git add -b branchName`"
    
* To check the changes that would be added without actually adding them, you can use the command "`git add --dry-run`"
    
* To add all the new files in a folder to the repository, you can use the command "`git add myfolder/`".
    

It is worth mentioning that you can use these commands in different combinations as well, for example you can use "`git add -u -p`" to interactively review and add changes in tracked files and remove deleted files.

Overall, the "`git add`" command is a powerful and versatile command that allows you to add changes to the staging area, review them and prepare them for commit. The flexibility of the command allows you to add changes selectively, interactively and with different options to fit your workflow.