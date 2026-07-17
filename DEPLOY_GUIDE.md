# GitHub 部署操作指南

## 📋 快速部署步骤

### 第一步：在GitHub创建仓库

1. **打开GitHub**: https://github.com/new
2. **填写信息**:
   - Repository name: `wechat-cover-tool`
   - Description: 运营模版工具 - 公众号封面编辑器+AI生图
   - 选择 **Public**
3. **不要勾选** "Add a README file"
4. 点击 **Create repository**

### 第二步：推送代码

打开终端（Terminal），执行：

```bash
cd /Users/fadada/CodeBuddy/20260716103757/github-deploy

# 替换 YOUR_GITHUB_USERNAME 为你的GitHub用户名
git remote add origin https://github.com/YOUR_GITHUB_USERNAME/wechat-cover-tool.git

# 推送到GitHub
git push -u origin main
```

如果提示输入用户名密码，请使用 **GitHub Personal Access Token**:
1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
2. 生成新token，勾选 `repo` 权限
3. 使用token作为密码

### 第三步：启用GitHub Pages

1. 打开仓库页面: `https://github.com/YOUR_USERNAME/wechat-cover-tool`
2. 点击 **Settings** （仓库页面右上角）
3. 左侧菜单选择 **Pages**
4. **Build and deployment** 部分：
   - Source: 选择 **Deploy from a branch**
   - Branch: 选择 `main`，文件夹选 `/ (root)`
5. 点击 **Save**
6. 等待1-3分钟（查看Actions是否运行完成）
7. 访问: `https://YOUR_USERNAME.github.io/wechat-cover-tool/ai.html`

### 第四步：测试使用

1. 打开上面的链接
2. 应该会看到 **API配置窗口**
3. 输入API地址和密钥（参考README.md中的服务商列表）
4. 测试生图功能

---

## 🔧 常见问题

### Q1: 推送时提示认证失败
- 使用Personal Access Token代替密码
- 或安装GitHub CLI: `brew install gh` 然后 `gh auth login`

### Q2: Pages显示404
- 确认Settings → Pages中Branch设置正确
- 等待几分钟让部署生效
- 检查Actions标签页是否有错误

### Q3: API调用失败/CORS错误
- 某些API服务商禁止浏览器直接调用
- 解决方案：
  a. 联系服务商开放CORS
  b. 使用CORS代理服务
  c. 安装浏览器插件临时解决

### Q4: 想更新网站
```bash
cd /Users/fadada/CodeBuddy/20260716103757/github-deploy
git add .
git commit -m "update: 更新内容"
git push
# 自动触发GitHub Pages重新部署
```

---

## ✅ 部署成功标志

- [x] 能访问 `https://USERNAME.github.io/wechat-cover-tool/ai.html`
- [x] 页面弹出API配置窗口
- [x] 输入API信息后能正常保存
- [x] 生图功能正常工作（取决于API服务商）

---

## 🎉 完成！

现在你可以把这个链接发给任何人使用：
```
https://YOUR_USERNAME.github.io/wechat-cover-tool/ai.html
```

无需再发送整个安装包了！🚀
