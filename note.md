# Git 学习笔记

学习链接：[一小时掌握Git](https://www.bilibili.com/video/BV1HM411377j/?share_source=copy_web&vd_source=82fa3a30ff60d300c90c56999d163f81)

## 新建仓库

```bash
git init #在当前文件夹新建一个空仓库
```

## 工作区域和文件状态

工作区，暂存区，本地仓库：

![](./assets/IMG_3937.PNG)

文件状态：

1. 未跟踪（Untrack）：新创建的，未被`git`管理起来的文件。
1. 未修改（Unmodified）：已经被`git`管理起来，但是还没修改过的文件。
1. 已修改（Modified）：已修改的文件，但是还没提交到暂存区里的文件。
1. 已暂存（Staged）：修改后已经添加到暂存区里的文件。

![IMG_3938](./assets/IMG_3938.JPG)

```bash
git status#查看仓库的状态
git status -s#-s表示简略模式
```
## 添加和提交文件

```bash
git add file.txt#将file.txt添加到暂存区
```
```bash
git commit #提交，该命令只会提交暂存区的文件，不会提交工作区的文件!
git commit -m "第一次提交"#-m命令来描述提交细节。
```

![IMG_3940](./assets/IMG_3940.JPG)

## 回退版本

![IMG_3942](./assets/IMG_3942.JPG)

```bash
git reset --soft 5af90b8#回退版本的id
git reset --hard HEAD^#“^”表示上一个版本
git reset HEAD^#mixed参数是默认参数
```

```bash
git ls-files#查看暂存区的内容
```

```bash
#误删回溯
git reflog#查看需要恢复的版本号
git reset --hard b270efb#恢复到这个版本
```

## 查看差异

```bash
git diff#比较工作区和暂存区的差异
git diff HEAD#比较工作去和版本库之间的差异
git diff --cached #比较暂存区和版本库之间的差异
```

**HEAD**:指向当前分支的最新提交节点。

**HEAD^（HEAD~）**:上一个版本。

**HEAD~2**：上两个版本。

```bash
git diff 31862cd fa76031#比较两个版本的差异
git diff HEAD~2 HEAD file.txt#只查看这两个版本中file.txt的差异
```

![IMG_3943](./assets/IMG_3943.JPG)

## 删除文件

![IMG_3944](./assets/IMG_3944.JPG)

## .gitignore

生效范围：不在版本库中的文件。

tip：

```bash
echo 123 >> file.txt#>>表示追加
```

在.gitignore中添加`temp/`表示忽略temp文件夹

![IMG_3947](./assets/IMG_3947.JPG)

## 远程仓库

```bash
git push#本地修改提交到远程仓库
git pull#远程仓库的修改拉取到本地仓库
#git pull <远程仓库名> <远程分支名>:<本地分支名>
#                     此处相同可以省略冒号后的内容
```

**关联远程仓库：**

```bash
git remote add origin git@github.com:Syuu614/learngit.git#关联远程仓库
git branch -M main#指定分支的名称为main
git push -u origin main#:main #把本地main分支和远程仓库的main分支关联起来
```

```bash
git remote -v#查看当前仓库所对应的远程仓库的别名和地址
```

## 分支（重点）

```bash
git branch#查看所有分支
git branch dev#创建一个名叫dev的分支
git checkout dev#切换到dev分支/恢复文件dev(该方法存在歧义：建议使用git switch命令)
git switch main#切换到main分支
git merge dev#将dev分支合并到main分支
```

```bash
git log --graph --oneline --decorate --all#图形化的分支图
alias graph="git log --graph --oneline --decorate --all"#定义名为graph的命令
```

分支合并之后仍然存在，要手动删除。

```bash
git branch -d dev#删除已经合并的分支，如果是-D就是强制删除。
```

![IMG_3951](./assets/IMG_3951.JPG)

## 冲突

![IMG_3952](./assets/IMG_3952.JPG)

## 回退、恢复和变基

```bash
git checkout -b dev 244d35#恢复dev分支到ID为244d35的节点
```

[回退版本](#回退版本)

```bash
git switch dev#切换到dev分支
git rebase main#将dev分支的提交变基到main分支上，此时dev分支上的提交会添加在main分支的最新提交之后。
```

```bash
git switch main#切换到main分支
git rebase dev#将main分支的自出现dev分支之后的提交变基到dev分支上，此时main分支的自出现dev分支之后的提交会添加在dev分支的最新提交之后。
```

![IMG_3953](./assets/IMG_3953.JPG)

![IMG_3954](./assets/IMG_3954.JPG)

## 番外篇：开发规范

![IMG_3955](./assets/IMG_3955.JPG)

![IMG_3956](./assets/IMG_3956.JPG)
