# 论坛应用 (Forum Application)

一个现代化的论坛应用，支持用户注册、发布帖子、评论、分类等功能。

## 功能特性

✨ **用户管理**
- 用户注册和登录
- 用户资料编辑
- 用户头像和简介

📝 **帖子管理**
- 发布、编辑、删除帖子
- 帖子分类和标签
- 浏览次数统计
- 帖子点赞功能

💬 **评论系统**
- 发布和回复评论
- 嵌套评论支持
- 评论点赞功能

🏷️ **分类管理**
- 帖子分类
- 分类管理

🔐 **安全性**
- JWT 认证
- 密码加密
- 权限验证

## 技术栈

- **后端框架**: Express.js
- **数据库**: MongoDB
- **认证**: JWT
- **加密**: bcryptjs
- **验证**: express-validator
- **跨域**: CORS

## 快速开始

### 安装依赖

```bash
npm install
```

### 配置环境变量

```bash
cp .env.example .env
```

编辑 `.env` 文件，配置以下内容：
- `MONGODB_URI`: MongoDB 连接字符串
- `JWT_SECRET`: JWT 密钥
- `PORT`: 服务器端口（默认 5000）

### 启动服务器

**开发模式**
```bash
npm run dev
```

**生产模式**
```bash
npm start
```

## API 文档

### 认证相关

#### 注册
```
POST /api/auth/register
{
  "username": "用户名",
  "email": "邮箱",
  "password": "密码"
}
```

#### 登录
```
POST /api/auth/login
{
  "email": "邮箱",
  "password": "密码"
}
```

### 帖子相关

#### 获取所有帖子
```
GET /api/posts?page=1&limit=10&category=xxx&search=xxx
```

#### 获取帖子详情
```
GET /api/posts/:id
```

#### 创建帖子
```
POST /api/posts
Authorization: Bearer <token>
{
  "title": "标题",
  "content": "内容",
  "category": "分类ID",
  "tags": ["标签1", "标签2"]
}
```

#### 更新帖子
```
PUT /api/posts/:id
Authorization: Bearer <token>
```

#### 删除帖子
```
DELETE /api/posts/:id
Authorization: Bearer <token>
```

### 评论相关

#### 获取评论
```
GET /api/comments/post/:postId
```

#### 发布评论
```
POST /api/comments
Authorization: Bearer <token>
{
  "content": "评论内容",
  "post": "帖子ID",
  "parentComment": "父评论ID (可选)"
}
```

### 分类相关

#### 获取所有分类
```
GET /api/categories
```

#### 获取分类详情
```
GET /api/categories/:slug
```

### 用户相关

#### 获取用户资料
```
GET /api/users/:username
```

#### 更新用户资料
```
PUT /api/users/profile
Authorization: Bearer <token>
{
  "bio": "个人简介",
  "avatar": "头像URL"
}
```

## 项目结构

```
forum/
├── models/              # 数据模型
│   ├── User.js
│   ├── Post.js
│   ├── Comment.js
│   └── Category.js
├── routes/              # API 路由
│   ├── auth.js
│   ├── posts.js
│   ├── comments.js
│   ├── categories.js
│   └── users.js
├── middleware/          # 中间件
│   └── auth.js
├── server.js            # 主服务器文件
├── package.json         # 项目依赖
├── .env.example         # 环境变量示例
└── README.md           # 项目说明
```

## 后续开发建议

- [ ] 添加前端界面（React/Vue）
- [ ] 实现用户头像上传功能
- [ ] 添加帖子搜索功能
- [ ] 实现通知系统
- [ ] 添加用户权限管理系统
- [ ] 实现热贴排行榜
- [ ] 添加数据缓存层（Redis）
- [ ] 完善错误处理和日志记录
- [ ] 编写单元测试和集成测试
- [ ] 部署到云平台（AWS、阿里云等）

## 许可证

MIT
