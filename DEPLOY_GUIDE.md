# GitHub Pages 部署指南

## 步骤 1：在 GitHub 上创建仓库

1. 打开 GitHub：https://github.com/new
2. **Repository name**（仓库名称）：输入 `my-wiki`（或其他名称）
3. 选择 **Private**（私有）或 **Public**（公开）
4. **不要**勾选 "Add a README file"（因为项目已有一个）
5. 点击 **Create repository**

## 步骤 2：添加远程仓库并推送代码

在您的终端中运行以下命令（将 `YOUR_USERNAME` 替换为您的 GitHub 用户名）：

```bash
cd "D:/workbuddy/MyWiki"

# 添加远程仓库
git remote add origin https://github.com/YOUR_USERNAME/my-wiki.git

# 推送代码到 GitHub
git push -u origin main
```

## 步骤 3：启用 GitHub Pages

1. 在 GitHub 上打开您的仓库
2. 点击 **Settings**（设置）选项卡
3. 在左侧菜单中找到 **Pages**
4. 在 **Source** 部分：
   - 选择 **Source**: **Deploy from a branch**
   - 选择 **Branch**: **gh-pages**（如果下拉菜单中有的话）
   - 或者等待 GitHub Actions 自动部署后，选择 **main** 分支和 **/ (root)** 文件夹
5. 点击 **Save**

## 步骤 4：等待部署完成

1. 打开 **Actions** 选项卡查看部署状态
2. 等待 "Deploy to GitHub Pages" 工作流完成（通常 1-3 分钟）
3. 部署完成后，访问您的网站：
   - 地址格式：`https://YOUR_USERNAME.github.io/my-wiki/`

## 故障排除

### 问题：Actions 中没有看到 "Deploy to GitHub Pages" 工作流

确保您已将 `.github/workflows/deploy.yml` 文件推送到仓库。如果缺少此文件，请重新推送。

### 问题：页面显示 404 错误

GitHub Pages 可能需要几分钟时间来完全激活。请等待 5-10 分钟后再试。

### 问题：CSS/JS 资源加载失败

检查 `quartz.config.ts` 中的 `baseUrl` 设置。对于用户页面（`username.github.io/repo-name/`），应留空。

## 常用命令

```bash
# 推送更新到 GitHub
git add .
git commit -m "更新说明"
git push

# 查看远程仓库地址
git remote -v

# 克隆仓库到新电脑
git clone https://github.com/YOUR_USERNAME/my-wiki.git
```
