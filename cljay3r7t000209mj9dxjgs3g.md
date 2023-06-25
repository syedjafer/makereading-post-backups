---
title: "Fork bomb"
seoTitle: "Understanding Fork Bomb: Recursive Program Replication Explained""
seoDescription: "Discover the concept of a fork bomb, a recursive program that replicates itself endlessly. Learn how fork bombs work, their implications, and its importance"
datePublished: Sun Jun 25 2023 04:44:14 GMT+0000 (Coordinated Universal Time)
cuid: cljay3r7t000209mj9dxjgs3g
slug: fork-bomb
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687667526394/de074e6c-ad9e-4d80-9449-63dc5c3cf406.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1687668198136/a55ab5c3-0c15-4edb-b72c-bc8f396b19be.png
tags: linux, technology, tamil, fork-bomb, tamiltech

---

Fork bomb is a process which is enough to bring down your system by consuming all the system resources. It goes away after a system reboot, though.

In this post, we will see

1. What is a fork bomb in general
    
2. How does the `:(){ :|:& };:` turn into a fork bomb
    
3. Why the fork bomb is likely not to do any damage (yes, your distro might be bombproof)
    
4. Quick tip on preventing fork bombs
    

Consider fork bomb as a DoS (denial of service) attack, as it replicates existing processes till your system utilizes 100% of system resources and makes it completely unusable.

## Explanation:

Imagine you have a computer program that you can run. When you run this program, it creates a copy of itself, and both the original program and the copy continue running simultaneously. Now, each of these copies also creates more copies of itself, and the process keeps repeating rapidly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687667622777/f13d2b77-19f4-4157-8af1-6171e5137f7b.png align="center")

As a result, the computer gets overwhelmed with an increasingly large number of running copies of the program. This can consume a significant amount of the computer's resources, such as processing power and memory, to the point where the computer becomes sluggish or unresponsive. It's like having an army of clones that multiply exponentially, eventually causing chaos and making it difficult for anything else to function properly.

This kind of program is called a fork bomb because it "forks" or creates copies of itself endlessly, bombarding the computer with an ever-growing number of processes.

## Is it malicious?

Fork bombs are not meant to be used maliciously but rather as a demonstration of how a simple piece of code can cause significant disruption. However, they can be harmful if they are used on a computer without permission, as they can cause the system to crash or become unusable until the excess processes are terminated.

Just a restart will do fine.

## How to write a fork bomb ?

We have the code examples in different languages here [https://github.com/makereading/fork-bomb](https://github.com/makereading/fork-bomb). Now lets inspect the famous shell fork bomb with 11 characters,

```bash
:(){ :|:& };:
```

Let's break down how this shell fork bomb works:

1. `:(){ ... }`: This defines a shell function named `:` (a single colon), which is a valid function name in Bash. The function definition is enclosed within curly braces.
    
2. `:|:&`: Inside the function, there is a command sequence. The `:` followed by a pipe symbol (`|`) means that the function calls itself recursively. The pipe redirects the output of the function to another instance of the function.
    
    The ampersand (`&`) at the end puts the command sequence in the background, allowing the function to run concurrently with other processes.
    
    So essentially, each time the function is called, it creates two more instances of itself, and this replication continues exponentially.
    
3. `;:`: After defining the function, the final `;:` executes the function for the first time, triggering the recursive replication.
    

When this fork bomb is executed, the shell function `:` is invoked, and it starts multiplying itself rapidly. Each instance of the function creates more instances, quickly exhausting system resources such as CPU time, memory, and process slots. Eventually, the system becomes overwhelmed and may freeze or become unresponsive.

## How come the second instance will get triggered ?

Since its an recursive function, you might have the doubt of why the second is getting even hit. The function is invoked twice in a pipeline and the pipe is backgrounded, so both instances are being run in the background. Although that's a semantic detail as in reality it is likely that only one is ever attempted, and its recursion halts the system before the other ever starts