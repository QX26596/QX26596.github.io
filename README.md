# 个人主页（GitHub Pages）

一套零依赖的单页个人主页模板。全站只有 `index.html` 一个文件需要改。

本仓库对应的账号是 **QX26596**，站点地址将是 `https://qx26596.github.io`。

> **当前状态：仓库被建成了 `lingran798.github.io`，与账号名不匹配。**
>
> 因此 GitHub 没把它当「个人主站」，只当普通项目站处理，实际可访问地址是
> `https://qx26596.github.io/lingran798.github.io/`（已实测返回 200）。
>
> 根域名 `https://qx26596.github.io/` 目前是 404 —— 要拿到这个干净地址，
> 需要把仓库改名，见文末「改名成个人主站」。

## 需要改的地方

页面里现在**全是占位文案，不含任何真实个人信息**。替换时搜下面这几个关键词即可定位：

| 关键词 | 位置 | 说明 |
| --- | --- | --- |
| `你的名字` | 标题、页头 h1、页脚 | 换成你想展示的名字或昵称 |
| `一句话介绍你自己` | 页头标语 | 一行说明你在做什么 |
| `your@email.com` | 页头第一个链接 | 邮箱 |
| `你的用户名` | 页头 GitHub 链接 | 换成 GitHub 用户名 |
| `20XX` | 教育背景、项目、荣誉 | 年份 |

五个板块（关于我 / 教育背景 / 方向与技能 / 项目精选 / 荣誉与专利）都是占位内容，不需要的整段删掉即可，样式不会乱。

想加一个项目：复制一个 `<article class="card">...</article>` 块就行，卡片会自动排成网格。

想换配色：改 `<style>` 开头 `:root` 里的几个变量即可（深色模式对应下面 `@media` 块里的同名字段）：

| 变量 | 用途 |
| --- | --- |
| `--c1` / `--c1-soft` | 主色（靛蓝），用于顶部色条、头像、主按钮、`01` 关于我 |
| `--c2` / `--c2-soft` | 辅助色（青绿），用于 `02` 教育背景的时间线圆点 |
| `--c3` / `--c3-soft` | 辅助色（紫），用于 `03` 方向与技能 |
| `--c4` / `--c4-soft` | 辅助色（品红），用于 `04` 项目精选 |
| `--c5` / `--c5-soft` | 辅助色（琥珀），用于 `05` 荣誉与专利 |

正文字号、板块间距、圆角分别由 `body` 的 `font-size`、`section` 的 `padding`、`--radius` 控制。


> **隐私提醒**：这个仓库是公开的，页面内容会被发布到公网。**不要**在页面里写手机号、身份证号、学号、家庭住址、未公开的论文或实验数据。


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

## 关于可见性（常见误解）

- 仓库的 **Public / Private 是每个仓库各自独立**的属性。改名只影响被改名的那一个仓库，其他项目的可见性一个字都不会变。
- 这个站点仓库**必须**是 Public：GitHub 免费账号只允许公开仓库启用 Pages。所以「网站公开 + 仓库私有」在免费版做不到（GitHub Pro 能让私有仓库开 Pages，但发布出去的网站内容依然是公开的，只是源代码不公开）。
- Pages 只发布 `QX26596.github.io` 这一个仓库里的文件。其他私有仓库的代码**不会**出现在网站上，也**不会**因此变成公开。
- 唯一要当心的：不要往这个站点仓库里放 API key、token、未公开的实验数据或论文材料 —— 它的内容会被发布到公网。

## 网址是怎么定下来的

**域名永远由账号名决定，与仓库名无关。**

- 账号是 `QX26596`，所以域名永远是 `qx26596.github.io`，不会因为仓库怎么叫而改变
- 仓库名只决定「谁去占用这个域名的根」：
  - 仓库名 == `qx26596.github.io` → 识别为**用户主站** → 地址 `https://qx26596.github.io`
  - 仓库名是别的 → 识别为**项目站** → 地址 `https://qx26596.github.io/<仓库名>`

所以改名前后网址会变：

| 状态 | 仓库名 | 判定 | 网址 |
| --- | --- | --- | --- |
| 改名前 | `lingran798.github.io` | ≠ 账号名 → 项目站 | `https://qx26596.github.io/lingran798.github.io/` |
| 改名后 | `QX26596.github.io` | = 账号名 → 用户主站 | `https://qx26596.github.io` |

规定这么死是为了防止有人用仓库名去占用别人账号的域名根 —— 否则任何人都能冒充别人的主页。**`<X>.github.io` 的根永远只属于账号名为 X 的人。**

## 想用 `https://lingran798.github.io/` ？

**唯一办法：把账号用户名改成 `lingran798`。**

- 实测 `https://github.com/lingran798` 返回 Page not found，说明**这个用户名目前没人占用**
- 操作：`Settings → Account → Change username`
- 改完后，已有的 `lingran798.github.io` 仓库会**自动**被识别为用户主站（仓库名与账号名对上了），`https://lingran798.github.io` 直接生效，不用再建仓库
- 实测 `https://lingran798.github.io/` 现在是 404，说明该根域名目前没有主站

改用户名的代价：

- 所有仓库网址变成 `github.com/lingran798/xxx`；旧链接 GitHub 会做跳转，但不是永久的
- 旧用户名会被释放，可能被别人注册
- 本地克隆过的仓库要更新远程地址：`git remote set-url origin https://github.com/lingran798/仓库名.git`
- 已写在简历、申请表、名片上的 `QX26596` 链接会失效
- GitHub 对频繁改名有限制，改之前想清楚

> 如果只是想要个好看的网址，更省事的办法是买一个自己的域名（几十元/年），
> 在 `Settings → Pages → Custom domain` 绑定 —— 比任何 `github.io` 子域名都更专业。

## 方案对比：保持现状 vs 改名

两种都能用，都能正常访问，区别只在网址好不好看。

| | 保持现状 | 改名成 `QX26596.github.io` |
| --- | --- | --- |
| 站点地址 | `https://qx26596.github.io/lingran798.github.io/` | `https://qx26596.github.io` |
| 现在能用吗 | 能，已实测返回 200 | 改名后 1–10 分钟生效 |
| 根域名 `qx26596.github.io` | 永远 404 | 变成你的主页 |
| 需要做什么 | 什么都不用做 | 改一次仓库名 |
| 适合场景 | 自己看、随手分享给同学 | 写进简历、申请材料、名片 |

另外三点：

- **其他仓库不受任何影响。** 实测 `https://qx26596.github.io/desktop-tutorial/` 和 `https://qx26596.github.io/test/` 都是 404 —— 没在 `Settings → Pages` 里开启发布的仓库，根本不会被发布出去。
- **一个账号只有一个「用户主站」名额**（即名为 `<账号名>.github.io` 的仓库）。保持现状的话，将来想要干净域名有两条路：给这个仓库改名，或者另建一个仓库叫 `QX26596.github.io` 当主页 —— 两者可以并存，前者仍是项目站。
- **子路径站点的路径注意**：以后往页面里加图片，要写相对路径 `img/a.png`，不要写 `/img/a.png`。后者会跑到根域名去找，在子路径站点里会 404。

## 改名成个人主站（推荐）

仓库建错名字不用删除重建，改名即可，历史记录和文件都在。

1. 打开仓库 → `Settings` → `General`（默认就在这一页）
2. 最上方 **Repository name** 把 `lingran798.github.io` 改成 **`QX26596.github.io`**
3. 点 **Rename**
4. 回到 `Settings → Pages`，确认 Source 仍是 `Deploy from a branch` / `main` / `/ (root)`；如果掉了就重选一次并 Save
5. 等 1–10 分钟，访问 `https://qx26596.github.io`

改名后会发生三件事：

- 新地址 `https://qx26596.github.io` 生效，这是你要的个人子域名
- 旧地址 `https://qx26596.github.io/lingran798.github.io/` 失效（仓库网页地址 GitHub 会自动跳转，但 Pages 站点不会）
- 本地仓库（如果你 clone 过）需要更新远程地址：

```bash
git remote set-url origin https://github.com/QX26596/QX26596.github.io.git
git remote -v
```

> 如果十分钟后根域名还是 404，把仓库名改成全小写 `qx26596.github.io` 再试一次，然后回 Pages 页面重新保存一次发布源。

