# Welcome to LZLQW's blog
每天写1000个单词改变了我的生活

GIT的基本操作  
===========
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
     example：*On branch master  
                Changes not staged for commit:  
                    (use "git add <file>..." to update what will be committed)  
                    (use "git checkout -- <file>..." to discard changes in working directory)  
                     modified:   readme.txt  
                 no changes added to commit (use "git add" and/or "git commit -a")*
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
      example:*$ git log --pretty=oneline  
                1094adb7b9b3807259d8cb349e7df1d4d6477073 (HEAD -> master) append GPL  
                e475afc93c209a690c39c13a46716e8fa000c366 add distributed  
                eaadf4e385e865d25c48e7ca9c8395c3f7dfaef0 wrote a readme file*  
              1094ad...是commit id（版本号）  
              HEAD表示当前版本，上一个是HEAD^,上上一个版本是HEAD^^,以此类推...  
      版本回退：  
      `$ git reset --hard HEAD^`  
        或者  
      `$ git reset --hard 1094a`   
        即填写版本号，没必要写全但也不能太少。当然也可以这样使用回到最新的那个版本 append GPL  
          
   `$ git reflog`  
      查看每一次命令做了什么（查看命令历史便于回到未来哪个版本）  
       example:*$ git reflog  
                e475afc HEAD@{1}: reset: moving to HEAD^  
                1094adb (HEAD -> master) HEAD@{2}: commit: append GPL  
                e475afc HEAD@{3}: commit: add distributed  
                eaadf4e HEAD@{4}: commit (initial): wrote a readme file*  
     
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
            从版本库中恢复本地误删除的文件  
