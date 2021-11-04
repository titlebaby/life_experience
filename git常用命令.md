
### git远程分支覆盖本地分支
```json
git fetch --all
git reset --hard origin/master (这里master要修改为对应的分支名)
git pull
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