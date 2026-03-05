# Google Cloud 网站

这是一个准备部署到 Google Cloud 的静态网站项目。

## 项目结构

```
gcp-website/
├── index.html       # 首页
├── privacy.html     # 隐私权政策页面
├── terms.html       # 服务条款页面
└── README.md        # 项目说明文件
```

## 功能特点

- ✅ 包含指向首页的链接
- ✅ 包含指向隐私权政策的链接
- ✅ 包含指向服务条款的链接
- ✅ 响应式设计，支持移动设备
- ✅ 现代化的 UI 设计
- ✅ 符合 Google Cloud 部署要求

## 部署方法

### 方法一：使用 Firebase Hosting（推荐）

1. 安装 Firebase CLI：
```bash
npm install -g firebase-tools
```

2. 登录 Firebase：
```bash
firebase login
```

3. 初始化项目：
```bash
cd gcp-website
firebase init hosting
```

4. 部署：
```bash
firebase deploy
```

### 方法二：使用 Google Cloud Storage

1. 创建存储桶：
```bash
gsutil mb gs://your-bucket-name
```

2. 上传文件：
```bash
gsutil -m rsync -r . gs://your-bucket-name
```

3. 设置为公共访问：
```bash
gsutil iam ch allUsers:objectViewer gs://your-bucket-name
```

4. 配置网站：
```bash
gsutil web set -m index.html -e 404.html gs://your-bucket-name
```

### 方法三：使用 Google App Engine

1. 创建 `app.yaml` 文件（已包含在项目中）

2. 部署：
```bash
gcloud app deploy
```

## 本地预览

你可以直接在浏览器中打开 `index.html` 文件查看效果，或使用本地服务器：

```bash
# 使用 Python 3
python3 -m http.server 8000

# 使用 Node.js http-server
npx http-server

# 然后访问 http://localhost:8000
```

## 自定义修改

- 修改配色：在 HTML 文件的 `<style>` 标签中查找 `#667eea` 和 `#764ba2` 并替换为你喜欢的颜色
- 修改内容：直接编辑对应的 HTML 文件
- 修改联系邮箱：在 privacy.html 和 terms.html 中搜索并替换邮箱地址

## 注意事项

- 部署前请将 `example.com` 替换为你的实际域名
- 根据需要更新隐私权政策和服务条款的内容
- 确保在 Google Cloud Console 中配置正确的权限和设置
