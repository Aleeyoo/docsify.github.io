> [!TIP] **git 工作区域**
> ![git.png](https://raw.githubusercontent.com/Aleeyoo/note-gen-image-sync/main/72267ccb-8a99-443a-bd33-ea40ccb4ee0b.png)
> **工作区：** 就是你在电脑上看到的目录，也叫做工作目录。<br>
> **暂存区：** 英文叫stage, 或index。一般存放在".git目录"下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。<br>
> **本地仓库：** 就是你在本地计算机上的版本库，也叫做本地仓库。<br>
> **远程仓库：** 托管在网络服务器上的版本库，也叫做远程仓库。<br>

## Git 命令

#### **初始配置**

+ **0. 初始化仓库** +
  
  语法格式： `git init`
  <br>作用: 初始化仓库
  
  > 示例:<br>
  > git init<br>
+ **1. 配置用户名** +
  
  语法格式： `git config --global user.name "用户名"`
  <br>作用: 配置全局用户名
  
  > 示例:<br>
  > git config --global user.name "Aleeyoo"<br>
+ **2. 配置用户邮箱** +
  
  语法格式： `git config --global user.email "邮箱地址"`
  <br>作用: 配置全局用户邮箱
  
  > 示例:<br>
  > git config --global user.email "123456@qq.com"<br>
+ **3. 查看当前的配置信息** +
  
  语法格式： `git config --list`
  <br>作用: 查看当前的配置信息
  
  > 代码:<br>
  > git config --list<br>
+ **4. 通过 alias 配置简写** +
  
  语法格式： `git config --global alias.简写 "命令"`
  <br>作用: 配置简写命令
  
  > 示例:<br>
  > git config --global alias.co checkout<br>
  > git config --global alias.br branch<br>
  > git config --global alias.ci commit<br>
  > git config --global alias.st status<br>
+ **5. 配置 ssh key** +
  
  语法格式： `ssh-keygen -t rsa -c "邮箱地址"`
  <br>作用: 生成 ssh key 并添加注释<br><br>
  语法格式： `ssh-keygen -t rsa -P "" -f ~/.ssh/id_rsa`
  <br>作用: 生成 ssh key 并添加注释，不设置密码<br><br>
  语法格式： `cat ~/.ssh/id_rsa.pub`
  <br>作用: 查看 ssh key 公钥<br><br>
  步骤：`将 ssh key 粘贴到远端仓库`
  <br>作用: 将 ssh key 公钥粘贴到远端仓库，例如 github 仓库<br><br>
  语法格式： `ssh -T git@github.com`
  <br>作用: 测试 ssh key 是否配置成功

## 高频命令

<!-- tabs:start -->

#### **git remote**

+ 查看当前所有远程仓库 +
  
  语法格式： `git remote -v`
  
  > 示例：<br>
  > git remote -v<br>
+ 添加一个新的远程仓库 +
  
  语法格式： `git remote add <仓库名> <git url>`
  
  > 示例：<br>
  > git remote add origin git@github.com:Aleeyoo/note.git<br>
+ 删除指定的远程仓库 +
  
  语法格式： `git remote remove <仓库名>`
  
  > 示例：<br>
  > git remote remove origin<br>
+ 重命名远程仓库 +
  
  语法格式： `git remote rename <旧仓库名> <新仓库名>`
  
  > 示例：<br>
  > git remote rename origin new-origin<br>
+ 查看远程仓库的详细信息 +
  
  语法格式： `git remote show <仓库名>`
  
  > 示例：<br>
  > git remote show origin<br>
+ 修改推送源 +
  
  语法格式： `git remote set-url origin <新的 git url>`
  
  > 示例：<br>
  > git remote set-url origin git@github.com:Aleeyoo/note.git<br>
+ 为远程仓库添加多个 URL（同时推送多个仓库） +
  
  语法格式： `git remote set-url --add <仓库名> <新的 git url>`
  
  > 示例：<br>
  > git remote set-url --add origin git@github.com:Aleeyoo/note.git<br>
+ 移除远程仓库的某个 URL（当绑定了多个 URL 时） +
  
  语法格式： `git remote set-url --delete <仓库名> <git url>`
  
  > 示例：<br>
  > git remote set-url --delete origin git@github.com:Aleeyoo/note.git<br>

#### **git clone**

+ 克隆远端仓库到本地 +
  
  语法格式： `git clone <git url>`
  
  > 示例：<br>
  > git clone git@github.com:Aleeyoo/note.git<br>
+ 克隆远端仓库到本地，并同时切换到指定分支 branch1 +
  
  语法格式： `git clone <git url> -b branch1`
  
  > 示例：<br>
  > git clone git@github.com:Aleeyoo/note.git -b branch1<br>

#### **git add**

+ 将所有修改的文件都提交到暂存区 +
  
  语法格式： `git add .`
  
  > 示例：<br>
  > git add .<br>
+ 将指定文件提交到暂存区 +
  
  语法格式： `git add <文件名>` （多个文件空格隔开）
  
  > 示例：<br>
  > git add ./a.js ./b.js（./ 表示当前工作目录）<br>
+ 将指定文件下修改的内容提交到暂存区（多个文件空格隔开） +
  
  语法格式： `git add <文件夹>` （多个文件夹空格隔开）
  
  > 示例：<br>
  > git add ./js<br>

#### **git commit**

+ 将暂存区内容提交到本地仓库，并添加提交信息 +
  
  语法格式： `git commit -m "提交信息"`
  
  > 示例：<br>
  > git commit -m "add a.js and b.js"<br>
+ 将暂存区内容提交到本地仓库，并对上一次 commit 记录进行覆盖 +
  
  语法格式： `git commit --amend -m "提交信息"`
  
  > 示例：<br>
  > git commit --amend -m "add a.js and b.js"<br>
  
  > 说明：
  > *例如先执行 git commit -m "commit1" 提交了文件a，commit_sha为hash1；再执行 git commit -m "commit2" --amend 提交文件b，commit_sha为hash2。最终显示的是a，b文件的 commit 信息都是 "commit2"，commit_sha都是hash2*<br>
+ 将暂存区内容提交到本地仓库，并跳过 commit 信息填写 +
  
  语法格式： `git commit --amend --no-edit`
  
  > 示例：<br>
  > git commit --amend --no-edit<br>
+ ⚠️ 跳过校验直接提交 ⚠️ +
  
  语法格式： `git commit --amend --no-verify -m "提交信息"`
  
  > 示例：<br>
  > git commit --amend --no-verify "add a.js and b.js"<br>
+ 直接从工作区提交到本地仓库 +
  
  语法格式： `git commit -a -m "提交信息"`
  
  > 示例：<br>
  > git commit -a -m "add a.js and b.js"<br>
+ 提交暂存区内容，但排除指定文件 +
  
  语法格式： `git commit -m "提交信息" -- <文件路径1> <文件路径2>` （多个文件空格隔开，-- 为分隔符）
  
  > 示例：<br>
  > git commit -m "提交大部分修改，排除临时文件" -- .gitignore temp.log<br>
+ ⚠️ 修改历史提交（非最近一次）⚠️ +
  
  语法格式： `git rebase -i HEAD~n` （n为回溯的提交数量）
  
  > 示例：<br>
  > git rebase -i HEAD~3<br>（回溯最近3次提交，准备修改其中某次）
  
  > 说明：
  > *进入交互式界面，可修改指定的历史提交（需将目标提交的pick改为edit，修改后用git commit --amend修正，最后git rebase --continue完成）*
  > *仅建议修改本地未推送的提交，修改已推送的历史提交可能导致冲突*<br>
+ 取消最近一次提交，但保留暂存区和工作区内容 +
  
  语法格式： `git reset --soft HEAD~1` （HEAD~n 可指定撤销前n次提交）
  
  > 示例：<br>
  > git reset --soft HEAD~1<br>
+ 创建不含文件修改的空提交（常用于触发流程等场景） +
  
  语法格式： `git commit --allow-empty -m "提交信息"`
  
  > 示例：<br>
  > git commit --allow-empty -m "触发CI/CD构建"<br>
+ 临时指定本次提交的作者和邮箱，不影响全局配置 +
  
  语法格式： `git commit -m "提交信息" --author "用户名 <邮箱>"`
  
  > 示例：<br>
  > git commit -m "修复登录bug" --author "Bob <bob@example.com>"<br>

#### **git push**

+ 将本地仓库内容推送到远端仓库 +
  
  语法格式： `git push`
  
  > 示例：<br>
  > git push<br>
+ 将本地分支推送到远程并创建同名分支（首次推送新分支,后续可直接用 `git push`） +
  
  语法格式： `git push -u origin 本地分支名`
  
  > 示例：<br>
  > git push -u origin feature/login<br>（推送本地 feature/login 分支到远程，`-u`进行关联）
+ 将本地仓库指定分支 branch1 内容推送到远端仓库 branch1 +
  
  语法格式： `git push origin branch1`
  
  > 示例：<br>
  > git push origin branch1<br>
+ 推送本地分支到远程，但远程分支名与本地不同 +
  
  语法格式： `git push origin 本地分支名:远程分支名`
  
  > 示例：<br>
  > git push origin dev:develop<br>（将本地 dev 分支推送到远程 develop 分支）
+ 批量推送本地所有分支到远程（远程不存在的分支会被创建） +
  
  语法格式： `git push --all origin`
  
  > 示例：<br>
  > git push --all origin<br>
+ ⚠️ 强制推送本地仓库内容到远端仓库 ⚠️ +
  
  语法格式： `git push --force`
  
  > 示例：<br>
  > git push --force<br>
  
  > 说明：
  > *强制推送会覆盖远端仓库的内容，可能导致数据丢失*<br>
+ 强制推送但保留远程新增提交（安全强制推送） +
  
  语法格式： `git push --force-with-lease`
  
  > 示例：<br>
  > git push --force-with-lease origin main<br>
  
  > 说明：<br>
  > *类似 `--force`，但会检查远程是否有本地未同步的新提交，有则拒绝推送（减少协作时的误覆盖）,比 `--force` 更安全，推荐协作场景中优先使用*<br>
+ 删除远程仓库的指定分支 +
  
  语法格式： `git push origin --delete 远程分支名`
  
  > 示例：<br>
  > git push origin --delete feature/old<br>（删除远程的 feature/old 分支）

#### **git pull**

+ 从远端仓库拉取最新内容并合并到当前分支 +
  
  语法格式： `git pull`
  
  > 说明：<br>
  > *拉取并合并的远程分支和当前本地分支名称一致*<br>
+ 拉取并合并的远程分支和当前本地分支名称不一致 +
  
  语法格式： `git pull <远程主机名> <分支名>`
  
  > 示例：<br>
  > git pull git@github.com:zh-lx/git-practice.git branch1<br>
  
  > 说明：<br>
  > *常见的写法是：git pull origin branch1（origin 是远程仓库的默认简写，需先通过 git remote add origin <URL> 配置）*<br>
+ 拉取远程分支，与本地指定分支合并（无需先切换到本地分支） +
  
  语法格式： `git pull <远程主机名> <远程分支名>:<本地分支名>`
  
  > 示例：<br>
  > git pull origin dev:local-dev<br>（拉取远程 dev 分支，合并到本地 local-dev 分支）
+ ⚠️ 强制拉取远程分支并覆盖本地分支 ⚠️ +
  
  语法格式： `git pull --force`
  
  > 示例：<br>
  > git pull --force origin main<br>
  
  > 说明：
  > *此操作会直接丢弃本地与远程不一致的修改，仅在确认无需保留本地变更时使用*<br>
+ 拉取远程分支但不自动合并（仅获取更新） +
  
  语法格式： `git fetch <远程主机名> <分支名>`（`git pull` 本质 = `git fetch` + `git merge`）
  
  > 示例：<br>
  > git fetch origin main<br>（获取远程 main 分支的更新，存到本地 origin/main）
  > *之后可通过 `git merge origin/main` 手动合并，或 `git rebase origin/main` 变基合并*
+ 拉取所有远程仓库中所有分支的最新内容（通常用于同步多分支项目的全局更新） +
  
  语法格式： `git pull --all`
  
  > 示例：<br>
  > git pull --all<br>
+ 使用 rebase 模式进行合并 +
  
  语法格式： `git pull --rebase`
  
  > 示例：<br>
  > git pull --rebase<br>
  
  > 说明：<br>
  > *rebase 模式会将本地提交放到远程分支的后面，避免合并提交（使提交历史更线性）*<br>

#### **git checkout**

+ 切换到指定分支 +
  
  语法格式： `git checkout <分支名>`
  
  > 示例：<br>
  > git checkout dev<br>
+ 切换到指定提交（可用于回滚） +
  
  语法格式： `git checkout 提交哈希值` （分支名/提交哈希/main）
  
  > 示例：<br>
  > git checkout abc123<br>
+ 基于当前本地分支，创建并切换到新分支 +
  
  语法格式： `git checkout -b <新分支名>`
  
  > 示例：<br>
  > git checkout -b feature/login<br>（创建并切换到 feature/login 分支）
+ 基于远程分支，创建并切换到新分支 +
  
  语法格式： *git checkout -b <新分支名> <远程分支名>*
  
  > 示例：<br>
  > git checkout -b feature/login origin/main<br>
  > *基于 origin/main 创建并切换到 feature/login 分支*
  
  > 说明：<br>
  > *当前创建的 feature/login 关联的上游分支是 origin/main ，所以 push 时需要 `git push --set-upstream origin feature/login` 关联到远程 feature/login 分支*<br>
+ ⚠️ 撤销工作区 file 内容的修改 ⚠️ +
  
  语法格式： *git checkout -- <file>*
  
  > 示例：<br>
  > git checkout -- README.md<br>
  > git checkout .<br>
  > *撤销所有工作区文件的修改*<br>
  
  > 说明：<br>
  > *git checkout -- <file> 仅能撤销工作区未暂存的修改（即未执行 git add 的文件）。若文件已 git add 到暂存区，需先执行 `git reset HEAD <file>` 取消暂存，再用该命令撤销工作区修改*<br>

#### **git restore**

+ 用暂存区的版本覆盖工作区的修改（丢弃工作区未暂存的修改） +
  
  语法格式： `git restore <file>`
  
  > 示例：<br>
  > git restore README.md<br>
+ 从其他分支或历史提交中提取文件，直接覆盖当前工作区的对应文件（不影响暂存区） +
  
  语法格式： `git restore --source <分支名/提交哈希> <file>`
  
  > 示例：<br>
  > git restore --source dev utils.js<br>
  > git restore --source abc123 index.html<br>
+ 既用历史版本覆盖工作区，也清空该文件的暂存状态（彻底回到未修改状态，回到上一次提交状态） +
  
  语法格式： `git restore --worktree --staged <file>`
  
  > 示例：<br>
  > git restore --worktree --staged README.md<br>
+ 将指定文件取消缓存 +
  
  语法格式： `git restore --staged <file>`
  
  > 示例：<br>
  > git restore --staged README.md<br>
+ 将所有文件取消缓存 +
  
  语法格式： `git restore --staged .`
  
  > 示例：<br>
  > git restore --staged .<br>

#### **git reset**

+ 本地仓库回退到指定提交，暂存区内容被清空，工作区修改保留 +
  
  语法格式： `git reset --mixed 提交哈希值` （分支名/提交哈希/main）
  
  > 示例：<br>
  > git reset --mixed abc123<br>
+ 本地仓库回退到指定提交，暂存区内容保留，工作区不变 +
  
  语法格式： `git reset --soft 提交哈希值` （分支名/提交哈希/main）
  
  > 示例：<br>
  > git reset --soft abc123<br>
+ 本地仓库、暂存区、工作区全部回退到指定提交状态 +
  
  语法格式： `git reset --hard 提交哈希值` （分支名/提交哈希/main）
  
  > 示例：<br>
  > git reset --hard abc123<br>
+ 用 `git reset` 撤销最近n次提交 +
  
  语法格式： `git reset --<模式> HEAD~n`（n为要撤销的提交次数）
  
  > 示例：<br>
  > git reset --hard HEAD~2<br>（彻底撤销最近2次提交，工作区修改丢弃）
git reset --soft HEAD~3<br>（撤销最近3次提交，修改保留在暂存区）
+ 仅清空暂存区，本地仓库和工作区不变（等价于 `git restore --staged .`） +

语法格式： `git reset --staged .`

> 示例：<br>
> git reset --staged .<br>

#### **git status**

+ 查看当前仓库的状态（包括未暂存、暂存、未提交的修改） +
  
  语法格式： `git status`（-s 以概要形式）
  
  > 示例：<br>
  > git status<br>
+ 忽略未跟踪文件的状态显示 +
  
  语法格式： `git status --untracked-files=no`
  
  > 示例：<br>
  > git status --untracked-files=no<br>
+ 显示状态的同时，附带分支对比信息 +
  
  语法格式： `git status --branch`
  
  > 示例：<br>
  > git status --b<br>

#### **git log**

+ 查看提交历史（包括提交哈希、作者、日期、提交信息等） +
  
  语法格式： `git log`<br>
  （-p 显示每次提交的差异，--oneline 简要模式，--graph 显示分支合并图，--decorate 显示分支标签，-n 显示最近n次提交）
  
  > 示例：<br>
  > git log<br>
  > git log -p<br>

#### **git branch**

+ 查看本地所有分支 +
  
  语法格式： `git branch`<br>
  （-a 显示所有分支，包括远程分支；-r 显示远程分支；-vv 显示分支关联的远程分支）
  
  > 示例：<br>
  > git branch<br>
+ 删除分支 +
  
  语法格式： `git branch -d <分支名>`（大写 -D，等价于 --delete --force）
  
  > 示例：<br>
  > git branch -d feature/login<br>
+ 重命名分支 +
  
  语法格式： `git branch -m <旧分支名> <新分支名>`
  
  > 示例：<br>
  > git branch -m feature/login feature/login-20231201<br>
+ 查看分支的最后一次提交信息 +
  
  语法格式： `git branch -v`
  
  > 示例：<br>
  > git branch -v<br>
+ 将本地分支与远程分支关联 +
  
  语法格式： `git branch --set-upstream-to=<远程分支名>`
  
  > 示例：<br>
  > git branch --set-upstream-to=origin/main main<br>
+ 取消本地分支与远程分支的关联 +
  
  语法格式： `git branch --unset-upstream>`
  
  > 示例：<br>
  > git branch --unset-upstream-to<br>

#### **git rm**

+ 删除文件 +
  
  语法格式： `git rm <file>`
  
  > 示例：<br>
  > git rm utils.js<br>
+ 删除某个文件索引（不会更改本地文件，只会是 .gitignore 范围重新生效） +
  
  语法格式： `git rm --cached <file>`
  
  > 示例：<br>
  > git rm --cached utils.js<br>
+ ⚠️ 清除所有文件的索引 ⚠️ +
  
  语法格式： `git rm --cached .`
  
  > 示例：<br>
  > git rm --cached .<br>
  
  > 说明：<br>
  > 执行该命令后，所有未被跟踪的文件（包括已被添加到暂存区的文件）都将被从索引中移除。这意味着这些文件将不再被 Git 跟踪，也不会出现在 `git status` 或 `git diff` 中。请谨慎使用该命令，确保你不再需要这些文件的历史版本。

#### **git diff**

+ 查看暂存区与工作区的差异 +
  
  语法格式： `git diff`
  
  > 示例：<br>
  > git diff<br>
+ 查看暂存区与指定提交的差异 +
  
  语法格式： `git diff <提交哈希>`
  
  > 示例：<br>
  > git diff abc123<br>
+ 查看工作区与暂存区的差异 +
  
  语法格式： `git diff --staged`
  
  > 示例：<br>
  > git diff --staged<br>
+ 查看两个分支之间代码差异 +

语法格式： `git diff <分支1> <分支2>`

> 示例：<br>
> git diff main feature/login-20231201<br>

#### **git fetch**

+ 从远程仓库获取最新的提交记录 +
  
  语法格式： `git fetch <远程仓库名>`（默认远程仓库名为 origin）
  
  > 示例：<br>
  > git fetch origin<br>
+ 查看远程分支的最新状态 +
  
  语法格式： `git fetch --all`（-a 或 --all 显示所有远程分支）
  
  > 示例：<br>
  > git fetch --all<br>
+ 查看本地分支与远程分支的差异 +
  
  语法格式： `git fetch --dry-run`（--dry-run 模拟执行，不实际更新本地分支）
  
  > 示例：<br>
  > git fetch --dry-run<br>

#### **git merge**

+ 本地合并分支 +
  
  语法格式： `git merge <分支名>`
  
  > 示例：<br>
  > git merge feature/login-20231201<br>
+ 远程合并分支 +
  
  语法格式： `git merge <远程主机名> <分支名>`
  
  > 示例：<br>
  > git merge origin/main main<br>

#### **git revert**

+ 撤销之前的提交 +
  
  语法格式： `git revert <提交哈希>`
  
  > 示例：<br>
  > git revert abc123<br>

#### **git rebase <span class="tab-badge-red">未完成</span>**

+ 基于指定分支的新提交历史 +
  
  语法格式： `git rebase <目标分支>`
  
  > 示例：<br>
  > git rebase main<br>
+ 交互式 Rebase +
  
  语法格式： `git rebase -i <目标分支>`
  
  > 示例：<br>
  > git rebase -i main<br>

#### **git cherry-pick <span class="tab-badge-red">未完成</span>**

+ 从其他分支变动合并至当前分支 +
  
  语法格式： `git cherry-pick <提交哈希>`
  
  > 示例：<br>
  > git cherry-pick abc123<br>
+ 将多次变动变动合并至当前分支 +
  
  语法格式： `git cherry-pick <提交哈希1> <提交哈希2> ...`<br>
  （或者：commit-sha1..commit-sha5 表示从 commit-sha1 到 commit-sha5 的所有提交）
  
  > 示例：<br>
  > git cherry-pick abc123 def456 ghi789<br>

#### **git stash**

+ 暂存当前工作目录的更改 +
  
  语法格式： `git stash`
  
  > 示例：<br>
  > git stash<br>
+ 缓存代码时添加备注 +
  
  语法格式： `git stash save "备注"`
  
  > 示例：<br>
  > git stash save "修复登录问题"<br>
+ 查看暂存的更改 +
  
  语法格式： `git stash list`
  
  > 示例：<br>
  > git stash list<br>
+ 应用并删除最近的暂存更改 +
  
  语法格式： `git stash pop`
  
  > 示例：<br>
  > git stash pop<br>
+ 应用并保留最近的暂存更改 +
  
  语法格式： `git stash apply`
  
  > 示例：<br>
  > git stash apply<br>
+ 删除最近的暂存更改 +
  
  语法格式： `git stash drop stash@{n}`<br>
  （不加`stash@{n}`表示删除最近的暂存更改）
  
  > 示例：<br>
  > git stash drop stash@{0}<br>
+ 清除所有的暂存更改 +
  
  语法格式： `git stash clear`
  
  > 示例：<br>
  > git stash clear<br>

<!-- tabs:end -->

---

#### 或者看这个大佬的 [文章 🔗](https://www.cnblogs.com/jamiechoo/articles/18408791)

---

<!-- 统一容器样式，增加上下间距避免内容拥挤 -->

<div style="display:flex; gap:12px; flex-wrap:wrap; align-items:center; justify-content:center; margin:20px auto; padding:0 15px;">
  <!-- 优化跳动动画：增加缓动效果，让跳动更自然 -->
  <a href="https://www.ifdian.net/a/leoowa" target="_blank" rel="noopener noreferrer" 
     style="text-decoration:none; display:inline-block; animation: bounce 1.2s infinite ease-in-out; transition: transform 0.2s;">
    <img src="https://raw.github.com/Aleeyoo/note-gen-image-sync/main/b608f211-4aec-4994-9d43-8f80c150c21d.gif"  alt="爱发电"
         style="width:32px; height:32px; border:0; border-radius:4px; transition: opacity 0.3s;">
  </a>

<!-- 其他图标添加hover效果，提升交互感 -->

<a href="https://github.com/Aleeyoo" target="_blank" rel="noopener noreferrer" style="text-decoration:none; transition: transform 0.2s;">
    <img src="https://img.shields.io/badge/Aleeyoo-3498db?style=for-the-badge&logo=blogger&logoColor=white"  alt="GitHub"
         style="height:32px; width:auto; border:0; border-radius:4px; transition: opacity 0.3s;">
  </a>
  <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/" target="_blank" rel="noopener noreferrer" style="text-decoration:none; transition: transform 0.2s;">
    <img src="https://img.shields.io/badge/CC%20BY--NC--SA%204.0-9b59b6?style=for-the-badge&logo=creative-commons&logoColor=white"  alt="BY--NC--SA"
         style="height:32px; width:auto; border:0; border-radius:4px; transition: opacity 0.3s;">
  </a>
</div>

<style>
  /* 优化跳动动画：调整幅度和节奏，避免过于生硬 */
  @keyframes bounce {
    0%, 100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-8px); /* 减小跳动幅度，更显精致 */
    }
  }
  
  /* 统一hover效果：所有图标hover时轻微放大+提升透明度 */
  a:hover {
    transform: scale(1.05);
  }
  a:hover img {
    opacity: 0.9;
  }

