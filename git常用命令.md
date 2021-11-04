
### git远程分支覆盖本地分支
```
git fetch --all
git reset --hard origin/master (这里master要修改为对应的分支名)
git pull
##
git reset –hard HEAD 清空暂存区，将已提交的内容的版本恢复到本地，本地的文件也将被恢复的版本替换（恢复到上一次commit后的状态，上一次commit后的修改也丢弃）
```

### git 添加多个远程仓库

```
 git remote add <name> <url>
 git push <name> <branch>
 git fetch <name> <branch>
 ### 把远程B仓库的代码合并到A仓本，先把B仓库的分支fetch到本地，再试用cherry-pick 将对应的提交合并到本地A仓库对应的分支上。
 ### 不能直接用merge ，不然会merge很多没用的代码
 git cherry-pick <log-id>
```

### 撤销git pull

```
git reflog
git reset --hard HEAD@{n}  ##n是你要回退到的引用位置）回退
git reset --hard <log-id>

```

### git restore  <file>和 git restore --staged  <file> 的区别

```
#没有add 的文件在工作区，add之后的文件进入暂存区。
git restore <file>: 撤销 本地修改 （表示将在 工作区 但是 不在暂存区 的文件撤销更改）=> git checkout .（checkout只能对文件内容撤回，restore包括文件自身的操作，如添加文件、删除文件）
git restore --staged <file>: 撤销 暂存区 (作用是将 暂存区的文件从暂存区撤出，但不会更改文件) => 取消add 操作

```

### git 学习链接
[搞清 git checkout，git restore 和 git reset](https://blog.csdn.net/Sweet_19BaBa/article/details/111950384)
[git restore 和 git restore --staged 的区别](https://blog.csdn.net/houhj168/article/details/106335131)