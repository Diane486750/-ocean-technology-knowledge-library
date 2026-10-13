# 海技知识库 · 静态浏览站

本目录由 `run.py export-site` 自动生成，**只读浏览**（上传/抽取需要在本地电脑上跑）。

- 数据文件：1746 个
- 课件页图：1604 张（WebP 压缩）
- 程序生成示意图：189 张
- 总体积：约 92.5 MB

---

## 一、本地预览

双击上一级目录的 **`预览静态站.bat`**（会自动开浏览器）。
或者手动：本目录下 `python -m http.server 8099`，然后访问 http://127.0.0.1:8099

---

## 二、部署到云端（三选一）

### 🥇 方案 A：Netlify Drop —— 最省事，啥都不用装（推荐先试这个）

1. 打开 https://app.netlify.com/drop
2. 把 **整个 `dist` 文件夹**拖进网页
3. 等 1~2 分钟 → 得到一个网址，立刻能看
4. 想长期保留：注册免费账号（邮箱即可），站点就永久归你了

> 优点：不用装 git、不用命令行。缺点：网址是随机串（可在设置里改名）。

### 🥈 方案 B：Cloudflare Pages —— 长期最合适，还能加门禁

1. 注册免费 Cloudflare 账号
2. 控制台 → Workers & Pages → Create → **Pages** → **Upload assets（直接上传）**
3. 拖入 `dist` 文件夹 → 部署
4. 得到 `https://<项目名>.pages.dev`

> **加门禁**（只有同学的邮箱能看）：项目 → Settings → Access policy →
> 开启 Cloudflare Access，填允许的邮箱（免费额度 50 人）。
> 这样教材扫描页就不会被陌生人看到，也不违反「同学间自用」。

### 🥉 方案 C：GitHub Pages —— 你最初选的，但需要先装 git

```bash
# 1) 装 git：https://git-scm.com/download/win  （一路下一步）
# 2) 注册 GitHub 账号：https://github.com/signup
# 3) 在 GitHub 上新建一个仓库（Public），拿到仓库地址
# 4) 开 PowerShell：
cd D:\2 学习整合\dist
git init
git add -A
git commit -m "update knowledge base"
git branch -M main
git remote add origin https://github.com/<你的用户名>/<仓库名>.git
git push -u origin main
```
然后：仓库 → Settings → Pages → Source 选 `main` / `/(root)` → Save。
1 分钟后访问 `https://<用户名>.github.io/<仓库名>/`

> ⚠️ **GitHub Pages 仓库必须公开** = 教材扫描页也会公开到互联网。
> 若不想公开：改用方案 B 加门禁，或先跑 `run.py export-site --no-pages`
> 生成纯文字版（约 3MB）再上传。

---

## 三、以后怎么更新

1. 本地跑新的资料（`一键处理.bat` → `抽取知识点.bat` → `生成考点.bat`）
2. 双击 `导出静态站.bat` 重新生成 `dist`
3. 把 `dist` 重新拖上去（方案 A/B），或 `git add -A && git commit && git push`（方案 C）
