# 怎么发布这套图

两条路都能走通：**网页上传**（不用装任何东西，图里这几步就是这么做的）和 **命令行**（改得多了更顺手）。第一次做建议先走第一条，五分钟能出结果。

---

## 一、网页上传（零安装，推荐第一次用）

### 1. 建仓库

1. 浏览器打开 <https://github.com/new>，登录自己的账号。
2. **Repository name** 填个名字，比如 `ai-collab-workflow-diagrams`。
3. 可见性选 **Public**（要开免费 Pages 就得是公共仓库；私有仓库开 Pages 需要付费账号）。
4. 下面三个初始化选项（README / .gitignore / license）**全都不勾**，先建个空仓库。
5. 点 **Create repository**。

### 2. 传文件

1. 仓库页点 **上传现有文件**（add file → upload files），地址变成 `.../upload`。
2. 点 **选择文件**，在弹出的系统对话框里**多选**要传的文件：
   - 想批量选，在「文件名」框里直接敲带引号的名字，用空格隔开，例如
     `"index" "human-ai-collab-workflow" "human-ai-collab-structure" "README"`
     回车即可一次选中多个；或者点第一个文件再按住 Ctrl 点其它文件。
3. 文件进了待提交列表后，在下面 **提交更改** 的输入框里写一句说明（比如"新增导航页"），点 **提交更改**。

> 上传对话框默认一次最多 100 个文件、单个文件 25 MB 以内。这两个 HTML 各约 850 KB，随便传。

### 3. 开 Pages

1. 进仓库 **Settings → Pages**（地址是 `.../settings/pages`）。
2. **Source** 选 **Deploy from a branch（从分支部署）**。
3. **Branch** 选 `main`，右边的目录选 `/ (root)`，点 **Save**。
4. 页面顶部会跳出"GitHub Pages source saved"，这时侧栏会出现一条 **Deployments · github-pages**。等它跑完（一般十几秒到两分钟）。

### 4. 访问

网址规则是固定的：

```
https://<你的用户名>.github.io/<仓库名>/
```

导航页就是根网址；两张图分别是
`.../human-ai-collab-workflow.html` 和 `.../human-ai-collab-structure.html`。

---

## 二、命令行（改得多了再用）

### 前置检查

```powershell
git --version      # 没装就先装 https://git-scm.com/download/win
gh --version       # 可选，装了能省掉手动建仓库
```

**Git 第一次用必须配身份**，否则 commit 会直接报错：

```powershell
git config --global user.name  "你的名字"
git config --global user.email "你的邮箱"
```

### 仓库已经建好的情况

**不要用 `git init` 再来一遍。** 远程已经有 commit 了，本地 init 出来的历史跟它没关系，push 会被拒（`non-fast-forward`）。正确做法是**先 clone**：

```powershell
git clone https://github.com/<用户名>/<仓库名>.git
cd <仓库名>
# 把改好的文件覆盖进来
git add -A
git commit -m "说明这次改了什么"
git push
```

第一次 `push` 会弹浏览器让你授权一次，授权完以后就不用再输了。

### 从零开始（本地有文件、远程还没仓库）

```powershell
cd 你的项目目录
git init
git add -A
git commit -m "init"
git branch -M main
git remote add origin https://github.com/<用户名>/<仓库名>.git
git push -u origin main
```

---

## 三、几个容易踩的坑

| 坑 | 现象 | 怎么办 |
| --- | --- | --- |
| 首页文件名不对 | 根网址显示的是 README 排版，不是导航页 | 导航页必须**正好**叫 `index.html`，大小写敏感 |
| 中文文件名 | 网址变成 `%E4%BA%BA%E5%B7%A5...` 一长串 | 文件名用英文，中文只放在页面内容里 |
| 刚提交就刷新 | 看到的还是旧页面 | 等 Deployments 那条跑完；没好就 Ctrl+F5 强刷 |
| 私有仓库开 Pages | 设置里根本找不到开启入口 | 改公共仓库，或者升级付费账号 |
| push 被拒 non-fast-forward | `Updates were rejected` | 远程已有提交，先 `git pull --rebase` 再 push，别 `--force` |
| 传上去打不开 | 404 | 检查 Pages 的 Branch 是不是 `main`、目录是不是 `/ (root)` |

---

## 四、以后怎么改

改图有两种方式：

- **改文字**：直接用记事本 / VS Code 打开 HTML，搜要改的那句话改掉（图片本身是 SVG，文字都是文本节点，不是像素）。
- **重画**：用 archify 生成新的 HTML，覆盖同名文件再上传。

改完走一遍第 2 步（网页上传）或第二条路的 `add / commit / push`，Pages 会自动重新构建。

---

## 许可证

本仓库用 [MIT](LICENSE)。要拿去改成自己的版本，直接改、改名、改配色都行，保留版权声明即可。
