# git

## 常用命令流程图
![](https://huatu.98youxi.com/markdown/work/uploads/upload_c7705adcae1c13ff5798c8fdf494d061.png)

![](https://huatu.98youxi.com/markdown/work/uploads/upload_724fbbd29a75fb2a25972869590d050d.png)
## `git status`
```
git status
```
- 该命令将显示所有需要提交的文件。


## `git config`
- 该命令将分别设置提交代码的用户名和电子邮件地址。
```
git config –global user.name “[name]”
git config –global user.email “[email address]”
```
## `git init`
- 该命令可用于创建一个新的代码库。
```bash
git init
git init [repository name]
```
## `git clone`
- `git clone` 是 Git 中用于克隆远程仓库到本地的命令。通过 `git clone`，你可以将远程仓库的所有文件、分支和历史记录完整地复制到本地，创建一个与远程仓库相同的本地仓库副本。
```bash
git clone <repository_url> [<local_directory>]
```
- 其中，`<repository_url>` 是远程仓库的 URL，指定你要克隆的仓库地址。`<local_directory>` 是可选的，用于指定你要在本地创建的目录名称，如果不提供 `<local_directory>` 参数，默认会在当前目录下创建一个与远程仓库同名的文件夹。

- 克隆指定分支的远程仓库：
```bash
git clone -b <branch_name> <repository_url>
```
- 例如，要克隆名为 `myrepo` 的远程仓库的 `dev` 分支到当前目录下，可以执行以下命令：
```bash
git clone -b dev https://github.com/user/myrepo.git
```



## `git add`
- 该命令可以将一个文件添加至stage(暂存区)。
```bash
git add [file]
```
- 该命令可以将多个文件添加至stage(暂存区)。
```bash
git add .
```

## `git commit`
- 该命令可以在版本历史记录中永久记录文件。
```bash
git commit -m “[注释]”
```
- 该命令将提交git add命令添加的所有文件，并提交git add命令之后更改的所有文件。
```bash
git commit -a
```
## `git log`
- 该命令将删除工作目录中的文件，并将删除动作添加到stage。
```bash
git log
```
- 起别名优化显示
```bash
alias git-log='git log --pretty=oneline --all --graph --abbrev-commit'
```
## `git reflog`
```bash
git reflog
```
- 显示引用日志的列表，包含一系列引用操作的记录，按时间顺序排序。每个记录都有一个唯一的哈希值（commit hash），用于标识该操作。引用日志的输出通常包括以下信息：
	- 哈希值：引用操作所涉及的提交的哈希值。
	- 引用名称：受影响的引用的名称，如分支名、标签名等。
	- 操作说明：描述该引用操作的简短说明，如合并、提交、重置等。

- 通过查看引用日志，你可以跟踪仓库中的引用变动，了解分支之间的切换、提交的移动、合并和重置等操作历史。引用日志对于恢复误删的分支、回退到先前的提交状态等情况非常有用。

## `git reset`
- 该命令将从stage中撤出指定的文件，但可以保留文件的内容。
```bash
git reset [file]
```
- 该命令可以撤销指定提交之后的所有提交，并在本地保留变更。
```bash
git reset [commit]
```
- 该命令将丢弃所有的历史记录，并回滚到指定的提交。
```bash
git reset –hard [commit]
```
## `git branch`
- 该命令将显示当前代码库中所有的本地分支
```bash
git branch
```
- 该命令将创建一个分支
```bash
git branch [branch name]
```
- 该命令将删除指定的分支。
```bash
git branch -d [branch name]
# 强制删除
git branch -D [branch name]
```

- `git branch -vv` 是一个用于查看分支及其关联的远程分支的 Git 命令。它会显示本地分支列表，并列出每个分支所跟踪的远程分支的名称。
```bash
git branch -vv
```
```bash
* main                4c0d6f7 [origin/main] Update README.md
  feature/branch-a    97c9f12 [origin/feature/branch-a: ahead 2] Add feature A
  feature/branch-b    7a18e9e [origin/feature/branch-b] Fix bug B
  master              3fcd0a8 [origin/master: behind 1] Update file
```


## `git checkout`
- 你可以通过该命令切换分支。
```bash
git checkout [branch name]
```
- 你可以通过该命令创建一个分支，并切换到新分支上。
```bash
git checkout -b [branch name]
```

## `git merge`
- 该命令可以将指定分支的历史记录合并到当前分支。
```bash
git merge [branch name]
```
- 当你在合并分支时遇到问题或者合并过程中出现冲突时，可以使用该命令将合并操作回滚到合并之前的状态。
	- 取消当前的合并操作。
	- 恢复原始分支的状态，将其回滚到合并之前的版本。
	- 丢弃合并操作中已经处理的修改。
```bash
git merge --abort
```
- 使用 `git merge --abort` 命令的前提是，你已经开始了一个合并操作但还没有完成。如果合并已经完成并且已经执行了提交操作，那么 `git merge --abort` 将无法回滚合并。

## .gitignore
- `.gitignore` 文件是一个用于指定哪些文件和文件夹应该被 Git 忽略的配置文件。在 Git 仓库中，`.gitignore` 文件可以帮助你排除不想被版本控制的文件、临时文件、编译生成的文件等。

- 以下是 `.gitignore` 文件的写法和一些常见的规则说明：

1. 模式匹配规则：
  
  - `*`：匹配任意字符（除了目录分隔符 `/`）。
  - `?`：匹配任意单个字符。
  - `/`：目录分隔符，用于指定路径。
  - `**`：递归通配符，匹配零个或多个目录。
  - `!`：否定符号，表示取反，不忽略匹配的文件或文件夹。
2. 文件或文件夹的规则：
  
  - 直接指定文件或文件夹的相对路径：例如 `path/to/file.txt`。
  - 使用通配符进行匹配，如 `*.txt` 表示匹配所有扩展名为 `.txt` 的文件。
3. 注释：
  
  - 使用 `#` 符号表示注释，以 `#` 开头的行将被忽略。
```bash
# 忽略编译生成的文件
build/
dist/
*.exe

# 忽略临时文件
temp-*

# 忽略特定文件
config.ini
private.key

# 不忽略特定目录中的文件
!docs/

# 递归忽略文件或目录
logs/
**/cache/

# 忽略根目录下的 .env 文件
/.env
```
## 远程仓库
### 生成 ssh 公钥
```bash
 ssh-keygen -t rsa
```
- 如果公钥已存在，则自动覆盖
###  获取公钥
```bash
cat ~/.ssh/id_rsa.pub
```
### 测试 SSH 连接
```bash
ssh -T git@github.com
或
ssh -T git@gitee.com
```
### 本地仓库与远程仓库进行关联
```bash
git remote add origin <remote_repository_url>
```
### 查看远程仓库
```bash
 git remote
```

## `git push`
- 将本地仓库的更改推送到远程仓库
```bash
git push <远程主机名> <本地分支名>:<远程分支名>
```
- 如果本地分支名与远程分支名相同，则可以省略冒号：
```bash
git push <远程主机名> <本地分支名>
```

- 例如，以下命令将本地的 master 分支推送到 origin 主机的 master 分支。
```bash
git push origin master
```

- 如果本地版本与远程版本有差异，但又要强制推送可以使用 --force 参数：
```bash
git push --force origin master
```

- 删除主机的分支可以使用 --delete 参数，以下命令表示删除 origin 主机的 master 分支：
```bash
git push origin --delete master
```

- 将本地分支与远程分支进行关联，以便后续的 `git push` 和 `git pull` 命令可以自动追踪到正确的远程分支。
```bash
git push --set-upstream <remote> <branch>
```

- 例如，要将当前分支的提交推送到名为 `origin` 的远程仓库的 `dev` 分支，并将本地分支 `dev` 与远程分支 `origin/dev` 进行关联，可以运行以下命令：
```bash
git push --set-upstream origin dev
```

## `git fetch`
- `git fetch` 是 Git 中用于从远程仓库获取（拉取）最新的提交、分支和标签等信息，但不会自动合并或修改本地分支。它将远程仓库的更新保存到本地，以便你可以在本地进行比较、合并或查看差异等操作。
```bash
git fetch <remote>
```

- 例如，要从名为 `origin` 的远程仓库获取最新的提交，可以运行以下命令：
```bash
git fetch origin
```

- 获取指定远程分支的更新：
```bash
git fetch <remote> <branch>
```
- 例如，要从名为 `origin` 的远程仓库获取 `dev` 分支的更新，可以运行以下命令：
```bash
git fetch origin dev
```
- 获取所有远程分支的更新：
```bash
git fetch --all
```

## `git pull`
- `git pull` 是 Git 中用于从远程仓库获取最新提交并自动合并（拉取并合并）到当前分支的命令。它相当于执行了 `git fetch` 和 `git merge` 两个步骤的组合操作。
```bash
git pull <remote> <branch>
```
- 其中，`<remote>` 是远程仓库的名称，如 `origin`，`<branch>` 是要拉取和合并的远程分支的名称。

- 例如，要从名为 `origin` 的远程仓库的 `main` 分支获取最新提交并自动合并到当前分支，可以运行以下命令：
```bash
git pull origin main
```

- 简化的方式：如果你已经将本地分支与远程分支进行了关联，可以直接使用 `git pull`，而无需指定远程仓库和分支名称。Git 会自动根据关联关系执行拉取和合并操作。例如：
```bash
git pull
```
