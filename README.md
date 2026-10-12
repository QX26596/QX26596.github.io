# 个人主页（GitHub Pages）

一套零依赖的单页个人主页模板。全站只有 `index.html` 一个文件需要改。

本仓库对应的账号是 **QX26596**，站点地址将是 `https://qx26596.github.io`。

## 需要改的地方

1. **`index.html` 里的个人信息** —— 打开文件，凡是注释 `<!-- 改这里 -->` 附近的内容都按需替换。
2. **项目卡片** —— 在「项目经历」区块里复制一个 `<article class="card">...</article>` 就是一个新项目。

配色会自动跟随访问者系统的浅色/深色模式，无需配置。想换主色调，改 `<style>` 里的 `--accent`。

## 上线步骤

### 第一步：在 GitHub 建仓库

1. 登录 GitHub，右上角 `+` → **New repository**
2. Owner 选 **QX26596**
3. Repository name 填 **`QX26596.github.io`**
   - 必须和账号名完全一致，前面换成任何别的名字都开不出个人主站
   - 如果这里报 `Something went wrong!`，多半就是名字填错了，或者被浏览器扩展拦了，见文末排错
4. 可见性选 **Public**（免费账号只有公开仓库能开 Pages）
5. **不要**勾 Add README / .gitignore / license（本地已有文件，勾了推送时会冲突）
6. 点 Create repository

### 第二步：把文件推上去

在本文件夹执行：

```bash
git init
git add .
git commit -m "init homepage"
git branch -M main
git remote add origin https://github.com/QX26596/QX26596.github.io.git
git push -u origin main
```

首次推送会弹出登录窗口，用浏览器授权即可。如果 GitHub 上已经初始化过 README，先执行 `git pull --rebase origin main` 再推。

### 第三步：开启 Pages

仓库页 → `Settings` → 左侧 `Code and automation` → `Pages`
- Source：`Deploy from a branch`
- Branch：`main`，目录选 `/ (root)`
- 点 **Save**

### 第四步：等待生效

1–10 分钟后访问 `https://qx26596.github.io`。

以后每次改完文件，只要：

```bash
git add .
git commit -m "update"
git push
```

## 本文件夹里的文件

| 文件 | 作用 |
| --- | --- |
| `index.html` | 网站首页，内容都在这里 |
| `.nojekyll` | 空文件，告诉 GitHub 不要用 Jekyll 处理，避免下划线开头的文件被忽略 |
| `README.md` | 本说明文件，不会被当成首页（有 index.html 优先） |

## 排错

### 建仓库时提示 `Something went wrong!`

这是 GitHub 最含糊的一个报错，按顺序排查：

1. **仓库名是否等于账号名 + `.github.io`** —— 必须一字不差。账号是 `QX26596`，仓库名就只能是 `QX26596.github.io`（`lingran798.github.io` 这种名字属于别的账号，GitHub 不会给）
2. **换无痕窗口试** —— 广告拦截类扩展（AdBlock、uBlock、CORS 类插件）会导致这个报错，这是最常见的原因
3. **Ctrl + F5 强刷页面** —— 页面停留太久，提交令牌会过期
4. **确认邮箱已验证** —— `Settings → Emails`，状态要是 Verified
5. **换网络或稍等几分钟** —— 新注册账号可能触发安全校验，GitHub 服务抖动也会这样

> 想用 `lingran798.github.io` 这个名字，唯一的办法是把账号用户名改成 `lingran798`：`Settings → Account → Change username`。改完用户名后旧链接会失效，需要自己权衡。

### 其他常见问题

- 网址打不开或 404：确认仓库名和账号名完全一致，且 Pages 里已经选了分支并保存
- 页面显示的不是你的网页：仓库里没有 `index.html`（检查文件名拼写和大小写）
- 推送后没变化：去仓库的 `Actions` 标签看 Pages 构建状态，不要反复强刷浏览器
- 想用自定义域名：`Settings → Pages → Custom domain`，DNS 配 A 记录指向 `185.199.108.153 / .109.153 / .110.153 / .111.153`，或 www 的 CNAME 指向 `qx26596.github.io`
