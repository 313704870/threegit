t 学习整理


//基本入门命令
git init;
git config --global user.name "秦文帅"
git config --global user.email "313704870@qq.com"

//对一个文件 分两步提交到github 
vim readme.txt
git add readme.txt
git commit -m "describtion this add"
git log 

//查看状态
git  status;

//版本回退
git log --graph
git log --graph=oneline --abbrev-commit
git reset --hard HEAD^ 回退上一步。
git reflog
git reset --hard commit_id 回退到任意版本。


//工作区和暂存区。
工作区（可以理解为一个目录）里 包含一个版本库。版本库中有 stage(暂存区)和自动创建的一个分支(master)，以及一个指向master的一个指针(HEAD)


原理是：
    新建一个文件。 vim test.txt
    先添加到暂存区。git add test.txt
    提交修改，把暂存区内容提交到当前分支 git commit -m "add test.txt"

eg:
    vim test.txt  //第一次修改
    git add test.txt 
    vim test.txt  //第二次修改
    git commit -m "first edit"

        //两次修改 其实只是第一次提交到当期分支了。以为第二次修改根本没提交到暂存区。

    git diff HEAD -- readme.txt   //查看工作区和版本库里面最新版本的区别

针对上述情况：
    可以 修改两次后。 在 git add  、git commit 统一提交到当前分支就好。


//撤销修改
    vim readme.txt
    git status
    git checkout -- readme.txt //还没添加到暂存区的时候。这样操作撤销操作

    vim readme.txt
    git add readme.txt
    git reset HEAD readme.txt 
    git checkout -- readme.txt //对已经添加到暂存区 这样去撤销修改。

    如果添加到暂存区，已经提交到当前分支了。可以使用 版本回退的功能。
        git reset --hard commit_id;


//删除文件
  vim  del.txt
  git add del.txt
  git commit -m "add del.txt"
  rm del.txt
  git rm del.txt
  git commit -m "remove del.txt"

  rm OK.txt
  git checkout -- Ok.txt  //如果删除这样回退

