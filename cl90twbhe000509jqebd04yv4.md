# Can we push an empty commit?

<iframe style="height: 400px; width: 90%" src="https://www.youtube.com/embed/06JDE3wvMUc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



**Git Repo: ** https://github.com/syedjafer/empty_commit_tut



### Introduction

During our software development, we follow continuous integrations to deploy our code to the dev/QA/prod environment. For continuous integration, we are using Azure/AWS CI/CD delivery pipelines which allow us to build, test and deploy applications on a single push to a specific git branch. It helps us to reduce the manual overhead of deploying code to the server and handle all the actions automatically.

### Problem

We might have faced a problem, where we needed to re-run our delivery pipeline of a branch without adding any extra space or changing any files in the repository.

### Solution

So I searched for the solution for a while and It turns out that Git is allowing us to push an empty commit without adding any staged files to the branch, by using one option **--allow-empty** during the git commit.

```bash
git commit --allow-empty -m "empty commit"
```

So we will try to create a scenario to check this working,

1.Let us create a new repository, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665287103800/x1JbSbjkc.png align="left")


2.After the first commit,

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665287189634/dvB2QXggl.png align="left")

3.Empty commit, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665287620994/68s4l7Adr.png align="left")

4.Verifying the commit details in github, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665287314312/yoRl0A0FM.png align="left")

### Conclusion

Thus, from now on we need not to change any files to re-trigger the CI/CD Piplelines.

