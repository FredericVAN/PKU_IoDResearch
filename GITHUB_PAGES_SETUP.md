# GitHub Pages 设置详细指南

本指南将详细说明如何将 IoDResearch 项目网站部署到 GitHub Pages。

## 前置准备

1. 确保你的代码已经推送到 GitHub 仓库
2. 确保仓库是公开的（Public），或者你使用的是 GitHub Pro/Team 账户（支持私有仓库的 Pages）

## 方法一：使用 GitHub Actions 自动部署（推荐）

这是最推荐的方法，因为可以自动部署，并且支持自定义域名等高级功能。

**重要提示：** 你的网站是 **Static HTML**（纯静态 HTML/CSS/JS），不是 Jekyll。我已经创建了 `.nojekyll` 文件来确保 GitHub Pages 正确处理静态文件。

### 步骤 1: 检查工作流文件

确保你的仓库中有 `.github/workflows/deploy.yml` 文件。如果还没有，我已经为你创建好了。

### 步骤 2: 推送代码到 GitHub

```bash
# 如果还没有初始化 git
git init
git add .
git commit -m "Initial commit: Add IoDResearch website"
git branch -M main
git remote add origin https://github.com/你的用户名/仓库名.git
git push -u origin main
```

### 步骤 3: 在 GitHub 上设置 Pages

1. **打开你的 GitHub 仓库页面**
   - 访问 `https://github.com/你的用户名/仓库名`

2. **进入仓库设置**
   - 点击仓库页面顶部的 **"Settings"** 标签

3. **找到 Pages 设置**
   - 在左侧边栏中找到并点击 **"Pages"**（在 "Code and automation" 部分下）

4. **配置部署源**
   - 在 **"Source"** 部分，选择 **"GitHub Actions"**
   - **注意：** 选择 GitHub Actions 而不是 Jekyll，因为你的网站是 Static HTML
   - 如果看到警告，点击 **"Configure"** 按钮

5. **保存设置**
   - 设置会自动保存

### 步骤 4: 触发部署

有两种方式触发部署：

**方式 A: 自动触发（推荐）**
- 当你推送代码到 `main` 或 `master` 分支时，GitHub Actions 会自动运行并部署网站
- 你可以在 **"Actions"** 标签页查看部署进度

**方式 B: 手动触发**
- 进入 **"Actions"** 标签页
- 选择 **"Deploy to GitHub Pages"** 工作流
- 点击 **"Run workflow"** 按钮

### 步骤 5: 查看部署结果

1. **查看部署状态**
   - 进入 **"Actions"** 标签页
   - 点击最新的工作流运行
   - 查看部署是否成功（绿色 ✓ 表示成功）

2. **访问网站**
   - 部署成功后，你的网站地址将是：
     ```
     https://你的用户名.github.io/仓库名/
     ```
   - 例如：`https://username.github.io/PKU_IoDResearch/`

3. **查看网站**
   - 在仓库的 **"Settings > Pages"** 页面，你会看到 "Your site is live at" 的链接
   - 点击链接即可访问

### 常见问题

**Q: 部署失败怎么办？**
- 检查 `.github/workflows/deploy.yml` 文件是否存在且格式正确
- 确保仓库是公开的，或者你有 GitHub Pro/Team 账户
- 查看 Actions 标签页中的错误信息

**Q: 网站显示 404？**
- 等待几分钟，GitHub Pages 需要一些时间来构建
- 检查 `index.html` 文件是否在仓库根目录
- 确保 `.nojekyll` 文件存在

**Q: 如何更新网站？**
- 只需推送新的代码到 `main` 分支
- GitHub Actions 会自动重新部署

---

## 方法二：使用分支部署（传统方法）

如果你不想使用 GitHub Actions，可以使用传统的分支部署方法。

**注意：** 即使使用分支部署，你的网站仍然是 **Static HTML**，不是 Jekyll。`.nojekyll` 文件会确保 GitHub Pages 正确处理静态文件。

### 步骤 1: 确保代码在正确的位置

确保 `index.html`、`style.css`、`script.js` 等文件在仓库的根目录。

### 步骤 2: 在 GitHub 上设置 Pages

1. **打开仓库设置**
   - 访问 `https://github.com/你的用户名/仓库名`
   - 点击 **"Settings"** 标签

2. **进入 Pages 设置**
   - 在左侧边栏点击 **"Pages"**

3. **配置部署源**
   - 在 **"Source"** 下拉菜单中选择 **"Deploy from a branch"**
   - 在 **"Branch"** 下拉菜单中选择你的主分支（通常是 `main` 或 `master`）
   - 在 **"Folder"** 下拉菜单中选择 **"/ (root)"**
   - 点击 **"Save"** 按钮

4. **等待部署**
   - GitHub 会自动构建和部署你的网站
   - 通常需要 1-2 分钟

5. **访问网站**
   - 部署完成后，你的网站地址将是：
     ```
     https://你的用户名.github.io/仓库名/
     ```

---

## 验证部署

### 检查清单

- [ ] 代码已推送到 GitHub
- [ ] 在 Settings > Pages 中配置了部署源
- [ ] 部署状态显示为 "Success" 或 "Published"
- [ ] 可以通过提供的 URL 访问网站
- [ ] 所有图片和资源都能正常加载

### 测试网站

1. **打开网站 URL**
   - 检查页面是否正常加载
   - 检查导航链接是否正常工作
   - 检查图片是否正常显示

2. **检查移动端**
   - 在手机浏览器中打开网站
   - 确保响应式设计正常工作

3. **检查链接**
   - 点击所有外部链接（如论文链接）
   - 确保它们都能正常打开

---

## 自定义域名（可选）

如果你想使用自定义域名（如 `iodresearch.com`）：

1. **在仓库设置中添加自定义域名**
   - 进入 **Settings > Pages**
   - 在 **"Custom domain"** 部分输入你的域名
   - 点击 **"Save"**

2. **配置 DNS**
   - 在你的域名注册商处添加 CNAME 记录
   - 指向 `你的用户名.github.io`

3. **等待 DNS 传播**
   - 通常需要几分钟到几小时

---

## 更新网站内容

每次更新网站内容后：

1. **提交更改**
   ```bash
   git add .
   git commit -m "Update website content"
   git push
   ```

2. **等待自动部署**
   - 如果使用 GitHub Actions，会自动部署
   - 如果使用分支部署，也会自动更新
   - 通常需要 1-2 分钟

3. **清除浏览器缓存**
   - 如果看不到更新，尝试清除浏览器缓存或使用无痕模式

---

## 故障排除

### 问题：网站显示空白页面

**解决方案：**
- 检查浏览器控制台是否有 JavaScript 错误
- 确保所有文件路径都是相对路径
- 检查 `index.html` 中的资源路径是否正确

### 问题：图片不显示

**解决方案：**
- 确保图片文件已推送到 GitHub
- 检查图片路径是否正确（使用相对路径，如 `assets/image.png`）
- 确保图片文件名不包含空格或特殊字符

### 问题：样式不生效

**解决方案：**
- 检查 `style.css` 文件是否在正确位置
- 检查 `index.html` 中的 CSS 链接是否正确
- 清除浏览器缓存

### 问题：GitHub Actions 部署失败

**解决方案：**
- 检查 `.github/workflows/deploy.yml` 文件格式是否正确
- 确保仓库有 Pages 权限
- 查看 Actions 标签页中的详细错误信息

---

## 需要帮助？

如果遇到问题，可以：
1. 查看 GitHub Pages 官方文档：https://docs.github.com/en/pages
2. 检查 GitHub Actions 日志中的错误信息
3. 在 GitHub 仓库中创建 Issue 寻求帮助

---

## 快速参考

### 常用命令

```bash
# 查看当前状态
git status

# 添加所有更改
git add .

# 提交更改
git commit -m "描述你的更改"

# 推送到 GitHub
git push

# 查看部署日志（在 GitHub Actions 中）
# 访问：https://github.com/你的用户名/仓库名/actions
```

### 重要文件

- `index.html` - 主页面
- `style.css` - 样式文件
- `script.js` - JavaScript 文件
- `.nojekyll` - GitHub Pages 配置
- `.github/workflows/deploy.yml` - 自动部署配置

### 网站 URL 格式

```
https://你的用户名.github.io/仓库名/
```

注意：如果仓库名是 `用户名.github.io`，则网站 URL 是：
```
https://你的用户名.github.io/
```

