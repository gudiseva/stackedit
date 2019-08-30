# Git Commands

## Global Setup

    D:\WORKSPACE\git_projects>git --version
    git version 2.15.0.windows.1

    D:\WORKSPACE\git_projects>git config --global user.name "Nag Arvind Gudiseva"

    D:\WORKSPACE\git_projects>git config --global user.email "gnarvind@gmail.com"

## Create a new repository on the command line

    D:\WORKSPACE\git_projects> echo "# stackedit" >> README.md

    D:\WORKSPACE\git_projects> git init

    D:\WORKSPACE\git_projects> git add README.md

    D:\WORKSPACE\git_projects> git commit -m "first commit"

    D:\WORKSPACE\git_projects> git remote add origin https://github.com/gudiseva/stackedit.git

    D:\WORKSPACE\git_projects> git pull --rebase origin master

    D:\WORKSPACE\git_projects> git push -u origin master

## Push an existing repository from the command line

    D:\WORKSPACE\git_projects> git remote add origin https://github.com/gudiseva/stackedit.git

    D:\WORKSPACE\git_projects> git push -u origin master

## Import code from another repository

Initialize this repository with code from a Subversion, Mercurial, or TFS project.
> Import Code

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQyNjMzNzU2MV19
-->
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NzExNDA3ODgsMjk2NjExNjcwXX0=
-->