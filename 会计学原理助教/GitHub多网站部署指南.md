# GitHub Pages 多网站部署指南

本指南介绍如何使用 GitHub 部署多个独立的网站项目。

---

## 方案选择

### 方案一：每个项目一个仓库

适合多个独立的网站项目，互不干扰。

**优点：**

- 各项目独立管理，清晰明了
- 访问地址互不影响
- 便于单独更新和维护

**缺点：**

- 需要创建多个仓库

---

### 方案二：一个仓库放多个网页（推荐！）

适合想把多个网页放在一个仓库统一管理。

**优点：**

- 只需要一个仓库，管理方便
- 一次部署，全部上线
- 适合相关联的多个页面

**访问地址格式：**

| 网页  | 访问地址                                         |
| ----- | ------------------------------------------------ |
| 网页1 | `https://用户名.github.io/仓库名/网页1文件夹/` |
| 网页2 | `https://用户名.github.io/仓库名/网页2文件夹/` |
| 网页3 | `https://用户名.github.io/仓库名/网页3文件夹/` |

---

## 操作步骤

### 第一步：创建 GitHub 仓库

为每个网站项目创建独立的仓库：

1. 登录 [GitHub](https://github.com)
2. 点击右上角 `+` → `New repository`
3. 填写仓库名称（例如：`website-1`）
4. 设为 **Public**（公开仓库才能使用 GitHub Pages）
5. 点击 `Create repository`

**重要：** 为每个网站重复此步骤，创建多个仓库。

---

### 第二步：准备网站文件

每个项目的文件结构示例：

```
website-1/
├── index.html      # 必须有入口文件
├── style.css
├── script.js
└── images/
    └── logo.png
```

**注意：** 入口文件必须命名为 `index.html`

---

### 第三步：上传代码到 GitHub

#### 方法 A：使用网页上传（适合简单项目）

1. 进入你的仓库页面
2. 点击 `uploading an existing file`
3. 拖拽或选择文件上传
4. 填写提交信息（例如："首次提交"）
5. 点击 `Commit changes`

#### 方法 B：使用 Git 命令（推荐）

在项目文件夹打开终端：

```bash
# 初始化 Git 仓库
git init

# 添加所有文件
git add .

# 提交
git commit -m "首次提交"

# 关联远程仓库（替换为你的仓库地址）
git remote add origin https://github.com/你的用户名/website-1.git

# 推送代码
git branch -M main
git push -u origin main
```

---

### 第四步：启用 GitHub Pages

1. 进入仓库页面
2. 点击 `Settings`（设置）
3. 左侧菜单找到 `Pages`
4. 在 `Source` 下选择：
   - **Branch**: `main`（或 `master`）
   - **Folder**: `/ (root)`
5. 点击 `Save`

等待约 1-2 分钟，页面会显示你的网站地址：

```
https://你的用户名.github.io/website-1/
```

---

### 第五步：重复部署其他项目

对每个网站项目，重复第二至第四步。

**最终效果：**

| 项目  | 仓库名    | 网站地址                                |
| ----- | --------- | --------------------------------------- |
| 网站1 | website-1 | `https://用户名.github.io/website-1/` |
| 网站2 | website-2 | `https://用户名.github.io/website-2/` |
| 网站3 | website-3 | `https://用户名.github.io/website-3/` |

---

## 方案二：一个仓库放多个网页

### 第一步：创建一个 GitHub 仓库

只需要创建一个仓库，用来存放所有网页。

1. 登录 [GitHub](https://github.com)
2. 点击右上角 `+` → `New repository`
3. 填写仓库名称（例如：`my-websites`）
4. 设为 **Public**
5. 点击 `Create repository`

---

### 第二步：准备文件结构

在本地创建文件夹，把每个网页放在独立的子文件夹中：

```
my-websites/
├── website-1/          # 第一个网页
│   ├── index.html      # 入口文件
│   ├── style.css
│   └── images/
├── website-2/          # 第二个网页
│   ├── index.html
│   ├── style.css
│   └── images/
└── website-3/          # 第三个网页
    ├── index.html
    └── style.css
```

**关键点：** 每个子文件夹里都要有一个 `index.html` 作为入口文件！

---

### 第三步：上传到 GitHub

```bash
# 进入项目根目录
cd my-websites

# 初始化 Git
git init

# 添加所有文件
git add .

# 提交
git commit -m "首次提交多个网页"

# 关联远程仓库
git remote add origin https://github.com/你的用户名/my-websites.git

# 推送
git branch -M main
git push -u origin main
```

---

### 第四步：启用 GitHub Pages

1. 进入仓库页面
2. 点击 `Settings`
3. 左侧菜单找到 `Pages`
4. 在 `Source` 下选择：
   - **Branch**: `main`
   - **Folder**: `/ (root)`
5. 点击 `Save`

等待 1-2 分钟后，你的网页就可以通过以下地址访问：

| 网页      | 访问地址                                            |
| --------- | --------------------------------------------------- |
| website-1 | `https://用户名.github.io/my-websites/website-1/` |
| website-2 | `https://用户名.github.io/my-websites/website-2/` |
| website-3 | `https://用户名.github.io/my-websites/website-3/` |

**访问方式：** 直接在浏览器输入上面的完整地址即可！

---

### 方案二更新内容

修改任何一个网页后：

```bash
# 进入项目根目录
cd my-websites

# 提交更新
git add .
git commit -m "更新某个网页"
git push
```

所有网页都会同步更新，非常方便！

---

## 更新网站内容

当需要修改网站时：

```bash
# 进入项目目录
cd website-1

# 修改文件后，提交更新
git add .
git commit -m "更新内容"
git push
```

GitHub Pages 会自动重新部署，稍等片刻即可看到更新。

---

## 常见问题

### Q1: 网站显示 404 错误？

**可能原因：**

- 仓库设为 Private（私有），改为 Public
- 入口文件不是 `index.html`
- 刚启用 Pages，等待 1-2 分钟

### Q2: 一定要用 index.html 命名吗？

是的，GitHub Pages 默认识别 `index.html` 作为入口文件。

### Q3: 中文文件名可以吗？

可以，但建议使用英文，避免某些服务器出现编码问题。

### Q4: 每次更新都要重新配置 Pages 吗？

不需要，第一次配置好后，后续只需要 `git push` 推送代码即可自动更新。

### Q5: 这个算"上线"了吗？

是的！部署到 GitHub Pages 后，你的网站就有了公开网址，任何人都可以访问，这就是"上线"了。

### Q6: 方案二访问网址太长怎么办？

GitHub Pages 生成的地址确实较长。如果想要简短域名，可以考虑：

- 使用自定义域名（需要购买域名并配置）
- 或者接受这个免费的长地址

### Q7: 可以在方案二中混合放不同类型的网页吗？

可以！一个仓库里可以放任何类型的网页项目：

- HTML/CSS/JS 网页
- 不同框架的项目
- 静态展示页面

只要每个文件夹有 `index.html` 就可以。

---

## 一键部署脚本（可选）

如果你熟悉命令行，可以创建一个部署脚本 `deploy.bat`（Windows）：

```batch
@echo off
echo 开始部署到 GitHub...
git add .
git commit -m "更新内容"
git push
echo 部署完成！
pause
```

使用时双击运行即可。

---

## 总结

### 方案对比

| 对比项   | 方案一：多仓库  | 方案二：单仓库多文件夹 |
| -------- | --------------- | ---------------------- |
| 仓库数量 | 每个网页一个    | 只需要一个             |
| 访问地址 | `.../仓库名/` | `.../仓库名/文件夹/` |
| 管理难度 | 独立管理，清晰  | 统一管理，方便         |
| 适合场景 | 完全独立的项目  | 相关的多个页面         |

### 快速选择

- **想要独立管理每个网站** → 选方案一
- **想统一管理，一个仓库搞定** → 选方案二（推荐！）

### 核心要点

- ✅ **每个网页都要有** `index.html`
- ✅ **仓库必须设为** Public
- ✅ **更新方式** = `git push`
- ✅ **免费托管** = GitHub Pages

祝你部署顺利！
