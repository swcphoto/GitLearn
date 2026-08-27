# 查询状态 
* 查询工作区状态 `git status`

# 比较对象及命令 
* 工作区&暂存区  `git diff <file>`
* 工作区&版本库  `git diff HEAD <file>`
* 暂存区&版本库  `git diff --cached <file>`


# 日志查询 
* 查询提交历史 `git log`
* 查询提交历史 `git log --pretty=oneline`
* 查询提交历史 显示分支合并图 `git log --graph --pretty=oneline --abbrev-commit`
* 查看历史命令 `git reflog`

# 版本回退
* 回退至上一版本 `git reset --hard HEAD^`
* 回退至某版本 `git reset --hard <commit-hash>`

# 撤销修改
* 丢弃工作区修改 `git checkout -- <file>`
* 丢弃工作区修改 `git restore <file>`
* 丢弃工作区修改 `git restore .`
* 撤销暂存区修改 `git reset HEAD <file>`
* 丢弃暂存区修改 `git restore --staged <file>`
* 撤销工作区与暂存区修改 `git restore --staged --worktree <file>`
* 撤销工作区与暂存区修改 `git restore -S -W <file>`
* 恢复到历史版本 `git restore --source=<commit-hash-or-branch-name> <file>`

# 分支管理
* 创建分支 `git switch -c <branch-name>`
* 创建分支 `git checkout -b <branch-name>`
* 切换分支 `git switch <branch-name>`
* 切换分支 `git checkout <branch-name>`
* 重命名当前分支 `git branch -m <new-branch-name>`
* 重命名非当前分支 `git branch -m <old-branch-name> <new-branch-name> `

# 删除文件
* 语法 `git rm [option] <file>...`

| 选项 | 全称 | 说明 |
| :-----: | :------: | :-----: |
| -f | --force | 强制删除，即使文件有未暂存的修改 |
| -n| --dry-run |试运行，显示将要删除的文件但不实际执行|
|-r||递归删除目录及其内容|
|--cache||仅从暂存区删除，保留工作目录中的文件|
|--ignore-unmatch||即使文件不存在也不报错（退出状态为0）|

* 删除文件
    * 删除单个文件 `git rm main.c`
    * 删除多个文件 `git rm main.c test.c`
    * 使用通配符删除 `git rm *.c`
* 删除目录
    * 删除空目录 `git rm dir/`
    * 删除目录及其子内容 ` git rm -r dir/`
* 删除暂存区中的文件
    * `git rm --cache <file>`

```bash
git rm file.txt
git commit -m "remove file.txt
```

# 远程仓库
## 添加远程仓库
* 添加远程仓库 ` git remote add <远程仓库名称> <URL> `
* 配置步骤
    * 查看当前远程仓库 `git remote -v`
    * 添加远程仓库 `git remote add origin git@github.com:用户名/仓库名.git`
    * 验证添加结果 `git remote -v`
    * 推送代码至远程仓库
        * 第一次推送 `git push -u origin main`
        * 后续推送 `git push`

* 管理多个远程仓库

* 删除远程分支 `git push <repo-name> --delete <branch-name>`

```bash
# 添加主仓库
git remote add origin https://github.com/yourname/repo.git

# 添加另一个协作者的仓库
git remote add colleague https://github.com/colleague/repo.git

# 添加公司GitLab仓库
git remote add company https://gitlab.company.com/project.git
```

* 其他常用操作
    * 查看远程仓库详细信息 `git remote show origin`
    * 重命名远程仓库 `git remote rename old-name new-name`
    * 移除远程仓库 `git remote remove origin`
    * 更改远程仓库URL `git remote set-url origin https://github.com/yourname/new-repo.git`


- 创建分支并直接关联远程分支 `git checkout -b <master> <origin/master>`
- 将本地某分支管理远程分支 `git branch -u <origin/branch> <local/branch>`
- 关联当前分支到远程分支 `git branch -u origin/master`
- 首次推送并关联(当前分支) `git push -u origin master`
- 取消关联当前分支 `git branch --unset-upstream`
- 取消关联指定分支 `git branch --unset-upstream <branch-name>`
- 查看关联 `git branch -vv`
- `git push <origin> <local/branch>`
- 指定推送来源及目的地 `git push origin <source>:<destination>`
-  将foo分支的提交同步至远程main分支（截止至foo的上一条提交） `git push origin foo^:main`
- 将本地main分支的提交同步到远程的newBranch分支 `git push origin main:newBranch`
- 拉取远程分支 `git fetch <origin> <branch>`
- `git fetch origin <source>:<destination>`
- `git pull origin main:foo` 将远程的main分支下载到本地foo分支，将foo分支合并到当前分支


# 克隆远程仓库
* 克隆 `git clone <URL>`

# 分支管理
* 创建与合并分支
    * 创建并切换分支 `git checkout -b <branch>`
    * 查看当前分支 `git branch`
    * 切换分支  `git checkout <branch>`
    * 分支合并 `git merge dev`
    * 删除分支 `git branch -d dev`
    * 创建并切换分支 `git switch -c <branch>` 
    * 切换分支 `git switch <branch>`
    * 

- 查看分支
    - 查看本地分支 `git branch`
    - 查看远程分支 `git branch -r`
    - 查看所有分支 `git branch -a`

- 创建分支
    - 创建新分支 `git branch <branch-name>`
    - 创建并切换新分支 `git checkout -b <branch-name>`
    - 创建并切换新分支 `git switch -c <branch-name>`

- 切换分支
    - 切换已有分支 `git checkout <branch-name>`
    - 切换已有分支 `git switch <branch-name>`

- 删除分支
    - 删除本地分支 `git branch -d <branch-name>`
    - 强制删除分支 `git branch -d <branch-name>`
    - 删除远程分支 `git push orgin --delete <branch-name>`
    - 删除远程分支 `git push origin :<branch-name>`

- 合并分支
    - 合并某分支到当前分支 `git merge <branch-name>`
    - 合并分支 禁用快进 `git merge --no-ff -m "xxx" <branch-name>`

- 暂存更改
    - 暂存当前工作 `git stash`
    - 恢复暂存内容 `git stash pop`
    - 查看暂存列表 `git stash list`
    - 恢复指定stash `git stash apply stash@{number}`

- 复制提交
    - 将提交的修改复制到当前分支 `git cherry-pick <commit-hash>`
    
# 标签管理
- 创建标签 `git tag <tag-name> `
- 为指定提交创建标签 `git tag <tag-name> <commit-hash>`
- 为指定提交创建标签 `git tag -a <tag-name> -m "xxx" <commit-hash>`
- 查看所有标签 `git tag`
- 查看指定标签信息 `git show <tag-name>`
- 将标签推送到远程 `git push origin <tag-name>`
- 推送所有标签 `git push origin --tags`
- 删除标签 `git tag -d <tag-name>`
- 删除远程标签 `git push origin :refs/tags/<tagname>`

# rebase 
- 更改当前分支的目标基底 git rebase <目标基底>
- 更换指定分支的目标基底 git rebase <目标基底> <指定分支>


# 分离HEAD
- HEAD指向某次提交或分支 `git checkout <commit-hash/branch>`
- 相对引用，将HEAD指向上一次提交 `git checkout HEAD^`
- 相对引用，当前节点有两个父节点时 `git checkout HEAD^` `git checkout HEAD^2`可以指向不同父节点
- 绝对引用 `git check HEAD~3`

# 撤销提交
- `git reset HEAD^`
- `git revert HEAD`

# 提取单个提交
- `git cherry-pick <commit-id> ... `

# 交互式变基
- `git rebase -i HEAD~4`

- `git describe`



