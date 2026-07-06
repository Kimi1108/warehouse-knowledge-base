# 📦 仓储知识库 — GitHub Pages 完整操作指导书

> 版本：v1.0 | 日期：2026-07-06 | 适用范围：个人学习和团队共享

---

## 目录

1. [概述](#1-概述)
2. [前置准备](#2-前置准备)
3. [一键部署](#3-一键部署)
4. [手动部署（备选）](#4-手动部署备选)
5. [日常维护](#5-日常维护)
6. [内容更新指南](#6-内容更新指南)
7. [自定义域名](#7-自定义域名)
8. [常见问题](#8-常见问题)
9. [技能包使用](#9-技能包使用)

---

## 1. 概述

你的仓储知识库已包含 **7大板块、6份专业参考文档**，覆盖：

| 板块 | 内容量 | 适用场景 |
|------|:------:|---------|
| 🏠 首页总览 | 市场数据+趋势+误区 | 快速了解行业全貌 |
| 🤖 仓储自动化 | AGV/AMR/ASRS/数字孪生/9家厂商 | 设备选型和技术调研 |
| 💻 WMS选型 | 10款产品对比+5大维度 | 系统选型决策 |
| 📋 最佳实践 | Lean/5S/布局/拣选/KPI | 日常运营提升 |
| 🏭 行业案例 | 电商/制造/医药/冷链/新能源/化工 | 行业方案参考 |
| 📐 体系标准 | IATF 16949/VDA 6.3/ISO 45001/27001 | 审核准备 |
| 🚗 客户审核 | 奔驰/宝马/大众/丰田/现代 | 客户验厂准备 |

---

## 2. 前置准备

### 2.1 你需要的东西

| 项目 | 说明 | 获取方式 |
|------|------|---------|
| GitHub 账号 | 免费即可 | https://github.com/signup |
| 网络环境 | 能访问 GitHub | - |
| 5分钟时间 | 首次部署 | - |

### 2.2 登录 GitHub CLI

在终端运行以下命令，然后按提示操作：

```bash
gh auth login
```

选择以下选项：
```
? What account do you want to log into?  GitHub.com
? What is your preferred protocol?      HTTPS
? Authenticate with credentials?        Login with a web browser
```

浏览器会自动打开，点击授权即可。

---

## 3. 一键部署

登录 GitHub 后，运行部署脚本：

```bash
bash /root/.codebuddy/artifact/5881073d-f6eb-4b2d-ade2-7df8d6f8092e/setup_github.sh <你的GitHub用户名>
```

**示例**：
```bash
bash /root/.codebuddy/artifact/5881073d-f6eb-4b2d-ade2-7df8d6f8092e/setup_github.sh zhangsan
```

脚本会自动完成：
1. ✅ 创建 GitHub 公开仓库 `warehouse-knowledge-base`
2. ✅ 上传网站文件和 README
3. ✅ 自动启用 GitHub Pages
4. ✅ 输出访问地址

---

## 4. 手动部署（备选）

如果自动脚本失败，可以手动操作：

### 第一步：创建仓库

访问 https://github.com/new

- Repository name: `warehouse-knowledge-base`
- 选择 Public（公开）
- 不要勾选任何初始化选项

### 第二步：上传文件

```bash
# 进入知识库目录
cd /tmp
mkdir warehouse-kb-upload && cd warehouse-kb-upload
cp /workspace/warehouse-kb/index.html .

# 初始化 Git
git init
git checkout -b main
git add index.html
git commit -m "初始化仓储知识库"

# 关联远程仓库并推送
git remote add origin https://github.com/<你的用户名>/warehouse-knowledge-base.git
git push -u origin main
```

### 第三步：启用 GitHub Pages

1. 访问 `https://github.com/<你的用户名>/warehouse-knowledge-base/settings/pages`
2. Source 选择 **Deploy from a branch**
3. Branch 选择 **main**，目录选择 **/ (root)**
4. 点击 **Save**
5. 等待 1-5 分钟，页面顶部会出现你的网址

---

## 5. 日常维护

### 5.1 查看你的知识库

访问：`https://<你的用户名>.github.io/warehouse-knowledge-base/`

> 💡 **建议**：把地址收藏到浏览器书签，手机也能随时查看。

### 5.2 克隆仓库到本地

如果你有自己的电脑，可以克隆仓库到本地编辑：

```bash
git clone https://github.com/<你的用户名>/warehouse-knowledge-base.git
cd warehouse-knowledge-base
```

### 5.3 更新内容流程

```
本地修改 index.html
       ↓
git add index.html
       ↓
git commit -m "更新了XX内容"
       ↓
git push
       ↓
等待 1-2 分钟自动部署
```

---

## 6. 内容更新指南

### 6.1 如何修改内容

知识库是一个**单个 HTML 文件**（`index.html`），所有内容都在里面。

| 想改什么 | 怎么改 |
|----------|--------|
| 加一个新的导航标签 | 在 `<nav><ul>` 区域内添加 `<li><a>` |
| 加一个新的内容区块 | 添加 `<section id="xxx" class="content-section">...</section>` |
| 修改表格数据 | 找到对应 `<table>` 区域，修改 `<td>` 里的内容 |
| 修改标题/段落 | 搜索对应文字直接改 |
| 修改样式 | 修改 `<style>` 块内的 CSS |

### 6.2 使用 AI 辅助更新

之后想更新内容时，直接把需求告诉我（或任意 AI 助手），比如：

> "帮我在客户审核板块加上特斯拉的审核要求"
> "更新市场规模数据到2027年"
> "把蓝色主题改成绿色"

然后把生成的 `index.html` 替换即可。

### 6.3 建议更新频率

| 内容 | 更新频率 | 说明 |
|------|:--------:|------|
| 市场数据 | 每季度 | 市场报告发布后更新 |
| 厂商信息 | 半年 | 新产品和厂商动态 |
| 体系标准 | 有改版时 | VDA/IATF 改版发布后 |
| 客户要求 | 按需 | 接触新客户时补充 |

---

## 7. 自定义域名

如果你有域名（如 `kb.yourcompany.com`），可以绑定：

### 7.1 在 GitHub 设置

1. 进入仓库 Settings → Pages
2. Custom domain 填入你的域名
3. 点击 Save
4. 勾选 Enforce HTTPS

### 7.2 在域名 DNS 设置

添加一条 CNAME 记录：

| 类型 | 主机记录 | 记录值 |
|:----:|---------|--------|
| CNAME | kb（或 @） | `<用户名>.github.io` |

DNS 生效后（最长48小时），就可以用你的域名访问了。

---

## 8. 常见问题

### Q1：部署后访问显示 404？

**A**：首次部署需要 1-5 分钟生效。如果超过 5 分钟仍 404：
- 检查仓库 Settings → Pages 里 Source 是否设为 main 分支
- 检查仓库根目录是否有 `index.html`
- 尝试重新 push 触发部署

### Q2：修改后网站没更新？

**A**：
1. 确认 `git push` 成功
2. 等待 1-2 分钟
3. 用浏览器隐私模式打开（避免缓存）
4. 在网址后加 `?v=2` 强制刷新

### Q3：手机能看吗？

**A**：完全支持。网站是响应式设计，在手机上导航会变成顶部横栏。

### Q4：如何设置为私有仓库？

**A**：创建仓库时选择 Private，但 GitHub Pages 需要付费才能用于私有仓库。建议内容不涉及机密时保持 Public。

### Q5：这个网站会被搜索引擎收录吗？

**A**：公开仓库的 GitHub Pages 可能会被搜索引擎收录。如果不想被收录，在仓库根目录添加 `robots.txt` 文件：
```
User-agent: *
Disallow: /
```

---

## 9. 技能包使用

除了网页版，你还有一个可以**给 AI 用的技能包**：

📦 文件位置：`/workspace/warehouse-automation-expert.zip`

### 技能包用途

| 用途 | 说明 |
|------|------|
| AI 对话使用 | 安装后，AI 在回答仓库问题时自动加载专业知识 |
| 团队分享 | 分发给同事，导入他们的 AI 工具 |
| 离线参考 | 解压后直接阅读 Markdown 文件 |

### 技能包内容

```
warehouse-automation-expert/
├── SKILL.md                       # 主技能 + 路由规则
├── scripts/warehouse_roi.py       # ROI 计算器
└── references/
    ├── automation.md              # 仓储自动化
    ├── wms.md                     # WMS选型
    ├── best-practices.md          # 最佳实践
    ├── industry-cases.md          # 行业案例
    ├── standards.md               # 体系标准
    └── oem-audits.md              # 客户审核
```

---

## 📋 速查卡片

打印或截屏保存这张速查卡：

```
┌──────────────────────────────────────────┐
│          仓储知识库 速查卡片              │
├──────────────────────────────────────────┤
│                                          │
│  🌐 在线地址：                            │
│  <用户名>.github.io/warehouse-knowledge-base/
│                                          │
│  📦 仓库地址：                            │
│  github.com/<用户名>/warehouse-knowledge-base
│                                          │
│  🔄 更新命令：                            │
│  git add . && git commit -m "更新"        │
│  && git push                             │
│                                          │
│  📖 全功能指导书：GUIDE.md               │
│  📦 AI技能包：warehouse-automation-expert.zip│
│                                          │
└──────────────────────────────────────────┘
```
