## 华为Python培训

#### 第一章Git基础与实操

- 最开始出现的工具
  - diff  
  - patch
- RCS：最早期的本地版本控制工具
  - 只适合本地的版本控制
- CVS&SVN：集中式版本控制工具
  - 只记录之后所有内容的差异
- Git
  - GIt像是把数据看作是小型文件系统的一组快照
  - 每次提交更新，或在GIT中保存项目状态时，它主要对当时的全部文件制作一个快照并保存这个快照的索引
  - 为了高效，如果文件没有修改，Git不再重新存储该文件，二十只保留一个链接指向之前存储的文件。Git对待数据更像是一个快照流
- 命令补齐
  - Linux的shell环境(bash)通过bash-completion软件包提供命令补齐的功能，能够实现在录入命令参数时按一下或两下TAB键，实现参数的自动补齐或提示。例如输入git com后按下TAB键，会自动补齐git commit
- git安装
- git 基本配置
  - 系统配置（对所有用户都适用）
    - 存放在git的安装目录下：%Git%/etc/gitconfig：若使用git config 时用 --system选项，读写的就是这个文件：git config --system core.autocrlf
  - 用户配置（只适用于该用户）
    - 存放在用户目录下，例如linux存放在：~/.gitconfig：若使用git config时用 --global选项，读写的就是这个文件：git config --global user.name
  - 仓库配置（只对当前项目有效）
    - 当前仓库的配置文件（也就是工作目录中的.git/config文件）；若使用git config时用 --local选项，读写的就是这个文件git config --local remote.origin.url
  - 配置个人身份（首次的git设定，设定身份，自己做主）——责任追踪/应用之间的用户关联/贡献度统计
    - git config --global user.name "Zhang San"
    - git config --global user.email zhangsan123@163.com
  - 文本换行符配置
    - git config --global core.autocrlf true/input/false
    - 结束符问题，Windows系统都是以CRLF结束，而Mac或Linux系统时以LF结束
  - 文本编码配置
    - i18n.commitEncoding选项：用来让git commit log存储时，采用的时编码，默认时UTF-8
    - i18n.logOutputEncoding选项：查看git log时，显示采用的编码，建议设置为UTF-8
  - 与服务器的认证配置
    - 常见的两种协议认证方式
    - http/https协议认证
      - 设置口令缓存：git config --global credential.helper store
      - 添加HTTPS证书的信任：git config http.sslverify false
    - ssh协议认证
      - SSH协议是一种非常常用的Git仓库访问协议，使用公钥认证、无需输入密码，加密传输，操作便利又保证安全性
      - ![image-20230328121820023](C:\Users\于志强\AppData\Roaming\Typora\typora-user-images\image-20230328121820023.png)



- git版本控制下的三种工程区域&文件状态

  - 版本库(Repository)：在工作区中有一个隐藏目录.git，这个文件夹就是Git的版本库，里面存放了Git用来管理该工程的所有版本数据，也可以叫做本地仓库
  - 工作区（Working Directory）：日常工作的代码文件或者文档所在的文件夹
  - 暂存区（stage）：一版存放在工程根目录.git/index文件中，所以我们也可以把暂存区叫做索引(index)
  - 三种文件状态：已提交，已修改，暂存（待提交）

- git常用命令

  - git init 初始化一个git文件
  - git clone 克隆远端工程到本地磁盘
  - git add/ git rm /git mv / 
  - git dff
    - ![image-20230328124853080](C:\Users\于志强\AppData\Roaming\Typora\typora-user-images\image-20230328124853080.png)
  - git status 命令用于显示工作目录和暂存区的状态
    - ![image-20230328155416767](C:\Users\于志强\AppData\Roaming\Typora\typora-user-images\image-20230328155416767.png)
  - git commit **主要是将暂存区里的文件改动提交到本地的版本库**
    - 提交这个动作只是本地动作，是往本地版本库中记录改动，不影响远端服务器。
    - git commit file_name -m "commit message"
    - git commit -am "commit message"
    - git commit --amend 修改
  - git log 用于查看提交历史
  - git push
    - 在实用 git commit 命令将自己的修改从缓存区提交到本地仓库后，可以实用git push将本地版本库的分支推送到远程服务器上对应的分支
    - git push origin branch_name，**origin是远端服务器名称**
  - git 分支管理
    - **git branch 命令即可以查看本地工程的所有git分支名称**
    - ![image-20230328160921968](C:\Users\于志强\AppData\Roaming\Typora\typora-user-images\image-20230328160921968.png)
    - git branch -d 和git branch -D都可以用来删除本地分支，后者大写表示强制删除
    - git checkout 命令除了创建分支，还用来切换分支，当然比较官方的叫法叫“检出”
    - git checkout branch_name   git checkout -f 强制切换
    - git pull 从远端服务器中获取某个分支的更新，**再与本地指定的分支进行自动合并**
    - git pull origin remote_branch:local_branch     git pull origin remote_branch
    - git fetch 从远端服务器中获取某个分支的更新到本地仓库，这样能留给用户一个操作空间，确认git fetch内容符合预期后，决定是否手动合并节点。git fetch origin remote_branch:local_branch
    - git merge 命令是用于从指定的分支（节点）合并到当前分支的操作，差异的内容合并过来  git merge branch_name
    - git rebase 用于合并目标分支内容到当前分支
    - git reset 通常用于撤销当前工作区中某些git add/commit操作，可以将工作区内容回退到历史提交节点。常用的工作区回退命令格式 git reset commit_id
    - git checkout . 用于回退本地所有修改而未提交的文件内容。git checkout . 这是条有风险的命令，因为他会取消本地工作区的修改（相对于暂存区），用暂存区的所有文件直接覆盖本地文件，达到回退内容的目的。但它不给任何用户确认的机会，所以谨慎使用。git check -filename ；如果想将工具去回退（检出）到某个提交版本，可以使用git checkout commit_id
  - 本地基本提交推送
  - 基本分支与节点更新
    - git fetch 只是将远端仓库拉到本地
    - git pull 将远端仓库拉到本地并进行合并
    - git fetch + git merge = git pull
    - git cherry-pick 
  
  - 合并的冲突处理
    - 什么时候分支合并会产生冲突：两个差异的节点存在，同时两个差异文件修改了文件中相近的行
  
  - git代码平台上添加SSH公钥
    - 先在本地生成公钥
    - 然后将公钥添加到代码平台
    - 再进行克隆
  
  
  





