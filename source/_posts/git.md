---
title: git
date: 2024-07-30
---

```
初始化项目
git init
拉取项目
git clone
查看项目状态
git status
拉取远程分支到本地
git pull origin mian
	拉取到本地仓库并合并工作区
	pull=fetch+merge
	拉取到本地仓库
    git fetch
    将本地仓库的合并到工作区
    git merge
查看历史版本
git log
以简化形式查看历史版本
git log --pretty=oneline
以极简化形式查看历史版本
git log oneline
回退版本，切换版本
git reset --hard xxx(哈希)
回退^个版本，版本数量取决于^的数量
git reset --hard HEAD^
回退n个版本
git reset --hard HEAD~n
    --soft参数：仅仅在本地库移动HEAD指针
    --mixed参数：在本地库移动HEAD指针，重置暂存区
    --hard参数：在本地库移动HEAD指针，重置暂存区，重置工作区
创建分支xxx
git branch xxx
查看分支
git branch -v
切换分支
git checkout xxx
推送暂存区的文件到远程库origin的main分支
git push origin main
在本地多次修改后查看修改记录
git reflog
在本地多次修改后回退修改版本
git reset HEAD@{index}
修改刚刚提交的commit信息
git commit --amend
```

```
工作区：能看到的文件
暂存区：提交到本地暂存区的文件
```

# commit错误的分支补救，转到其他分支

```
# 撤回这次提交，但保留改动的内容
git reset HEAD~ --soft
git stash
# 现在切到正确的那个分支去
git checkout name-of-the-correct-branch
git stash pop
git add . # 或者你可以添加指定的文件
git commit -m "your message here";
# 现在你的改动就在正确的分支上啦
```

```
git checkout name-of-the-correct-branch
# 抓取 master 分支上最新的那个 commit
git cherry-pick master
# 然后删掉 master 上的那个 commit
git checkout master
git reset HEAD~ --hard
```

# 提交commit后，需要修改部分文件内容

```git
# 再次修改文件
git add . # 或者你可以添加指定的文件
git commit --amend --no-edit
# 你这次的改动会被添加进最近一次的 commit 中
# 警告: 千万别对公共的 commit 做这种操作
```

# commit错误的分支补救，转到新分支

```
# 基于当前 master 新建一个分支
git branch some-new-branch-name
# 在 master 上删除最近的那次 commit
git reset HEAD~ --hard
git checkout some-new-branch-name
# 只有在这个新分支上才有你最近的那次 commit 哦
```

# git diff没有内容

```
将文件add之后，diff没有内容可以使用以下命令比较
git diff --staged
```

# 回到以前的commit

```git
# 先找到你想撤销的那个 commit
git log
# 如果在第一屏没找到你需要的那个 commit，可以用上下
# 箭头来滚动显示的内容，找到了以后记下 commit 的
# hash 值
git revert [刚才记下的那个 hash 值]
# 这个操作会新建一次提交，不会修改原有的提交，reset则会删除提交
# git 会自动修改文件来抵消那次 commit 的改动，并创
# 建一个新的 commit，你可以根据提示修改这个新 commit
# 的信息，或者直接保存就完事了
```

# 将某个文件回退到某个commit的版本

```git
# 找到文件改动前的那个 commit
git log
# 如果在第一屏没找到你需要的那个 commit，可以用上下
# 箭头来滚动显示的内容，找到了以后记下 commit 的
# hash 值
git checkout [刚才记下的那个 hash 值] -- path/to/file
# 改动前的文件会保存到你的暂存区
git commit -m "这样就不需要通过复制粘贴来撤回改动啦"
```