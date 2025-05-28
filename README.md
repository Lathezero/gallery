# 部署到Github Page

1. 克隆项目

```
git clone https://github.com/SimonAKing/AnimatedGallery.git
```

2. 安装依赖

```
npm install
```

3. 需要修改package.json中的CDN配置，以便部署到GitHub Pages的子目录。

   ```
   {
     "config": {
       "cdn": "https://cdn.jsdelivr.net/gh/[username]/gallery/photos/"
     }
   }
   ```

4. 构建项目

```
npm run build
```

5. 预览项目

```
npm run preview
```

# 将相册部署到 GitHub Pages 的步骤

## 已完成的工作

1. 安装了项目依赖
2. 修改了 `package.json` 中的 CDN 配置，将其指向新的 GitHub 仓库路径
3. 成功构建了项目，生成了优化后的文件
4. 启动了预览服务器，可以在 http://localhost:3000/ 查看效果

## 部署到 GitHub Pages 的步骤

由于您已经有一个 `username.github.io` 的仓库，我们将采用子目录方案进行部署。以下是详细步骤：

### 1. 创建新的 GitHub 仓库

1. 登录您的 GitHub 账号
2. 点击右上角的 "+" 图标，选择 "New repository"
3. 仓库名称填写 `gallery`（或您喜欢的其他名称）
4. 设置为公开仓库（Public）
5. 点击 "Create repository" 创建仓库

### 2. 将构建后的文件推送到新仓库

在您的本地计算机上，打开命令行终端，执行以下命令：

```bash
# 进入构建后的文件目录
cd dist

# 初始化 Git 仓库
git init

# 添加所有文件到暂存区
git add .

# 提交更改
git commit -m "first deploy"

# 添加远程仓库（请将 [用户名] 替换为您的 GitHub 用户名）
git remote add origin https://github.com/[用户名]/gallery.git

# 推送到远程仓库的 main 分支（强制推送）
git push -f origin main
```

### 3. 启用 GitHub Pages

1. 在 GitHub 上打开您刚创建的仓库
2. 点击 "Settings" 选项卡
3. 在左侧菜单中找到并点击 "Pages"
4. 在 "Source" 部分，选择 "Deploy from a branch"
5. 在 "Branch" 下拉菜单中选择 "main"，然后点击 "Save"
6. 等待几分钟，GitHub 会自动部署您的网站

### 4. 访问您的相册

部署完成后，您可以通过以下地址访问您的相册：

```
https://[用户名].github.io/gallery/
```

### 5. 更新相册内容

如果您想更新相册内容，只需：

1. 在原始项目中更新照片
2. 重新构建项目：`npm run build`
3. 重复上述部署步骤，将新的构建文件推送到 GitHub 仓库

## 注意事项

1. 请确保将 `package.json` 中的 CDN 配置中的 `[用户名]` 替换为您的实际 GitHub 用户名
2. 如果您使用的是 SSH 而不是 HTTPS 连接 GitHub，请相应调整 `git remote add` 命令
3. 如果您想使用自定义域名，可以在 GitHub Pages 设置中配置

​        