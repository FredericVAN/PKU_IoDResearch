# IoDResearch 项目网站

这是一个基于 HTML/CSS/JavaScript 的静态网站，用于展示 IoDResearch 项目。

## 本地运行

1. 直接在浏览器中打开 `index.html` 文件
2. 或者使用本地服务器：
   ```bash
   # 使用 Python
   python -m http.server 8000
   
   # 使用 Node.js (需要安装 http-server)
   npx http-server
   ```
   然后在浏览器中访问 `http://localhost:8000`

## 部署到 GitHub Pages

### 方法 1: 使用 GitHub Actions (推荐)

1. 确保你的仓库中有 `.github/workflows/deploy.yml` 文件
2. 在 GitHub 仓库设置中：
   - 进入 Settings > Pages
   - 在 Source 中选择 "GitHub Actions"
3. 推送代码到 main 或 master 分支，GitHub Actions 会自动部署

### 方法 2: 手动部署

1. 在 GitHub 仓库设置中：
   - 进入 Settings > Pages
   - 在 Source 中选择 "Deploy from a branch"
   - 选择分支（通常是 main 或 master）
   - 选择 `/ (root)` 文件夹
2. 保存后，GitHub Pages 会自动构建和部署

## 网站结构

```
.
├── index.html          # 主页面
├── style.css           # 样式文件
├── script.js           # JavaScript 交互
├── assets/             # 图片资源
├── .nojekyll           # GitHub Pages 配置
└── .github/
    └── workflows/
        └── deploy.yml  # GitHub Actions 部署配置
```

## 自定义

- 修改 `index.html` 来更改内容
- 修改 `style.css` 来更改样式
- 修改 `script.js` 来更改交互行为
- 在 `assets/` 目录中添加或替换图片

## 注意事项

- 确保所有图片路径使用相对路径（如 `assets/image.png`）
- 图片文件名不要包含空格或特殊字符
- 测试时确保所有链接和图片都能正常显示

