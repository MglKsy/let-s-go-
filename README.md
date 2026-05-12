# 新电脑 SSH 克隆 + 修改 + 推送 完整终极流程

（全程复制粘贴，一步到位，公司标准用法）

---

# 第一步：新电脑生成 SSH 密钥（只做一次）

打开终端，执行：

```bash
ssh-keygen -t ed25519 -C "你的GitHub邮箱"
```

一路回车 3 次，不要设置密码。

---

# 第二步：复制公钥（.pub 那个）

```bash
cat ~/.ssh/id_ed25519.pub
```

把输出的一整串内容全部复制。

---

# 第三步：把公钥添加到 GitHub

打开 GitHub：

- 头像
- Settings
- SSH and GPG keys
- 点击 `New SSH key`
- 粘贴刚才复制的内容
- 保存

---

# 第四步：测试连接是否成功

```bash
ssh -T git@github.com
```

看到：

```text
Hi MglKsy! You've successfully authenticated...
```

✅ 成功！

---

# 第五步：克隆项目到新电脑

```bash
git clone git@github.com:MglKsy/let-s-go-.git
```

进入项目：

```bash
cd let-s-go-
```

---

# 第六步：修改代码

随便改个文件，比如：

```text
README.md
```

---

# 第七步：提交并推送

```bash
git add .
git commit -m "新电脑修改代码"
git push
```

✅ 完成！代码直接上传 GitHub！

---

# 超级重要总结（你必须记住）

- 一台电脑 = 生成一次密钥 = 永久使用
- 所有项目共用同一个密钥
- 新项目不用重新生成
- `git push` 永远免密
- 这就是公司多人协作标准流程





# 新项目完整流程（你照着抄，永远不会错）

### 第一步：本地新建项目文件夹

bash

运行

```
git init
```

### 第二步：**去 GitHub 网页上新建一个空仓库**

（必须新建！不能用老的！）

### 第三步：把本地新项目关联到**新仓库**

bash

运行

```
git remote add origin git@github.com:你的用户名/新项目仓库.git
```

### 第四步：提交推送

bash

运行

```
git add .
git commit -m "新项目初始化"
git push -u origin main
```

