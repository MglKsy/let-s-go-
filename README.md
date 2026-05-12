# 我的第一个项目
🚀 新电脑 SSH 配置与 Git 开发终极流程
核心逻辑： 一台电脑 = 生成一次密钥 = 永久免密使用。

第一步：生成 SSH 密钥（全局仅一次）
打开终端（Terminal 或 Git Bash），执行以下命令：

Bash
ssh-keygen -t ed25519 -C "你的GitHub邮箱"
操作建议： 一路回车 3 次，不要设置密码。

优势： ed25519 算法比传统的 rsa 更安全且更短。

第二步：获取公钥内容
执行命令查看并复制你的公钥：

Bash
cat ~/.ssh/id_ed25519.pub
注意： 必须复制以 ssh-ed25519 开头的整行内容。

第三步：将公钥添加到 GitHub
登录 GitHub，点击右上角头像 → Settings。

左侧侧边栏选择 SSH and GPG keys。

点击 New SSH key。

Title 随便填（如：My-MacBook-Pro），Key 粘贴刚才复制的内容。

点击 Add SSH key 保存。

第四步：验证连接
在终端输入：

Bash
ssh -T git@github.com
关键点： 如果提示 Are you sure you want to continue connecting (yes/no/[fingerprint])?，请输入 yes 并回车。

成功标志： 看到 Hi [用户名]! You've successfully authenticated...

第五步：克隆项目（SSH 协议）
找到你的 GitHub 项目，确保复制的是 SSH 链接（以 git@github.com 开头）：

Bash
git clone git@github.com:MglKsy/let-s-go-.git
cd let-s-go-
第六步：首次配置 Git 用户信息
如果是新电脑，必须告诉 Git 你是谁，否则无法提交：

Bash
git config --global user.name "你的用户名"
git config --global user.email "你的GitHub邮箱"
第七步：修改、提交与推送
在本地修改代码后，执行标准三连操作：

Bash
# 1. 添加修改
git add .

# 2. 本地提交
git commit -m "feat: 新电脑首次代码修改"

# 3. 推送到远程仓库
git push
💡 必看 Tips：

免密原理： 只要你使用的是 git@github.com:... 这种 SSH 地址克隆的代码，后续所有的 push 和 pull 都不需要输入账号密码。

多项目复用： 以后克隆新项目，直接从 第五步 开始即可，无需重复生成密钥。

安全性： .pub 文件是公钥（给 GitHub 的），id_ed25519（不带后缀）是私钥，绝对不能给别人。
