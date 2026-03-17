# Claude 设计系统规范文档

## Design System Specification v1.0

---

## 目录

1. [设计原则](#1-设计原则)
2. [色彩系统](#2-色彩系统)
3. [排版规范](#3-排版规范)
4. [间距系统](#4-间距系统)
5. [布局规范](#5-布局规范)
6. [组件规范](#6-组件规范)
7. [响应式适配](#7-响应式适配)
8. [交互规范](#8-交互规范)
9. [代码实现](#9-代码实现)

---

## 1. 设计原则

### 1.1 设计理念

| 维度 | 描述 |
|------|------|
| **风格** | 简约温暖、现代友好、略带手绘艺术感 |
| **氛围** | 专业但不严肃，技术感与人文感平衡 |
| **体验** | 清晰的信息层级，流畅的交互反馈 |
| **目标** | 降低认知负担，提升阅读舒适度 |

### 1.2 设计关键词

- **温暖 (Warm)**：米色调营造舒适氛围
- **清晰 (Clear)**：信息层级分明，阅读路径明确
- **友好 (Friendly)**：圆角元素，柔和阴影，手绘风格
- **专业 (Professional)**：统一的视觉规范，细节精致

### 1.3 设计原则 checklist

- [ ] 使用足够的留白，避免信息拥挤
- [ ] 通过色彩和大小建立视觉层次
- [ ] 交互元素需要有明确的反馈状态
- [ ] 保持整体风格的一致性
- [ ] 优先考虑移动端阅读体验

---

## 2. 色彩系统

### 2.1 主色板

```css
:root {
  /* 背景色系 */
  --bg-primary: #F5F3EF;      /* 主背景 - 温暖米白 */
  --bg-secondary: #FFFFFF;     /* 卡片背景 - 纯白 */
  --bg-code: #F8F6F2;         /* 代码块背景 - 淡米 */
  
  /* 强调色 */
  --accent: #E86F51;          /* 主强调色 - 珊瑚橙 */
  --accent-light: #F5A623;    /* 次要强调 - 金黄 */
  
  /* 文字色系 */
  --text-primary: #2D2A26;    /* 主文字 - 深炭灰 */
  --text-secondary: #6B6560;  /* 次要文字 - 中灰 */
  --text-muted: #9A9590;      /* 辅助文字 - 浅灰 */
  
  /* 状态色 */
  --success: #52C41A;         /* 成功/完成 - 绿色 */
  --info: #1890FF;            /* 信息/链接 - 蓝色 */
  --warning: #FAAD14;         /* 警告 - 橙色 */
  --error: #FF4D4F;           /* 错误 - 红色 */
  
  /* 深色区域 */
  --footer-bg: #1A1816;       /* 页脚背景 - 深棕黑 */
  --footer-text: #A8A4A0;     /* 页脚文字 - 浅灰 */
  
  /* 边框与阴影 */
  --border-light: rgba(0,0,0,0.06);
  --shadow-soft: 0 1px 3px rgba(0,0,0,0.04);
  --shadow-hover: 0 4px 12px rgba(0,0,0,0.08);
}
```

### 2.2 色彩使用规则

#### 背景色使用

| 场景 | 色值 | 用途 |
|------|------|------|
| 页面背景 | `#F5F3EF` | 全局页面底色 |
| 卡片背景 | `#FFFFFF` | 内容卡片、浮层 |
| 代码块背景 | `#F8F6F2` | 代码示例、引用块 |
| 页脚背景 | `#1A1816` | 底部深色区域 |

#### 强调色使用

| 场景 | 色值 | 用途 |
|------|------|------|
| 主按钮 | `#E86F51` | 主要操作按钮 |
| 图标背景 | `#E86F51` | 渐变起始色 |
| 边框强调 | `#E86F51` | 左侧边框、选中状态 |
| 高亮文字 | `#E86F51` | 链接、标签 |

#### 文字色使用

| 层级 | 色值 | 用途 |
|------|------|------|
| 主标题 | `#2D2A26` | H1-H3标题 |
| 正文 | `#6B6560` | 段落文字 |
| 辅助文字 | `#9A9590` | 时间、标签、说明 |
| 反白文字 | `#FFFFFF` | 深色背景上的文字 |

### 2.3 色彩比例

```
页面色彩分布建议：
├── 背景色：70%（米白）
├── 卡片色：20%（纯白）
├── 强调色：8%（珊瑚橙）
└── 深色区域：2%（页脚）
```

### 2.4 渐变使用

```css
/* 主渐变 - 用于图标、插图 */
--gradient-primary: linear-gradient(135deg, #E86F51 0%, #F5A623 100%);

/* 成功渐变 - 用于进度条 */
--gradient-success: linear-gradient(90deg, #1890FF 0%, #52C41A 100%);

/* 深色渐变 - 用于页脚卡片 */
--gradient-dark: linear-gradient(135deg, #52C41A 0%, #389E0D 100%);
```

---

## 3. 排版规范

### 3.1 字体栈

```css
/* 主字体 */
--font-primary: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'PingFang SC', 'Hiragino Sans GB', 'Microsoft YaHei', sans-serif;

/* 代码字体 */
--font-mono: 'SF Mono', Monaco, 'Courier New', monospace;
```

### 3.2 字体层级

| 层级 | 字号 | 字重 | 行高 | 用途 |
|------|------|------|------|------|
| **Logo** | 20px | 700 (Bold) | 1.2 | 品牌标识 |
| **H1** | 36-40px | 700 (Bold) | 1.3 | 页面主标题 |
| **H2** | 24-28px | 700 (Bold) | 1.3 | 章节标题 |
| **H3** | 18-20px | 600 (Semibold) | 1.4 | 小节标题 |
| **H4** | 16px | 600 (Semibold) | 1.4 | 卡片标题 |
| **正文** | 15-16px | 400 (Regular) | 1.7 | 段落文字 |
| **小字** | 13-14px | 400 (Regular) | 1.6 | 辅助说明 |
| **代码** | 14px | 400 | 1.7 | 代码块 |

### 3.3 移动端字体调整

```css
@media (max-width: 768px) {
  --font-h1: 28px;
  --font-h2: 22px;
  --font-h3: 18px;
  --font-body: 15px;
}
```

### 3.4 文字样式规范

#### 标题样式

```css
.heading {
  color: var(--text-primary);
  font-weight: 700;
  line-height: 1.3;
  margin-bottom: 16px;
}
```

#### 正文样式

```css
.body-text {
  color: var(--text-secondary);
  font-size: 16px;
  line-height: 1.7;
  margin-bottom: 20px;
}
```

#### 辅助文字样式

```css
.caption {
  color: var(--text-muted);
  font-size: 13px;
  line-height: 1.6;
}
```

---

## 4. 间距系统

### 4.1 基础间距单位

以 **4px** 为基础单位，建立间距系统：

| 名称 | 数值 | 用途 |
|------|------|------|
| **xs** | 4px | 图标与文字间距 |
| **sm** | 8px | 紧密元素间距 |
| **md** | 16px | 标准元素间距 |
| **lg** | 24px | 卡片内边距 |
| **xl** | 32px | 区块间距 |
| **2xl** | 48px | 大区块分隔 |
| **3xl** | 64px | 页面章节间距 |

### 4.2 常用间距组合

#### 页面布局

```css
/* 页面边距 */
--page-padding: 24px;
--page-padding-mobile: 16px;

/* 最大内容宽度 */
--content-max-width: 800px;

/* 顶部导航高度 + 内容起始 */
--content-top: 100px;
```

#### 卡片间距

```css
/* 卡片内边距 */
--card-padding: 24px;
--card-padding-lg: 32px;
--card-padding-xl: 40px;

/* 卡片间距 */
--card-gap: 16px;
--card-gap-lg: 20px;
```

#### 组件间距

```css
/* 按钮内边距 */
--btn-padding-sm: 8px 20px;
--btn-padding-md: 12px 28px;
--btn-padding-lg: 16px 40px;

/* 输入框内边距 */
--input-padding: 12px 16px;

/* 标签内边距 */
--tag-padding: 6px 12px;
```

### 4.3 间距使用规则

- **卡片内部**：使用 `--card-padding` (24px)
- **卡片之间**：使用 `--card-gap` (16px)
- **章节分隔**：使用 `--space-xl` (32px) 或 `--space-2xl` (48px)
- **文字间距**：段落之间使用 20px，行高 1.7

---

## 5. 布局规范

### 5.1 页面结构

```
页面布局层级：
├── Navbar (固定顶部)
│   └── Logo + 导航链接 + 操作区
├── Main Content (居中)
│   ├── Breadcrumb (面包屑)
│   ├── Hero Section (头部)
│   ├── Content Section (内容区块)
│   └── ...
└── Footer (底部深色区)
    └── 反馈卡片 + 社交链接 + 版权
```

### 5.2 网格系统

#### 单列布局（默认）

```css
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 0 24px;
}
```

#### 双列布局

```css
.grid-2 {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}
```

#### 响应式网格

```css
.grid-responsive {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
}
```

### 5.3 布局模式

#### 居中卡片布局

```css
.card-center {
  background: var(--bg-secondary);
  border-radius: 20px;
  padding: 40px;
  margin: 32px 0;
  box-shadow: var(--shadow-soft);
  border: 1px solid var(--border-light);
}
```

#### 列表布局

```css
.list-item {
  display: flex;
  gap: 16px;
  padding: 24px;
  background: var(--bg-secondary);
  border-radius: 16px;
  margin-bottom: 16px;
}
```

### 5.4 响应式断点

```css
/* 移动端 */
@media (max-width: 768px) {
  /* 单列布局 */
  /* 减小字号 */
  /* 减小间距 */
}

/* 平板端 */
@media (min-width: 769px) and (max-width: 1024px) {
  /* 双列布局 */
}

/* 桌面端 */
@media (min-width: 1025px) {
  /* 最大宽度限制 */
}
```

---

## 6. 组件规范

### 6.1 按钮 (Button)

#### 主按钮

```css
.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 16px 40px;
  background: var(--text-primary);
  color: white;
  font-size: 16px;
  font-weight: 500;
  border: none;
  border-radius: 28px;  /* 胶囊形 */
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.btn-primary:hover {
  background: var(--accent);
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(232, 111, 81, 0.3);
}

.btn-primary:active {
  transform: scale(0.98);
}
```

#### 次要按钮

```css
.btn-secondary {
  padding: 12px 28px;
  background: var(--bg-primary);
  color: var(--text-secondary);
  border: none;
  border-radius: 24px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.btn-secondary:hover {
  background: var(--text-primary);
  color: white;
}
```

#### 小按钮

```css
.btn-small {
  padding: 8px 20px;
  background: var(--bg-primary);
  color: var(--text-secondary);
  border: none;
  border-radius: 20px;
  font-size: 13px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}
```

### 6.2 卡片 (Card)

#### 基础卡片

```css
.card {
  background: var(--bg-secondary);
  border-radius: 16px;
  padding: 24px;
  box-shadow: var(--shadow-soft);
  border: 1px solid var(--border-light);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-hover);
}
```

#### 大卡片

```css
.card-lg {
  border-radius: 20px;
  padding: 32px;
}
```

#### 带状态边框的卡片

```css
.card-status {
  border-left: 4px solid var(--accent);
}

.card-status.completed {
  border-left-color: var(--success);
}

.card-status.active {
  border-left-color: var(--accent);
}
```

### 6.3 标签 (Tag)

```css
.tag {
  display: inline-block;
  padding: 6px 12px;
  background: var(--bg-primary);
  border-radius: 20px;
  font-size: 13px;
  color: var(--text-secondary);
}

.tag-accent {
  background: rgba(232, 111, 81, 0.1);
  color: var(--accent);
}
```

### 6.4 输入框 (Input)

```css
.input {
  width: 100%;
  padding: 12px 16px;
  background: var(--bg-secondary);
  border: 1px solid var(--border-light);
  border-radius: 12px;
  font-size: 15px;
  color: var(--text-primary);
  transition: all 0.2s;
}

.input:focus {
  outline: none;
  border-color: var(--accent);
  box-shadow: 0 0 0 3px rgba(232, 111, 81, 0.1);
}
```

### 6.5 图标 (Icon)

#### 方形图标

```css
.icon-box {
  width: 40px;
  height: 40px;
  background: linear-gradient(135deg, var(--accent) 0%, var(--accent-light) 100%);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  color: white;
}
```

#### 圆形图标

```css
.icon-circle {
  width: 48px;
  height: 48px;
  background: var(--bg-primary);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
}
```

### 6.6 代码块 (Code Block)

```css
.code-block {
  background: var(--bg-code);
  border-radius: 12px;
  padding: 20px;
  overflow-x: auto;
  border-left: 4px solid var(--accent);
  font-family: var(--font-mono);
  font-size: 14px;
  line-height: 1.7;
  color: var(--text-primary);
}
```

### 6.7 高亮框 (Highlight Box)

```css
.highlight-box {
  background: linear-gradient(135deg, rgba(232, 111, 81, 0.08) 0%, rgba(245, 166, 35, 0.08) 100%);
  border-left: 4px solid var(--accent);
  border-radius: 0 12px 12px 0;
  padding: 24px;
  margin: 28px 0;
}
```

---

## 7. 响应式适配

### 7.1 断点定义

```css
/* 移动端 */
--breakpoint-sm: 640px;

/* 平板端 */
--breakpoint-md: 768px;

/* 桌面端 */
--breakpoint-lg: 1024px;

/* 大屏 */
--breakpoint-xl: 1280px;
```

### 7.2 移动端适配规则

#### 布局调整

```css
@media (max-width: 768px) {
  /* 网格变为单列 */
  .grid-2,
  .grid-3,
  .grid-4 {
    grid-template-columns: 1fr;
  }
  
  /* 减少页面边距 */
  .container {
    padding: 0 16px;
  }
  
  /* 调整卡片内边距 */
  .card {
    padding: 20px;
  }
}
```

#### 字体调整

```css
@media (max-width: 768px) {
  h1 { font-size: 28px; }
  h2 { font-size: 22px; }
  h3 { font-size: 18px; }
  body { font-size: 15px; }
}
```

#### 底部栏调整

```css
@media (max-width: 768px) {
  .footer-bar {
    flex-direction: column;
    gap: 12px;
  }
  
  .footer-bar button {
    width: 100%;
  }
}
```

### 7.3 触摸设备优化

```css
@media (hover: none) {
  /* 触摸设备移除悬停效果 */
  .card:hover {
    transform: none;
  }
  
  /* 增大点击区域 */
  .btn,
  .nav-link {
    min-height: 44px;
  }
}
```

---

## 8. 交互规范

### 8.1 状态定义

#### 按钮状态

| 状态 | 样式 |
|------|------|
| **Default** | 标准样式 |
| **Hover** | 背景变深/变色，上移2px |
| **Active** | scale(0.98)，轻微缩小 |
| **Disabled** | opacity: 0.5，cursor: not-allowed |
| **Loading** | 显示加载动画，禁用点击 |

#### 卡片状态

| 状态 | 样式 |
|------|------|
| **Default** | 标准样式 |
| **Hover** | translateY(-4px)，阴影加深 |
| **Active** | translateY(-2px) |
| **Selected** | 边框颜色变为 accent |

### 8.2 过渡动画

#### 基础过渡

```css
--transition-fast: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
--transition-normal: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
--transition-slow: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
```

#### 常用动画

```css
/* 淡入上浮 */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* 卡片依次出现 */
.card-animate {
  animation: fadeInUp 0.5s ease forwards;
  animation-delay: calc(var(--index) * 0.1s);
}
```

### 8.3 滚动行为

```css
/* 平滑滚动 */
html {
  scroll-behavior: smooth;
}

/* 固定元素 */
.navbar {
  position: fixed;
  top: 0;
  backdrop-filter: blur(10px);
}

/* 底部固定栏 */
.footer-bar {
  position: fixed;
  bottom: 0;
}
```

### 8.4 进度追踪

```javascript
// 滚动进度计算
function updateProgress() {
  const scrollTop = window.scrollY;
  const docHeight = document.documentElement.scrollHeight - window.innerHeight;
  const progress = Math.round((scrollTop / docHeight) * 100);
  
  progressBar.style.width = progress + '%';
  progressText.textContent = progress + '%';
}

window.addEventListener('scroll', updateProgress);
```

---

## 9. 代码实现

### 9.1 CSS 变量完整定义

```css
:root {
  /* Colors */
  --bg-primary: #F5F3EF;
  --bg-secondary: #FFFFFF;
  --bg-code: #F8F6F2;
  --accent: #E86F51;
  --accent-light: #F5A623;
  --text-primary: #2D2A26;
  --text-secondary: #6B6560;
  --text-muted: #9A9590;
  --success: #52C41A;
  --info: #1890FF;
  --footer-bg: #1A1816;
  --footer-text: #A8A4A0;
  
  /* Borders & Shadows */
  --border-light: rgba(0,0,0,0.06);
  --shadow-soft: 0 1px 3px rgba(0,0,0,0.04);
  --shadow-hover: 0 4px 12px rgba(0,0,0,0.08);
  
  /* Typography */
  --font-primary: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'PingFang SC', 'Microsoft YaHei', sans-serif;
  --font-mono: 'SF Mono', Monaco, 'Courier New', monospace;
  
  /* Spacing */
  --space-xs: 4px;
  --space-sm: 8px;
  --space-md: 16px;
  --space-lg: 24px;
  --space-xl: 32px;
  --space-2xl: 48px;
  
  /* Radius */
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-xl: 20px;
  --radius-full: 9999px;
  
  /* Transitions */
  --transition-fast: 0.2s;
  --transition-normal: 0.3s;
  --transition-slow: 0.5s;
  
  /* Layout */
  --content-max-width: 800px;
  --navbar-height: 64px;
}
```

### 9.2 基础重置样式

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: var(--font-primary);
  background: var(--bg-primary);
  color: var(--text-primary);
  line-height: 1.7;
  -webkit-font-smoothing: antialiased;
}

a {
  color: inherit;
  text-decoration: none;
}

button {
  font-family: inherit;
  cursor: pointer;
}

img {
  max-width: 100%;
  height: auto;
}
```

### 9.3 工具类

```css
/* 布局工具类 */
.container {
  max-width: var(--content-max-width);
  margin: 0 auto;
  padding: 0 var(--space-lg);
}

.flex {
  display: flex;
}

.flex-col {
  flex-direction: column;
}

.items-center {
  align-items: center;
}

.justify-between {
  justify-content: space-between;
}

.gap-md {
  gap: var(--space-md);
}

/* 文字工具类 */
.text-center {
  text-align: center;
}

.text-primary {
  color: var(--text-primary);
}

.text-secondary {
  color: var(--text-secondary);
}

.text-muted {
  color: var(--text-muted);
}

/* 间距工具类 */
.mt-lg {
  margin-top: var(--space-lg);
}

.mb-lg {
  margin-bottom: var(--space-lg);
}

.p-lg {
  padding: var(--space-lg);
}

/* 隐藏工具类 */
.hidden {
  display: none;
}

@media (max-width: 768px) {
  .hidden-mobile {
    display: none;
  }
}

@media (min-width: 769px) {
  .hidden-desktop {
    display: none;
  }
}
```

### 9.4 组件模板

#### 页面模板

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title</title>
  <link rel="stylesheet" href="design-system.css">
</head>
<body>
  <!-- 导航栏 -->
  <nav class="navbar">
    <div class="nav-container">
      <a href="/" class="logo">
        <div class="logo-icon">◉</div>
        <span>Brand</span>
      </a>
      <!-- 导航内容 -->
    </div>
  </nav>

  <!-- 主内容 -->
  <main class="main-content">
    <!-- 页面内容 -->
  </main>

  <!-- 页脚 -->
  <footer class="footer">
    <!-- 页脚内容 -->
  </footer>
</body>
</html>
```

---

## 10. 使用示例

### 10.1 课程详情页结构

```html
<!-- Hero Section -->
<header class="lesson-header">
  <div class="lesson-meta-bar">
    <span class="lesson-number-badge">1.1</span>
    <span class="lesson-type">⏱ 15分钟 · 📄 图文课程</span>
  </div>
  <h1>课程标题</h1>
  <p class="lesson-intro">课程简介...</p>
</header>

<!-- Content Section -->
<section class="content-section">
  <h2>
    <span class="section-icon">🌐</span>
    章节标题
  </h2>
  <p>正文内容...</p>
  
  <div class="highlight-box">
    <h4>💡 提示标题</h4>
    <ul>
      <li>要点1</li>
      <li>要点2</li>
    </ul>
  </div>
</section>
```

### 10.2 卡片列表

```html
<div class="card-list">
  <div class="card">
    <div class="card-header">
      <div class="icon-box">📚</div>
      <h3>卡片标题</h3>
    </div>
    <p>卡片描述...</p>
    <div class="card-footer">
      <span class="tag">标签</span>
      <button class="btn-small">操作</button>
    </div>
  </div>
</div>
```

---

## 11. 版本历史

| 版本 | 日期 | 更新内容 |
|------|------|----------|
| v1.0 | 2024-01-15 | 初始版本，包含完整设计规范 |

---

## 12. 附录

### 12.1 设计资源

- 主色值：`#E86F51`（珊瑚橙）
- 背景色：`#F5F3EF`（温暖米白）
- 字体：系统字体栈，无需额外加载

### 12.2 参考链接

- Claude 官方网站设计参考
- 设计原则基于 Material Design 3 和人机界面指南

---

**文档维护**：前端开发团队  
**最后更新**：2024-01-15  
**审核状态**：已审核

---

*本文档是 Claude 设计系统的技术规范，所有前端开发必须遵循本规范进行实现。*