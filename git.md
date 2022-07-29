# Git

```
git init
```

```
git add .
```

```
git rm --cached
```
> to view logs
```
git log
```
```
git status
```

```
git commit -m "message is here"
```

```
git --help
```

>*.gitignore && readme.md*

```
git branch
```

>*to **create** branch*
 
```
git branch (name og the branch)        
```

>*to **delete** branch*

```
git branch -D (name og the branch) 
```
>*to **rename** branch*
```
git branch -M (name og the branch)    
```
>**switch between** *branches*
```
git checkout (name og the branch)      
```
>*switch between branches and the same time switch to that branch straightaway*
```
git checkout -b (name og the branch)   
```
>*to **join** each other (each branch)*
```
git merge (name of the branch)         
```

>*after you can delete  extra branches*
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
