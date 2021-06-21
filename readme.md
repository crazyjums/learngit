- [ ] git command

  - [x] add files to the remote repository

    > 4 steps when you `git` files to the remote repository:
    >
    > 1. git add filename1, filename2, ....  or git add * (add all)
    > 2. git commit -m "add a hit here"
    > 3. git remote add origin "repository address"
    > 4. git push origin branch_name (such as: master)

  - [ ] merge 

  - [ ] rebase

  - [x] reset 

    > 对提交的版本进行回退，可以根据`git  log`命令查看已经提交的版本，然后可以根据指定`commit id`或者`HEAD`回退到不同的版本，
    >
    > `git log`信息如下：
    >
    > ```bash
    > $ git log
    > commit 466755c74ed4fd27059f6b0e4f42d0c3dcb8b663 (HEAD -> master, origin/master)
    > Author: crazyjums <crazyjums@gmail.com>
    > Date:   Mon Jun 21 14:58:11 2021 +0800
    > 
    >  add a second title
    > 
    > commit b57119f13a741f116daabfebd27b51a990b7322a
    > Author: crazyjums <crazyjums@gmail.com>
    > Date:   Mon Jun 21 14:39:35 2021 +0800
    > 
    >  modified the file, add a new line
    > 
    > commit 1f7990b84caf752f9e22d1dbcf215d5285066d25
    > Author: crazyjums <crazyjums@gmail.com>
    > Date:   Mon Jun 21 14:27:27 2021 +0800
    > 
    >  first time to commit
    > ```
    >
    > `HEAD`表示当前的版本号，如果需要回退到上一个版本号，则可以使用`HEAD^`、上上一个版本号则是`HEAD^^`、往上倒100个可以在`HEAD`后面写上100个`^`符号，当然也可以写成`HEAD~100`。
    >
    > `HEAD`在`git`中其实是一个指针，指向不同的版本号，回退也就是将`HEAD`指针重新指向了不同的版本信息。
    >
    > ![](C:\Users\ASUS\OneDrive\程序员文件夹\微信截图_20210621152126.png)
    >
    > 除了使用`HEAD`之外，还可以使用`commit id`进行回退，每一次版本提交都有一个宇宙唯一的`commit id`，指定该`commit id`的前几位就行，`git`会自行查找。
    >
    > ```bash
    > $ git reset --hard HEAD~2
    > HEAD is now at 1f7990b first time to commit
    > 
    > $ git reset --hard 466755
    > HEAD is now at 466755c add a second title
    > ```
    >
    > 在使用`git log`命令时，只会显示当前命令窗口的历史提交记录，如果电脑重启之后，在使用`git log`命令出现的历史记录会是空，但是在`git`中，就算是重启电脑之后，还是有办法找到每一次的历史提交记录，可以使用命令：`git reflog`：
    >
    > ```bash
    > $ git reflog
    > 1f7990b (HEAD -> master) HEAD@{0}: reset: moving to HEAD~2
    > 466755c (origin/master) HEAD@{1}: reset: moving to 466755
    > 1f7990b (HEAD -> master) HEAD@{2}: reset: moving to HEAD~2
    > 466755c (origin/master) HEAD@{3}: reset: moving to 466755
    > b57119f HEAD@{4}: reset: moving to HEAD^
    > 466755c (origin/master) HEAD@{5}: commit: add a second title
    > b57119f HEAD@{6}: commit: modified the file, add a new line
    > 1f7990b (HEAD -> master) HEAD@{7}: commit (initial): first time to commit
    > ```
    >
    > 在使用`reset`等命令修改了本地文件之后，也就是当前本地电脑上的文件不是`git`托管平台的最新版本的时候，需要使用`git pull`命令将`git`平台的命令拉过来。
    >
    > ```bash
    > git pull <remote_repository> <branch>
    > ```
    >
    > ```bash
    > $ git pull git@github.com:crazyjums/learngit.git master
    > From github.com:crazyjums/learngit
    >  * branch            master     -> FETCH_HEAD
    > Auto-merging readme.md
    > CONFLICT (content): Merge conflict in readme.md
    > Automatic merge failed; fix conflicts and then commit the result.
    > ```

  - [ ] revert 

  - [x] checkout 

    > git-checkout - Switch branches or restore working tree files
    >
    > ```bash
    > $ git checkout <branch name>  # swtich to a new branch
    > ```
    >
    > ```bash
    > ASUS@ZHG_ASUS MINGW64 ~/OneDrive/learngit (master)
    > $ git checkout new_branch
    > Switched to branch 'new_branch'
    > 
    > ASUS@ZHG_ASUS MINGW64 ~/OneDrive/learngit (new_branch)
    > ```

  - [ ] stash 

  - [ ] cherry-pick

  - [x] branch

    > branche是git tree中的分支，其中主分支是master
    >
    > ```bash
    > $ git branch <branch name> # create a new branch 
    > $ git push origin <branch name> # push the new branch to remote repository
    > $ git branch -d <branch name> # delete the local branch
    > $ git push origin :<branch name> # delete the remote repository branch
    > $ git chechout <branch name> # swtich to <branch name> branch
    > $ git branch -a # show all branch of your repository
    > ```

  - [x] delete file from remote repository

    > ```bash
    > $ git rm <file name> or <dic name>
    > $ git commit -m ""
    > $ git push origin <branch name>
    > ```