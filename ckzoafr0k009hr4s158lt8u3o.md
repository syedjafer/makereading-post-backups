## Folder Structure for Machine Learning Projects

Having a well-organized general Machine Learning project structure makes it easy to understand and make changes. Moreover, this structure can be the same for multiple projects, which avoids confusion. In this post, we will use the Cookiecutter package to create a Machine Learning project structure.

Step 1: Make sure that you have latest python and pip installed in your environment.

Step 2: Install cookiecutter

```bash
pip install cookiecutter
```

Step 3: Create a sample github repository, 

![Screenshot from 2022-02-15 20-50-47.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644938478676/28K2wc6XZ.png)

> Note: Don’t check any options under ‘Initialize this repository with:’ while creating a repository.

Step 4: Create a project structure

Go to a folder where you want to set up the project in your local system and run the following:

```bash
cookiecutter -c v1 https://github.com/drivendata/cookiecutter-data-science
```

It will ask the following options:

```
project_name [project_name]: <project-name>
repo_name [my-test]: <project-name>
author_name [Your name (or your organization/company/team)]: <Your name>
description [A short description of the project.]: <Details about the project>
Select open_source_license:
1 - MIT
2 - BSD-3-Clause
3 - No license file
Choose from 1, 2, 3 [1]: 1
s3_bucket [[OPTIONAL] your-bucket-for-syncing-data (do not include 's3://')]:
aws_profile [default]:
Select python_interpreter:
1 - python3
2 - python
Choose from 1, 2 [1]: 1
```

![Screenshot from 2022-02-15 20-59-09.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644938974373/PH4RdIyfV.png)

> Note: You can ignore the ‘s3_bucket’ and ‘aws_profile’ options.

Step 5: Add project to the git repository

```bash
cd <project folder>

echo "# ML-Project-Structure" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/syedjafer/ML-Project-Structure.git
git push -u origin main

```

The final structure will be the following:


![Screenshot from 2022-02-15 21-03-33.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644939233037/2xXdm5UbA.png)

Note: The data folder won’t appear in github. It will be in your local folder. This is not pushed to github as it will be in the ignore list (.gitignore file). If you want to checkin that also, just comment out in .gitignore file and add the data folder to github.

Some of the folder might not seem appropriate to your project. Feel free to delete it and adjust as per your need. 

