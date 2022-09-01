## Revisiting Git Commands - Part I

### Need

In my software development experience, as far now i have seen people using only a small set of git commands repeatedly. I also have doubts on functionality of git commands. git add, git commit, git status, git log, git rebase, git merge, git restore are the some commands we usually use. In this post, we will try to learn more extended functionalities. 

### Introduction

It's time we revisited Git and how important it is to master in order to advance in our careers. This guide serves as a reference for what I believe are necessary, yet lesser-known concepts. Mastering Git will make a huge difference in how you manage code and your own day-to-day workflow. Because Git commands are a bit archaic and hard to remember, this guide will be broken up by concepts and expected behavior instead.

In this post i have initialized a git repository in an empty folder and created a simple txt file for working. 


![empty git folder](https://cdn.hashnode.com/res/hashnode/image/upload/v1661949559430/pv1peDwBd.png align="left")


### Logging

Git log is a utility tool to review and read a history of everything that happens to a repository. Multiple options can be used with a git log to make history more specific. Generally, the git log is a record of commits.

- <u>git log</u>

It gives you the entire history of everything that happens to a repository. (More detailed log) In the descending order of timestamp (recent at the top)

![git log - full output detail](https://cdn.hashnode.com/res/hashnode/image/upload/v1661949596671/VaklMV3oL.png align="left")


- <u>git log --oneline</u>

It gives you more succinct output. Just the commit message with the commit hash (first 5 letters).

![git log --oneline](https://cdn.hashnode.com/res/hashnode/image/upload/v1661949496508/LHLYTytd5.png align="left")

- <u>git log --graph</u>

It gives you the commits details with a visual graph of branches. 

![git log --branch](https://cdn.hashnode.com/res/hashnode/image/upload/v1661949717445/Li2p2NZeI.png align="left")

- <u>git reflog</u>

To view your "undo" history. Because sometimes git log doesn't cut it, especially for commands that don't show up in your commit history.

**reflog** is basically your safety net after running "scary" commands like **git rebase**. You'll be able to see not only the commits you made, but each of the actions that led you there. 

**Usage of reflog:**

**Scenario**: You made some commits, did a git reset --hard to “undo” those changes (see above), and then realized: you want those changes back!

**Undo with**: git reflog and git reset or git checkout

**What’s happening**: git reflog is an amazing resource for recovering project history. You can recover almost anything—anything you’ve committed—via the reflog.

git reflog is similar to git log, but instead shows a list of times when HEAD changed.

### Modification

This category deals with checking the modifications done to the repository. 

- <u>git status</u>
While git status is a pretty basic command we all learn early on, its importance as a learning tool for internalizing git fundamentals bears repeating. It can also help you navigate through a complicated rebase or merge.

![git status](https://cdn.hashnode.com/res/hashnode/image/upload/v1661950078139/hzDwwBpqi.png align="left")

- <u>git diff</u>

To see the difference in changes of file, between the current state and last commit and between branches too. If git diff is used without any arguments, it will consider only the files in the unstaged stages. 

![git diff](https://cdn.hashnode.com/res/hashnode/image/upload/v1661950164473/ayXIF6HFO.png align="left")

- <u>git diff --staged</u>

It will consider the files in the staged changes. 


![staged difference](https://cdn.hashnode.com/res/hashnode/image/upload/v1661950320979/F57_8Sjfx.png align="left")

- <u>git diff branch_1..branch_2

To see the difference between two different branches.

![difference between 2 branches](https://cdn.hashnode.com/res/hashnode/image/upload/v1661952515546/eQKWiNyDH.png align="left")


### Final thoughts
In this blog post you have learnt about additional features in logging and modifications. In the upcoming blogs we will see about navigation and more other functionalities. 




