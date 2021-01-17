# Git



## 1. Install Git

```shell
$ sudo apt install git
```

## 2. Configure Git

```shell
$ git config --global user.name "Your name"
$ git config --global user.email "email@example.com"
```

"--global" means the configuration will be used by all repositories.

## 3. Create repository

```shell
$ mkdir learngit
$ cd learngit
$ pwd

# Initialized Git repository
$ git init
```

## 4. Your first commit

```shell
# Note that "git add" can be used repeatedly to add multiple files
$ git add readme.txt

$ git commit -m "worte a readme file"
[master (root-commit) 8d99978] worte a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
 
```

## 5. Modify the file and Commit it again

```shell
# modify your file
$ vim readme.txt

# git status
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")

# git diff
$ git diff
diff --git a/readme.txt b/readme.txt
index 4b80cea..96d5a03 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
-\nGit is freee software
+Git is a distributed version control system.
+Git is freee software

$ git add readme.txt
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   readme.txt

$ git commit -m "add distributed"
[master 8e59af9] add distributed
 1 file changed, 2 insertions(+), 2 deletions(-)

```

## 6. Return to previous versions

```shell
$ git log
commit 3ab31b96bbb8f3991e72f95ec1a762c8e7227ba5 (HEAD -> master)
Author: Zee-hash <62379579+Zee-hash@users.noreply.github.com>
Date:   Sun Jan 17 18:06:59 2021 +0800

    append GPL

commit 8e59af9e6d3eb73d18d3a2ae5589668698d3d5f5
Author: Zee-hash <62379579+Zee-hash@users.noreply.github.com>
Date:   Sun Jan 17 18:02:36 2021 +0800

    add distributed

commit 8d999785b3345c32c138bf623b2770f73bb10615
Author: Zee-hash <62379579+Zee-hash@users.noreply.github.com>
Date:   Sun Jan 17 17:48:42 2021 +0800

    worte a readme file
    
$ git log --pretty=oneline
3ab31b96bbb8f3991e72f95ec1a762c8e7227ba5 (HEAD -> master) append GPL
8e59af9e6d3eb73d18d3a2ae5589668698d3d5f5 add distributed
8d999785b3345c32c138bf623b2770f73bb10615 worte a readme file

# HEAD is pointed to the current version
# HEAD^ is pointed to the last version
# HEAD^^
# ...
# HEAD~100

$ git reset --hard HEAD^
HEAD is now at 8e59af9 add distributed

# DON't CLOSE YOUR TERMINAL IF YOU WANT TO BACK TO LATTER VERSION
# SO YOU CAN FIND COMMINR ID ON THE TERMINAL
# IF YOU HAVE CLOSED IT, YOU CAN USE "git reflog"
$ git reset --hard 3ab31
HEAD is now at 3ab31b9 append GPL
```

## 7. Working Directory / Repository 

### Working Directory 

the directory you could view on your computer. like **learngit**

### Repository 

a hidden directory on your working directory named **.git**

#### stage(index) 

After using "git add", files will to added to the stage area.

#### master

After using "git commit", files will to add to master branch.

### Git tracks changes

**Working Directory** ---add---> **stage** ---commit---> **master**

**commit only involves the files you have added to stage** 

## 8. Undo Edit

### working directory

```shell
$ git status 
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   readme.txt

$ git restore readme.txt
```

### stage

```shell
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   readme.txt
$ git restore --staged readme.txt
$ git restore readme.txt
```

# 9. Delete File

```shell
$ touch test.txt
$ git add test.txt
$ git commit -m "add test.txt"

$ rm test.txt
git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	deleted:    test.txt

no changes added to commit (use "git add" and/or "git commit -a")

# 1. git rm 
$ git rm test.txt
$ git commit -m "remove test.txt"

# 2. git restore
$ git restore test.txt
```



