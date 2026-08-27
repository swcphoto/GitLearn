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
- option
    - -u --set‑upstream	设置上游追踪分支，设置后直接简写git push	git push -u origin master
    - -f --force	强制推送，直接覆盖远程，危险，多人协作慎用	git push -f origin master
    - --force‑with‑lease	安全强制推送；远程有他人新提交则拒绝，推荐替代 -f	git push --force-with-lease origin master
    - --dry‑run	模拟推送，仅打印操作，不会真实上传代码	git push --dry-run origin master
    - --tags	推送全部本地标签到远程仓库	git push --tags origin
    - --all	推送本地所有分支	git push --all origin
    - --delete	删除远程分支	git push --delete origin dev
    - --no‑verify	跳过 pre‑push 钩子，不执行提交前校验	git push --no-verify
    
- 指定推送来源及目的地 `git push origin <source>:<destination>`
-  将foo分支的提交同步至远程main分支（截止至foo的上一条提交） `git push origin foo^:main`
- 将本地main分支的提交同步到远程的newBranch分支 `git push origin main:newBranch`
- 拉取远程分支 `git fetch <origin> <branch>`
- `git fetch origin <source>:<destination>`
- `git pull origin main:foo` 将远程的main分支下载到本地foo分支，将foo分支合并到当前分支

# git push & pull
- `git push [option] <remote> [<local_branch:remote_branch>]`
    - `remote`：远程仓库别名，通常为`origin`
    - `refspec`格式：`本地分支:远程分支`
        - 本地master推送到远程 master `git push origin master`
        - 本地dev推送到远程 feature/v1 `git push origin dev:feature/v1`
        - 删除远程dev分支  `git push origin :dev`
    - 高频实操示例
        - 首次推送并绑定上游分支 `git push -u origin master`
        - 重写commit后安全强制推送 `git push --force-with-lease origin master`
        - 删除远程test分支 `git push --delete origin test`
        - 预演推送，查看会提交哪些内容，不上传 `git push --dry-run origin master`
        - 绑定上游后简写，无需写origin和分支名 `git push`

- `git pull [option] <remote> [<remote_branch>:<local_branch>]`
    - option
        - --no‑rebase	使用普通 merge 合并，git pull 原始默认行为	git pull --no-rebase origin master
        - --rebase	拉取后使用变基rebase代替 merge 合并，保持线性提交历史，日常推荐	git pull --rebase origin master
        - --dry‑run	模拟拉取，不改动本地代码	git pull --dry-run origin master
        - -s / --strategy	指定合并策略	git pull -s resolve origin master
        - -X / --strategy‑option	给合并策略传递参数，设置冲突处理逻辑	git pull -X theirs origin master
    - 拉取远程master，合并到当前本地分支 git pull origin master
    - 拉取远程master，合并到本地dev分支（不需要切到dev） git pull origin master:dev
    - git pull origin master 等价于 git fetch origin & git merge origin/master
    - git pull --rebase origin master 等价于 git fetch origin & git rebase origin/master
    - 默认merge方式拉取代码 git pull origin master
    - rebase变基拉取（推荐，历史干净无多余merge节点）git pull --rebase origin master

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

# 配置用户参数
- 配置用户名 `git config --global user.name "newName"`
- 配置邮箱 `git config --global user.email "newEmail"` 
- 查看配置参数 `git config --global --list`

# SSH秘钥
- 生成ssh秘钥 `ssh-keygen -t rsa` 
- 测试ssh配置是否成功



