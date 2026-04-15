# GitHub Profile README 美化教程

## 原理

GitHub 有一个特殊机制：创建一个**和你用户名同名的仓库**，里面放 `README.md`，内容会自动显示在你的主页。

```
你的用户名：Pluto731
特殊仓库名：Pluto731/Pluto731
主页地址：https://github.com/Pluto731
```

---

## 第一步：创建仓库

1. 打开 https://github.com/new
2. Repository name 填写你的**用户名**（必须完全一致）
3. 选 **Public**
4. 勾选 **Add a README file**
5. 点 Create repository

---

## 第二步：了解 README 支持的内容

GitHub README 支持：
- **Markdown** 语法（标题、列表、代码块等）
- **HTML 标签**（`<div>`、`<img>`、`<pre>` 等）
- **外链图片**（通过 URL 嵌入动态 SVG 图片）

不支持：
- CSS 样式（`style=""` 属性会被过滤）
- JavaScript

---

## 第三步：核心组件详解

### 1. 动态头图 — capsule-render

服务地址：https://capsule-render.vercel.app

通过修改 URL 参数定制样式，无需任何代码：

```markdown
<img src="https://capsule-render.vercel.app/api?type=venom&height=200&text=你的名字&fontSize=60&color=0:ff6ec7,50:7873f5,100:00d4ff&stroke=00d4ff&fontColor=00d4ff&animation=twinkling" width="100%"/>
```

**关键参数：**

| 参数 | 说明 | 常用值 |
|------|------|--------|
| `type` | 形状 | `venom` `waving` `shark` `egg` `slice` |
| `color` | 颜色/渐变 | 单色：`ff6ec7`；渐变：`0:ff6ec7,100:00d4ff` |
| `height` | 高度(px) | `150` `200` `300` |
| `text` | 标题文字 | 你的名字或标语 |
| `fontSize` | 字号 | `40` `60` `90` |
| `animation` | 动画 | `twinkling` `fadeIn` `scaleIn` `blink` |
| `section` | 位置 | `header`（顶部）`footer`（底部） |

底部波浪用法（`section=footer`）：
```markdown
<img src="https://capsule-render.vercel.app/api?type=waving&height=100&color=0:ff6ec7,100:00d4ff&section=footer" width="100%"/>
```

---

### 2. 打字动画 — readme-typing-svg

服务地址：https://readme-typing-svg.demolab.com

```markdown
[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&pause=1000&color=7873F5&center=true&vCenter=true&width=600&lines=第一行文字;第二行文字;第三行文字)](https://git.io/typing-svg)
```

**关键参数：**

| 参数 | 说明 |
|------|------|
| `font` | 字体，推荐 `Fira+Code` |
| `size` | 字号 |
| `color` | 颜色（hex，不带#） |
| `center=true` | 居中显示 |
| `lines` | 轮播文字，用 `;` 分隔，空格用 `+`，中文需 URL 编码 |
| `pause` | 每行停顿时间（毫秒） |

中文 URL 编码工具：https://www.urlencoder.org/
（把中文粘进去，复制编码后的结果填进 lines 参数）

---

### 3. 技术栈图标 — skillicons.dev

```markdown
[![My Skills](https://skillicons.dev/icons?i=python,pytorch,linux,docker,git&theme=dark)](https://skillicons.dev)
```

**用法：** `i=` 后面填图标名，逗号分隔，`theme` 可选 `dark` 或 `light`

常用图标名：`python` `pytorch` `linux` `docker` `git` `github` `vscode` `tensorflow` `kubernetes` `postgres` `redis` `nginx`

完整图标列表：https://skillicons.dev

---

### 4. 自定义徽章 — shields.io

```markdown
![徽章名](https://img.shields.io/badge/显示文字-颜色?style=flat-square&logo=图标名&logoColor=white)
```

**样式（style）：**
- `flat-square` — 方形扁平
- `for-the-badge` — 大号方形
- `flat` — 圆角扁平

**颜色：** 直接填 hex（不带 #），如 `ff6ec7`

**图标名：** 在 https://simpleicons.org 搜索品牌图标

示例：
```markdown
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
```

---

### 5. 树形技能结构 — \<pre\> 标签

**注意：** emoji 放在 ` ``` ` 代码块里不会渲染，必须用 `<pre>` 标签。

```html
<pre>
技能树根节点
│
├─── 🧱  分支一
│         ├── 子项 A
│         └── 子项 B
│
└─── ⚔️  分支二
          └── 子项 C
</pre>
```

**树形字符：**
- `│` — 竖线
- `├───` — 中间分支
- `└───` — 最后分支

在 Mac/Linux 可以用 `tree` 命令自动生成目录树，然后手动加 emoji。

---

### 6. 活动折线图 — github-readme-activity-graph

```markdown
[![activity graph](https://github-readme-activity-graph.vercel.app/graph?username=你的用户名&theme=react-dark&hide_border=true&bg_color=0d1117&color=ff6ec7&line=7873f5&point=00d4ff&area=true)](https://github.com/ashutosh00710/github-readme-activity-graph)
```

**特点：** 每次有人访问主页时实时从 GitHub API 拉取，**完全自动更新，无需 GitHub Actions**。

**主题（theme）：** `react-dark` `github` `github-compact` `dracula` `tokyo-night`

**颜色参数：**
- `bg_color` — 背景色
- `color` — 文字/坐标颜色
- `line` — 折线颜色
- `point` — 数据点颜色

---

### 7. 访问量计数器 — komarev

```markdown
![Profile Views](https://komarev.com/ghpvc/?username=你的用户名&color=7873f5&style=flat-square&label=Profile+Views)
```

自动统计主页访问次数，数据存在 komarev 服务器上，不需要任何配置。

---

## 第四步：布局技巧

### 居中对齐
```html
<div align="center">

这里的内容会居中

</div>
```

### 图片并排
```html
<img height="170" src="图片1 URL" />
<img height="170" src="图片2 URL" />
```
两张图片写在同一个 `<div>` 里，height 相同就会并排显示。

### 语言切换链接
```markdown
**[English](README.md)** | **[中文](README_CN.md)**
```
两个 README 互相链接，点击跳转。中文版文件名用 `README_CN.md`。

---

## 第五步：配色方案参考

本项目使用**赛博朋克/霓虹**配色：

| 颜色 | 色值 | 用途 |
|------|------|------|
| 霓虹粉 | `ff6ec7` | 标题、重点 |
| 极光紫 | `7873f5` | 次要元素、折线 |
| 赛博青 | `00d4ff` | 数据点、描边 |
| 深黑底 | `0d1117` | 卡片背景（GitHub 深色背景色） |

渐变写法：`0:ff6ec7,50:7873f5,100:00d4ff`（位置:颜色，逗号分隔）

---

## 目录结构

```
Pluto731/              ← 仓库名 = 用户名
├── README.md          ← 英文版（主页默认显示）
├── README_CN.md       ← 中文版
└── GUIDE.md           ← 本教程
```

---

## 常见问题

**Q: emoji 在技能树里不显示？**
A: 把 ` ``` ` 换成 `<pre>` 标签，emoji 在代码块里会被当纯文本处理。

**Q: 图片加载很慢或显示不出来？**
A: 这些服务都是免费的 Vercel 部署，国内访问有时不稳定，刷新几次一般能好。

**Q: 需要 GitHub Actions 吗？**
A: 本方案所有组件（头图、打字动画、活动图、访问量）都是**实时 API 请求**，不需要 Actions，不受 billing 限制。

**Q: 改了 README 多久生效？**
A: push 后立刻生效，刷新主页即可看到。
