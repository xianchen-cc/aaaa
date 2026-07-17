# 运营模版工具 - GitHub Pages 部署版

> 无需本地服务器，直接通过浏览器访问即可使用！

## ✨ 功能特性

- 🎨 **封面编辑器** - 可视化编辑公众号封面
- 🤖 **AI生图** - 接入第三方API自动生成配图
- 🔑 **自定义API** - 用户自行输入API地址和密钥
- 💾 **本地存储** - 配置保存在浏览器localStorage中
- 📱 **响应式设计** - 支持桌面端使用

## 🚀 使用方式

### 方式一：在线访问（推荐）

1. 访问部署后的GitHub Pages链接
2. 首次使用会弹出 **API配置窗口**
3. 输入以下信息：
   - **API地址**: 如 `https://api.ikeap.cloud.tencent.com/v1`
   - **API密钥**: 您的服务商密钥
   - **模型名称**: 如 `gpt-image-2`（默认）
4. 点击"保存并开始使用"
5. 开始使用AI生图功能！

### 方式二：本地运行

```bash
# 进入目录
cd github-deploy

# 启动本地服务器（Python）
python3 -m http.server 8080

# 浏览器打开 http://localhost:8080/ai.html
```

## 🔧 API 配置说明

本工具支持所有兼容 **OpenAI Images API** 格式的服务商：

### 支持的服务商示例

| 服务商 | API地址 | 模型名 |
|--------|---------|--------|
| 腾讯云 (混元) | `https://api.ikeap.cloud.tencent.com/v1` | 自定义 |
| OpenAI兼容接口 | `https://your-api-endpoint/v1` | `gpt-image-2` / `dall-e-3` |
| 其他兼容服务 | 参照服务商文档 | - |

### 注意事项

⚠️ **关于CORS跨域问题**

由于是纯前端部署，直接调用API可能遇到跨域限制。解决方案：

1. **使用支持CORS的API服务商**（推荐）
2. **使用浏览器插件**（如 CORS Unblock）临时解决开发调试
3. **使用代理服务器**（需要后端支持）

## 📁 文件结构

```
github-deploy/
├── ai.html          # AI生图工作台（已改造为纯前端）
├── tool.html        # 封面编辑器（原版保留）
├── assets/          # 图片资源文件
│   ├── sample-light-*.png  # 示例素材
│   └── ...
└── README.md        # 本文档
```

## 🌐 部署到GitHub Pages

### 步骤一：创建GitHub仓库

1. 登录 [GitHub](https://github.com)
2. 点击右上角 "+" → "New repository"
3. 仓库名：`wechat-cover-tool`（或其他名称）
4. 选择 **Public** 或 **Private**
5. **不要**勾选 README、.gitignore 等选项
6. 点击 "Create repository"

### 步骤二：上传代码

在本地终端执行：

```bash
cd github-deploy

# 初始化Git（如果还没有初始化）
git init
git branch -m main
git add .
git commit -m "feat: 初始化运营模版工具"

# 添加远程仓库（替换 YOUR_USERNAME）
git remote add origin https://github.com/YOUR_USERNAME/wechat-cover-tool.git
git push -u origin main
```

### 步骤三：启用GitHub Pages

1. 打开仓库页面
2. 点击 **Settings** 标签
3. 左侧菜单选择 **Pages**
4. Source 选择 **Deploy from a branch**
5. Branch 选择 `main`，文件夹选 `/ (root)`
6. 点击 **Save**
7. 等待几分钟后，访问 `https://YOUR_USERNAME.github.io/wechat-cover-tool/ai.html`

## 🛠️ 技术架构

### 改造前后对比

| 项目 | 原版 | 改造版 |
|------|------|--------|
| 后端依赖 | Go服务器 (server.go) | ❌ 无需后端 |
| API密钥 | 硬编码在代码中 | 用户输入+本地存储 |
| 启动方式 | 双击exe/bat脚本 | 浏览器直接访问 |
| 部署方式 | 发送安装包 | GitHub Pages链接 |

### 主要改动

1. **ai.html 改造**
   - 新增 API 设置弹窗组件
   - 移除对 `/api/gpt-image` 等本地接口的调用
   - 改为前端直接调用第三方API
   - API配置存储在 localStorage

2. **tool.html 保留原版**
   - 封面编辑功能完全保留
   - 与 ai.html 通过 localStorage 联动

## ⚠️ 已知限制

1. **CORS跨域**: 部分API服务商不允许浏览器直接调用，可能需要：
   - 使用支持CORS的服务商
   - 搭建简易代理
   - 使用浏览器扩展
   
2. **绿幕抠图**: 由于移除了后端，改为浏览器端Canvas处理，性能略低但可用

3. **大图片处理**: 前端处理大尺寸base64图片时内存占用较高

## 📝 更新日志

### v1.0.0 (2026-07-17)
- ✅ 实现纯前端部署版本
- ✅ API密钥用户自主输入
- ✅ 兼容OpenAI Images API格式
- ✅ 保留完整编辑和生图功能

---

**提示**: 如果遇到任何问题，请检查浏览器控制台的错误信息（F12 → Console）。
