# Git 学习笔记

## 新建仓库

```bash
git init #在当前文件夹新建一个空仓库
```

## 工作区域和文件状态

工作区，暂存区，本地仓库：

![](/Users/zhouyu/Desktop/learngit/assets/IMG_3937.PNG)

文件状态：

1. 未跟踪（Untrack）：新创建的，未被`git`管理起来的文件。
1. 未修改（Unmodified）：已经被`git`管理起来，但是还没修改过的文件。
1. 已修改（Modified）：已修改的文件，但是还没提交到暂存区里的文件。
1. 已暂存（Staged）：修改后已经添加到暂存区里的文件。

![IMG_3938](/Users/zhouyu/Desktop/learngit/assets/IMG_3938.JPG)

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

![IMG_3940](/Users/zhouyu/Desktop/learngit/assets/IMG_3940.JPG)

## 回退版本

![IMG_3942](/Users/zhouyu/Desktop/learngit/assets/IMG_3942.JPG)

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

![IMG_3943](/Users/zhouyu/Desktop/learngit/assets/IMG_3943.JPG)

## 删除文件

![IMG_3944](/Users/zhouyu/Desktop/learngit/assets/IMG_3944.JPG)

## .gitignore

生效范围：不在版本库中的文件。

tip：

```bash
echo 123 >> file.txt#>>表示追加
```

在.gitignore中添加`temp/`表示忽略temp文件夹

![IMG_3947](/Users/zhouyu/Desktop/learngit/assets/IMG_3947.JPG)

## 远程仓库

```bash
git push#本地修改提交到远程仓库
git pull#远程仓库的修改拉取到本地仓库
```

