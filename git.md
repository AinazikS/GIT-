# Git
> Status
```
untracked(не отслеживаемый) -> modified(changes) -> staged(git add .) -> commited(git commit -m "Message")
```
```
git init
```

> it`ll return changes to the last commit
```
git restore main.asm
```
> diff -diffences | it shows which differences were done
```
git diff
```
> but if you have already git added the file, the git diff command won`t work, instead you should run
```
git diff --staged
```
> to view logs
```
git log
```
```
git status
```
____
```
git add .
```
```
git commit -m "message is here"
```
or  run this 1 command instead of this 2
> -a... means add
```
git commit -am "message is here"
```
---
```
git --help
```
> mv - move, rm -remove
```
git mv | git rm
```
> How delete file in commit but in the directory
```
git rm --cached
```
>*.gitignore && readme.md*
> in .gitignore file
```
__pycache__/
*.py[cod]
docker-compose.yml
log/
resources/products.json
```

```
git branch
```

>*to **create** branch*
 
```
git branch (name of the branch)        
```

>*to **delete** branch*

```
git branch -d (name of the branch) 
```
>*to **rename** branch*
```
git branch -M bugfix  
```
>**switch between** *branches*
```
git checkout (name of the branch)      
```
>*switch between branches and the same time switch to that branch straightaway*
```
git checkout -b (name of the branch)   
```
>*to **join** each other (each branch)*, do it in __main__ branch and use the name of the other one when merging 
```
git merge (name of the branch)         
```
>*after you can delete  extra branches*
___
> to switch between commits
```
git checkout __hash___
___
## Push
```
git remote add origin https://github.com/AinazikS/Online-Recording-System.git
```

```
git push -u origin
```
___
### Actions after renaming *master* branch
```
git branch -m master main
```

```
git fetch origin
```

```
git branch -u origin/main main
```

```
git remote set-head origin -a
```
___
# Steps

```
git add file1 file 2
```
git commit -m "Message1"
```
git add file3 file 4
```
git commit -m "Message2"

```
commit f70fdcef37c16fdf9f1e9dc239fe130d396aff0e    ------- HASH
Author: airgedon <104425308+airgedon@users.noreply.github.com>
Date:   Thu Jun 30 14:10:44 2022 +0600

    Rename main.asm to hello.asm
```
> it`ll show detaled information about this commit
```
git show __it`s__hash_
```
