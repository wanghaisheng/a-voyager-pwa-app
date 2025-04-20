# Voyager PWA 应用新手指南

欢迎加入 Voyager PWA 应用项目！本指南旨在帮助你快速理解项目架构、核心功能和开发流程，使你能够尽快融入团队并开始贡献代码。

## 1. 项目概览

### 1.1 项目目的

Voyager PWA 是一个渐进式 Web 应用（Progressive Web App），主要用于提供跨平台的社交媒体浏览和交互体验。该应用支持多平台部署（Web、iOS、Android），并提供离线访问、推送通知等 PWA 特性。

### 1.2 核心业务流程

1. **用户认证**：登录、注册、账户管理
2. **内容浏览**：社区、帖子、评论的浏览和交互
3. **内容创建**：发布帖子、评论
4. **社交互动**：点赞、分享、私信
5. **个性化设置**：主题切换、偏好设置

### 1.3 重要模块与职责

- **认证模块 (auth)**：处理用户登录、注册和会话管理
- **帖子模块 (post)**：帖子的展示、创建、编辑和交互
- **评论模块 (comment)**：评论的展示、创建和交互
- **社区模块 (community)**：社区的浏览、订阅和管理
- **信息流模块 (feed)**：各类内容的聚合展示
- **设置模块 (settings)**：用户偏好和应用配置
- **媒体模块 (media)**：图片、视频等媒体内容的处理

## 2. 文件夹结构解析

### 2.1 顶层目录结构

```
/
├── src/               # 源代码目录
├── public/            # 静态资源文件
├── android/           # Android 平台特定代码
├── ios/               # iOS 平台特定代码
├── fastlane/          # 自动化部署配置
├── e2e/               # 端到端测试
├── scripts/           # 构建和部署脚本
├── resources/         # 原始资源文件
├── manuall-docs/      # 项目文档
└── [配置文件]         # 各类配置文件
```

### 2.2 源代码目录 (src) 结构

```
src/
├── core/             # 核心功能和全局组件
├── features/         # 按功能模块组织的组件和逻辑
├── helpers/          # 通用辅助函数
├── routes/           # 路由定义和页面组件
├── services/         # 服务层，API 调用和数据处理
├── index.tsx         # 应用入口
└── store.tsx         # Redux 存储配置
```

#### 2.2.1 核心目录 (core)

包含应用的基础组件和功能：
- **App.tsx**: 应用的主组件
- **Auth.tsx**: 认证相关的核心逻辑
- **theme/**: 主题相关的样式和配置
- **listeners/**: 全局事件监听器

#### 2.2.2 功能模块目录 (features)

按功能模块组织的组件和业务逻辑：
- **auth/**: 认证相关功能
- **post/**: 帖子相关功能
- **comment/**: 评论相关功能
- **community/**: 社区相关功能
- **feed/**: 信息流相关功能
- **settings/**: 设置相关功能

每个功能模块通常包含：
- 组件文件 (.tsx)
- 样式文件 (.module.css)
- Redux slice 文件 (xxxSlice.ts)
- 自定义 hooks 和工具函数

#### 2.2.3 辅助函数目录 (helpers)

包含各种通用工具函数：
- 日期处理 (date.ts)
- URL 处理 (url.ts)
- 数组/对象操作 (array.ts, object.ts)
- Markdown 处理 (markdown.ts)
- 自定义 hooks (useXxx.ts)

#### 2.2.4 路由目录 (routes)

包含应用的路由定义和页面组件：
- **pages/**: 各个页面组件
- **tabs/**: 标签页组件
- **common/**: 路由间共享的组件

#### 2.2.5 服务目录 (services)

包含与后端 API 交互的服务：
- **lemmy.ts**: Lemmy API 服务
- **db.ts**: 本地数据库服务
- **app.ts**: 应用级服务

### 2.3 静态资源目录 (public)

包含应用的静态资源文件：
- **alternateIcons/**: 应用的替代图标
- **badges/**: 应用商店和平台徽章
- **favicons/**: 网站图标
- **splash/**: 启动屏幕图像
- **screenshots/**: 应用截图

### 2.4 目录结构约定

项目采用了以下约定：
- **特性驱动设计**：按功能模块组织代码，而非按技术类型
- **组件本地化**：组件相关的样式、逻辑和测试放在一起
- **Redux Toolkit**：使用 Redux Toolkit 进行状态管理
- **CSS Modules**：使用 CSS Modules 进行样式隔离

## 3. 本地运行与环境设置

### 3.1 环境要求

- **Node.js**: 16.x 或更高版本
- **npm** 或 **pnpm**: 推荐使用 pnpm
- **Git**: 用于版本控制

### 3.2 安装依赖

```bash
# 使用 pnpm
pnpm install

# 或使用 npm
npm install
```

### 3.3 本地开发

```bash
# 启动开发服务器
pnpm run dev

# 或使用 npm
npm run dev
```

开发服务器将在 http://localhost:3000 启动。

### 3.4 构建应用

```bash
# 构建 Web 版本
pnpm run build

# 构建 Android 版本
pnpm run build:android

# 构建 iOS 版本
pnpm run build:ios
```

### 3.5 推荐的开发工具

- **VS Code**: 推荐的代码编辑器
  - 推荐插件：ESLint, Prettier, TypeScript, React
- **React Developer Tools**: 用于调试 React 组件
- **Redux DevTools**: 用于调试 Redux 状态

## 4. 理解代码实现

### 4.1 核心流程示例：用户登录

要理解用户登录流程，可以从以下文件开始：

1. **src/features/auth/login/**: 登录相关组件
2. **src/features/auth/authSlice.ts**: 认证状态管理
3. **src/services/lemmy.ts**: 与 Lemmy API 的交互

### 4.2 核心流程示例：浏览帖子

要理解帖子浏览流程，可以从以下文件开始：

1. **src/features/feed/Feed.tsx**: 信息流组件
2. **src/features/post/**: 帖子相关组件
3. **src/routes/pages/PostPage.tsx**: 帖子详情页

### 4.3 状态管理

项目使用 Redux Toolkit 进行状态管理：

- **src/store.tsx**: Redux 存储配置
- **src/features/*/xxxSlice.ts**: 各功能模块的状态切片

### 4.4 路由导航

项目使用 Ionic 框架的路由系统：

- **src/routes/TabbedRoutes.tsx**: 主要路由配置
- **src/helpers/useAppNavigation.ts**: 导航辅助 hook

## 5. 开发新功能指导

### 5.1 添加新页面

要添加一个新页面，需要：

1. 在 **src/routes/pages/** 创建新的页面组件
2. 在 **src/routes/TabbedRoutes.tsx** 添加路由配置

### 5.2 添加新组件

要添加一个新组件，需要：

1. 确定组件属于哪个功能模块
2. 在对应的功能模块目录下创建组件文件和样式文件
3. 如果需要状态管理，考虑更新或创建 Redux slice

### 5.3 添加新 API 服务

要添加一个新的 API 服务，需要：

1. 在 **src/services/** 添加新的服务文件或更新现有服务
2. 创建相应的类型定义和接口

### 5.4 遵循的设计模式和最佳实践

- **组件设计**：遵循功能单一原则，组件应该只做一件事
- **状态管理**：使用 Redux Toolkit 进行全局状态管理，使用 React hooks 进行局部状态管理
- **样式管理**：使用 CSS Modules 进行样式隔离
- **异步操作**：使用 Redux Toolkit 的 createAsyncThunk 处理异步操作

## 6. 协作规范与最佳实践

### 6.1 代码风格

- **命名规范**：
  - 组件使用 PascalCase (如 PostCard)
  - 函数和变量使用 camelCase (如 fetchData)
  - 常量使用 UPPER_SNAKE_CASE (如 MAX_RETRY_COUNT)
  - CSS 类名使用 kebab-case (如 post-card)

- **注释要求**：
  - 复杂逻辑需要添加注释
  - 公共 API 和函数需要添加 JSDoc 注释

- **代码格式化**：
  - 使用 Prettier 进行代码格式化
  - 使用 ESLint 进行代码质量检查

### 6.2 版本控制流程

- **分支命名**：
  - 功能分支：`feature/feature-name`
  - 修复分支：`fix/bug-name`
  - 发布分支：`release/version`

- **提交信息格式**：
  - 使用语义化提交信息
  - 格式：`type(scope): message`
  - 类型：feat, fix, docs, style, refactor, test, chore

### 6.3 测试规范

- **单元测试**：
  - 使用 Jest 和 React Testing Library
  - 测试文件命名：`*.test.ts(x)`

- **端到端测试**：
  - 使用 Playwright
  - 测试文件位于 `e2e/` 目录

### 6.4 代码审查流程

- **提交前检查**：
  - 确保代码通过 ESLint 和 Prettier 检查
  - 确保测试通过

- **代码审查要点**：
  - 代码质量和可读性
  - 功能完整性和正确性
  - 性能和安全性考虑
  - 文档和注释的完整性

## 7. 调试与问题排查

### 7.1 常见问题与解决方案

- **构建失败**：
  - 检查依赖版本
  - 清除缓存：`pnpm clean`

- **运行时错误**：
  - 检查浏览器控制台错误信息
  - 使用 React Developer Tools 和 Redux DevTools 调试

### 7.2 提问技巧

提问时，请提供以下信息：

- 问题的详细描述
- 复现步骤
- 错误信息和堆栈跟踪
- 相关代码片段
- 已尝试的解决方案

### 7.3 日志和监控

- 开发环境中使用浏览器控制台查看日志
- 生产环境中使用应用内置的错误报告功能

## 8. 常用资源和参考

### 8.1 项目相关文档

- **项目结构与资源说明**：`manuall-docs/项目结构与资源说明.md`
- **架构文档和开发规范**：`manuall-docs/架构文档和开发规范.md`
- **代码规范**：`manuall-docs/代码规范.md`
- **团队协作流程**：`manuall-docs/团队协作流程.md`
- **测试与发布规范**：`manuall-docs/测试与发布规范.md`

### 8.2 技术栈文档

- [React 官方文档](https://reactjs.org/docs/getting-started.html)
- [Redux Toolkit 文档](https://redux-toolkit.js.org/introduction/getting-started)
- [Ionic Framework 文档](https://ionicframework.com/docs)
- [TypeScript 文档](https://www.typescriptlang.org/docs/)
- [PWA 文档](https://web.dev/progressive-web-apps/)

### 8.3 工具和库

- [Capacitor](https://capacitorjs.com/docs) - 用于构建跨平台应用
- [Fastlane](https://docs.fastlane.tools/) - 用于自动化部署
- [Playwright](https://playwright.dev/docs/intro) - 用于端到端测试

## 9. 结语

恭喜你完成了 Voyager PWA 应用的新手指南！现在你应该对项目有了基本的了解，并且知道如何开始贡献代码。如果你有任何问题，请随时向团队成员寻求帮助。

祝你在 Voyager PWA 项目中取得成功！