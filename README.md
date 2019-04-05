# HELLO! Simo   
# Welcome to LZLQW's blog     
---

*Git 只关心文件数据的整体是否发生变化  
提交时，若文件没有变化，Git 不会再次保存，而只对上次保存作一链接*  

*Git 使用 SHA-1 算法计算数据的校验和，通过对文件的内容或目录的结构计算出一个 SHA-1 哈希值，Git 数据库中的东西都是用此哈希值来作索引的*  

*已提交（committed），已修改（modified）和已暂存（staged）。已提交表示该文件已经被安全地保存在本地数据库中了；  
已修改表示修改了某个文件，但还没有提交保存；已暂存表示把已修改的文件放在下次提交时要保存的清单中*  

*Git 管理项目时，文件流转的三个工作区域：工作区，暂存区，以及本地仓库*  

*基本的 Git 工作流程如下：*  

*在工作目录中修改某些文件。  
对修改后的文件进行快照，然后保存到暂存区域。  
提交更新，将保存在暂存区域的文件快照永久转储到 Git 目录中*  
## GIT的基本操作
   自报家门:  
    1. `$ git config --global user.name "my name"`  
    2. `$ git config --global user.name "email@***.com"`
   
   创建版本库（创建空目录）  
    1. `$ mkdir learngit`  
    2. `$ cd learngit`  
    3. `$ pwd`(显示当前目录)  
    4. `$ git init`(使目录变为git可管理的仓库)  
    
   添加文件到git仓库  
    1. `$ git add example.txt`  
    2. `$ git commit -m "提交说明"`  
      commit 一次可提交多个文件，add 不同的文件到暂存区，随后使用commit提交即可，add 可反复多次使用  
      git add 命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行git commit就可以一次性把暂存区的所有修改提交到分支
   
   `$ git status`  
    查看当前仓库状态  
     example：*`On branch master  
                Changes not staged for commit:  
                    (use "git add <file>..." to update what will be committed)  
                    (use "git checkout -- <file>..." to discard changes in working directory)  
                     modified:   readme.txt  
                 no changes added to commit (use "git add" and/or "git commit -a")`*
                （文件已修改未提交）  
                *On branch master  
                 nothing to commit, working tree clean*  
                （暂存区为空 工作区也未修改）  
    
   `$ git diff example.txt`  
      查看文件修改了什么  
  
   `$ git log`  
      查看提交日志（历史）
    
   `$ git log --pretty=oneline`  
      精简版  
      example:*`$ git log --pretty=oneline  
                1094adb7b9b3807259d8cb349e7df1d4d6477073 (HEAD -> master) append GPL  
                e475afc93c209a690c39c13a46716e8fa000c366 add distributed  
                eaadf4e385e865d25c48e7ca9c8395c3f7dfaef0 wrote a readme file`*  
             1094ad...是commit id（版本号）  
             HEAD表示当前版本，上一个是HEAD^,上上一个版本是HEAD^^,以此类推...  
      版本回退：  
      `$ git reset --hard HEAD^`  
        或者  
      `$ git reset --hard 1094a`   
        即填写版本号，没必要写全但也不能太少。当然也可以这样使用回到最新的那个版本 append GPL  
          
   `$ git reflog`  
      查看每一次命令做了什么（查看命令历史便于回到未来哪个版本）  
       example:*`$ git reflog  
                e475afc HEAD@{1}: reset: moving to HEAD^  
                1094adb (HEAD -> master) HEAD@{2}: commit: append GPL  
                e475afc HEAD@{3}: commit: add distributed  
                eaadf4e HEAD@{4}: commit (initial): wrote a readme file`*  
     
   `$ cat example.txt`  
      查看example.txt的内容  
     
   `$ git checkout --example.txt`  
       把readme.txt文件在工作区的修改全部撤销，这里有两种情况：  
       一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；  
       一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。  
       总之，就是让这个文件回到最近一次git commit或git add时的状态。  
       符号 ‘--’必不可少  
       
   `$ git reset HEAD example.txt`  
       git reset HEAD <file>可以把暂存区的修改撤销掉，重新放回工作区  
     
   `$ rm example.txt`  
       从本地删除文件  
       1. `$ git rm example.txt`  
          `$ git commit -m "删除说明"`  
            从版本库删除文件example.txt  
       2. `$ git checkout --example.txt`  
            从版本库中恢复本地误删除的文件(未提交的修改无法恢复)  
    ### 分支  
    `$ git branch dev`  
       创建分支dev  
    `$ git checkout dev`  
       切换到分支dev，此时会显示`Switched to branch 'dev'` `$ git branch -b dev`表示快速创建并切换到dev分支  
    `$ git branch`  
       查看当前分支，当前分支前面会显示\*  
    `$ git merge`  
       合并指定分支到当前分支  
       合并后即可删除分支dev `$ git branch -d dev`  
       
---
## 实现AJAX的基本步骤  
要完整实现一个AJAX异步调用和局部刷新,通常需要以下几个步骤:  
      (1)创建XMLHttpRequest对象,也就是创建一个异步调用对象。  
      (2)创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息.  
      (3)设置响应HTTP请求状态变化的函数.  
      (4)发送HTTP请求.  
      (5)获取异步调用返回的数据.  
      (6)使用JavaScript和DOM实现局部刷新.   
       
