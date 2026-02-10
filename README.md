# WebNav Hub - 智能网址导航

一个现代化、响应式的网址导航网站，聚合了 AI 搜索、社交媒体、实用工具、科技资讯、云存储和电子邮箱等各类常用网站链接。

## 🌟 功能特点

- **📱 响应式设计** - 完美适配桌面、平板和手机等各种设备
- **🎨 深色主题** - 护眼的暗色系界面，橙色高亮点缀
- **⚡ 快速导航** - 分类清晰的链接卡片，一键直达目标网站
- **🔍 锚点跳转** - 顶部导航栏支持平滑滚动到对应分类
- **🚀 易于部署** - 支持 Cloudflare Workers 无服务器部署
- **📦 零依赖** - 纯 HTML/CSS/JavaScript，无需构建工具

## 📂 文件结构

```
StepFun/
├── index.html          # 主页面文件（可直接在浏览器打开）
├── worker.js           # Cloudflare Workers 部署脚本
└── README.md           # 项目说明文档
```

## 🚀 部署方式

### 方式一：本地使用

直接在浏览器中打开 `index.html` 文件即可使用：

```bash
# 在 Windows 上
start index.html

# 在 macOS 上
open index.html

# 在 Linux 上
xdg-open index.html
```

或者使用本地服务器：

```bash
# 使用 Python 3
python -m http.server 8080

# 使用 Node.js (http-server)
npx http-server -p 8080

# 使用 PHP
php -S localhost:8080
```

然后访问 `http://localhost:8080`

### 方式二：Cloudflare Workers 部署

#### 方法一：使用 Wrangler CLI（推荐）

1. **安装 Wrangler**
   ```bash
   npm install -g wrangler
   ```

2. **登录 Cloudflare 账号**
   ```bash
   wrangler login
   ```

3. **初始化项目**
   ```bash
   wrangler init webnav-hub
   cd webnav-hub
   ```

4. **复制 worker.js 内容**
   将本项目的 `worker.js` 内容复制到 `src/index.js` 中

5. **配置 wrangler.toml**
   ```toml
   name = "webnav-hub"
   main = "src/index.js"
   compatibility_date = "2024-01-01"
   ```

6. **部署**
   ```bash
   wrangler deploy
   ```

#### 方法二：通过 Cloudflare Dashboard 部署

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com)
2. 点击左侧菜单 **Workers & Pages**
3. 点击 **Create application** → **Create Worker**
4. 为 Worker 命名（如 `webnav-hub`）
5. 点击 **Deploy**，然后点击 **Edit code**
6. 将 `worker.js` 的全部内容粘贴到代码编辑器
7. 点击 **Save and deploy**

部署完成后，你会获得一个 `https://webnav-hub.your-subdomain.workers.dev` 的访问地址。

### 方式三：绑定自定义域名

1. 在 Workers 管理页面，点击 **Triggers** 标签
2. 点击 **Add Custom Domain**
3. 输入你的域名（如 `nav.yourdomain.com`）
4. 在 DNS 中添加对应的 CNAME 记录指向 Workers
5. 等待 DNS 生效后即可通过自定义域名访问

## 📋 分类说明

| 分类 | 描述 | 链接数量 |
|------|------|----------|
| **AI 搜索** | 各类 AI 聊天和搜索工具 | 50+ |
| **社交媒体** | 社交平台、视频下载、部署服务 | 15+ |
| **实用工具** | 域名、托管、代理、开发工具等 | 70+ |
| **科技资讯** | 科技新闻和博客网站 | 9 |
| **云存储** | 网盘和文件存储服务 | 7 |
| **电子邮箱** | 各类邮箱服务 | 8 |

## 🛠️ 技术栈

- **HTML5** - 语义化结构
- **CSS3** - Grid 布局、Flexbox、CSS 变量、响应式设计
- **JavaScript** - 原生 JS，无需框架
- **Font Awesome** - 图标库（CDN 引入）
- **Cloudflare Workers** - 边缘计算部署

## 🎨 自定义修改

### 添加新链接

在 `index.html` 或 `worker.js` 中找到对应分类的 `<section class="link-grid">`，添加以下代码：

```html
<div class="link-card">
  <a href="https://your-link.com" target="_blank"></a>
  <i class="fa-solid fa-icon-name"></i>
  <h3>网站名称</h3>
</div>
```

### 修改主题颜色

在 CSS 的 `:root` 中修改变量：

```css
:root {
  --primary-color: #ff9000;    /* 主色调 */
  --bg-color: #0d0d0d;         /* 背景色 */
  --card-bg-color: #1a1a1a;    /* 卡片背景色 */
  --text-color: #fff;          /* 文字颜色 */
}
```

### 添加新分类

1. 在 `<nav><ul>` 中添加导航链接：
   ```html
   <li><a href="#new-category">新分类</a></li>
   ```

2. 在 `<main>` 中添加分类内容：
   ```html
   <h2 class="category-title" id="new-category">新分类</h2>
   <section class="link-grid">
     <!-- 链接卡片 -->
   </section>
   ```

## 🔧 浏览器兼容性

- Chrome 60+
- Firefox 60+
- Safari 12+
- Edge 79+
- 移动端浏览器 iOS Safari / Chrome Android

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 本项目
2. 创建你的功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开一个 Pull Request

## 📜 开源协议

本项目采用 MIT 协议开源 - 详见 [LICENSE](LICENSE) 文件

## 🙏 致谢

- [Font Awesome](https://fontawesome.com/) - 提供精美的图标
- [Cloudflare](https://workers.cloudflare.com/) - 提供边缘计算平台

## 📧 联系方式

如有问题或建议，欢迎通过以下方式联系：

- 提交 [Issue](../../issues)
- 发送邮件至：your-email@example.com

---

<p align="center">Made with ❤️ by WebNav Hub Team</p>
<p align="center">© 2025 WebNav Hub. All rights reserved.</p>
