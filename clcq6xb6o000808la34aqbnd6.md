# GIT - Session 1 - Evolution of Version Control System

### Important Links:

1. Github Link: [https://github.com/makereading/GIT](https://github.com/makereading/GIT)
    
2. Discussions: [https://github.com/makereading/GIT/discussions](https://github.com/makereading/GIT/discussions)
    

### Problem description

Consider we are in the time period before the 70s. Let's start with how people would have developed software before the 70s collaboration without any **version control system**.

Let's define some process flows,

### Process Flow 1

![Process Flow 1](https://cdn.hashnode.com/res/hashnode/image/upload/v1672587795457/383a50f9-ad64-404a-9177-19c6f8ef5e58.png align="center")

In this flow, there will be a master copy of the project with a dedicated person '**admin**', who takes care of the repository (master copy). So whenever there is a new request for a feature,

1. A developer will take a copy of the code from the **master copy** and then they will add some features.
    
2. The developer will create a **tarball** or a zip file with the **changelog** file, which contains the details of files that are been touched/changed while adding this new functionality.
    
3. Then the admin will verify the changes and merge the code to the master copy - this will be tiresome work. So the next time, when a feature request is coming, developers can take the code again from main -&gt; add features -&gt; tarball -&gt; merge with master. This cycle will run.
    

The above process may feel simple, but what if many developers are working parallelly, whether they need to wait for the other developer to complete their work?

Let's see the other process flow,

### Process Flow 2

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672588645844/47550193-2d14-4d56-97db-5f11329ae751.png align="center")

In process 2, consider they have established some network kind of stuff so that each developer can log in to the host with their user ID and can access the files.

In the above situation, when developer 1 Is using a particular file, then the file will be locked and other developers won't be able to access the file.

So other developers have to wait till developer 1 finishes his work.

### Let's hear from people in 70's

1. [https://qr.ae/prvymC](https://qr.ae/prvymC)
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673349550240/4a0b9d47-8914-4219-a402-2248ac23daf0.png align="center")

William says that it is difficult for **merging the files**, and files were shared in **tarballs or zip**

1. [https://qr.ae/prvYFb](https://qr.ae/prvYFb)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673349650956/22c5500a-b4ce-4504-ac14-5581d7779465.png align="center")
    
    Sam says, only a single person is been allocated to merge new changes and they usually take backups and file comparisons before merging files.
    
2. [https://qr.ae/prvYO2](https://qr.ae/prvYO2)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673349737474/bd13a905-c830-42a2-9b70-96897d0e6154.png align="center")
    
    Jeff says the loss of files is common/normal. They usually take a backup on a daily basis.
    

These are some of the reviews that I got from Quora. Now we have some expectations about the tool that we wanted. Let's pen it down.

### Expectations of a tool?

1. It should enable multiple people to simultaneously work on a single project.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673350153985/df04376e-8f7d-4803-97e8-d039c69ecad7.png align="center")
    
2. Each person edits his or her own copy of the files and chooses when to share those changes with the rest of the team. Thus, temporary or partial edits by one person do not interfere with another person's work
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673350179054/abc5f6f1-2b03-4a9f-909d-0c2823c9dad8.png align="center")
    
    .
    
3. Enables one person to use multiple computers to work on a project, so it is valuable even if you are working by yourself.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673350197788/0d284ebb-0ed6-4b98-a9f4-aa8ba13b9b8e.png align="center")
    
4. 🔥Integration work should be done simultaneously by different team members. In most cases, edits to different files or even the same file can be combined without losing any work.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673350220740/26c5e97a-f8f4-4b7a-b0c5-7409f1c1f9dc.png align="center")
    
5. Historical versions of your project. If you make a mistake, you can roll back to a previous version. You can reproduce and understand a bug report on a past version of your software.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673350257908/c702c28d-449f-4ca4-990c-d08f89474db2.png align="center")
    

### Necessity is the mother of invention

In 1972, people from bell labs developed the first version of the **Version Control System** named **SCSS** which they used for UNIX development. Which led to the birth of different generations. Below you can find the brief of different generations, if you are interested in learning more about those tools, please check out this [initial commit blog](https://initialcommit.com/blog/Technical-Guide-VCS-Internals).

#### First Generation

The first generation VCS were intended to track changes for individual files and checked-out files could only be edited locally by one user at a time.

They were built on the assumption that all users would log into the same shared Unix host with their own accounts.

1. SCSS
    
2. RCS
    

#### Second Generation

Introduced networking which led to **centralized repositories** that contained the 'official' versions of their projects.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673350956524/ebf98289-afbc-44a4-89fc-5126ff462557.png align="center")

#### Third Generation

The third generation is a distributed version control system, where we have each repository for the user to develop features and then we have one centralized repo to merge our features.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673351114806/d5c28df6-8261-4317-86ee-0ed5cd5e9073.png align="center")

In the time of the third generation, **BitKeeper** was created. It's a proprietary and closed-source software developed by [Larry McVoy](https://en.wikipedia.org/wiki/Larry_McVoy).

### Why are we discussing BitKeeper?

Imagine that you are in 2002, <mark>Linus Torvalds</mark> and <mark>other open-source developers</mark> all around the world were using BitKeeper for maintaining Linux Kernel. Yeah, as you think many developers didn't like the concept of using a proprietary tool for open-source development. But Linus stuck with it since it was free to use for open-source developers and it does the job well.

One of the open-source enthusiasts, [Andrew Tridgell](https://en.wikipedia.org/wiki/Andrew_Tridgell) felt the same about not using proprietary software for open-source development, so he created an open-source client after reverse engineering the protocols of BitKeeper client software.

When Larry, came to know about this, he didn't like the concept of Tridgell and there was a fight between them on copyright issues. After that Larry announced that "*<mark>be it an open-source developer or any developer, if they are using BitKeeper they need to pay. </mark>* "

> Please checkout these posts from 2005 when the actual fight happened [https://www.linux.com/news/bitkeeper-and-linux-end-road/](https://www.linux.com/news/bitkeeper-and-linux-end-road/) [https://www.infoworld.com/article/2670360/linus-torvalds--bitkeeper-blunder.html](https://www.infoworld.com/article/2670360/linus-torvalds--bitkeeper-blunder.html)

### Birth of GIT

Linus Torvalds has no option now, so he just created a new tool with the experience he gained from using BitKeeper, and the tool is named as **GIT**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673351955633/3e68d261-3d7e-4411-b127-2e01e645f7e7.png align="center")

### Enough History, Now let us install GIT

Please check out this link [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for installing GIT in your machines.

Please follow the upcoming blogs on this series to get your hands dirty on GIT.