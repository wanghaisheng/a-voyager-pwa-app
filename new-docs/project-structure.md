# Voyager PWA 项目结构说明

本文档提供了 Voyager PWA 应用的详细目录结构和关键文件说明，帮助开发者快速了解项目组织方式。

## 顶层目录结构

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
├── new-docs/          # 新生成的项目文档
└── [配置文件]         # 各类配置文件
```

### 配置文件说明

- **package.json**: 项目依赖和脚本配置
- **capacitor.config.ts**: Capacitor 配置文件
- **vite.config.ts**: Vite 构建工具配置
- **tsconfig.json**: TypeScript 配置
- **ionic.config.json**: Ionic 框架配置
- **.github/**: GitHub Actions CI/CD 工作流配置
- **eslint.config.js**: ESLint 代码规范配置
- **.prettierrc**: Prettier 代码格式化配置

## 源代码目录 (src) 结构

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

### 核心目录 (core)

包含应用的基础组件和功能：

- **App.tsx**: 应用的主组件
- **Auth.tsx**: 认证相关的核心逻辑
- **GlobalStyles.tsx**: 全局样式定义
- **TabContext.tsx**: 标签页上下文管理
- **theme/**: 主题相关的样式和配置
  - **AppThemes.ts**: 主题定义
  - **darkVariables.css**: 暗色主题变量
  - **lightVariables.css**: 亮色主题变量
- **listeners/**: 全局事件监听器
  - **AndroidBackButton.tsx**: Android 返回按钮处理
  - **AppUrlListener.tsx**: URL 监听器
  - **HapticsListener.tsx**: 触觉反馈监听器
  - **network/**: 网络状态监听

### 功能模块目录 (features)

按功能模块组织的组件和业务逻辑：

- **auth/**: 认证相关功能
  - **login/**: 登录相关组件
  - **authSlice.ts**: 认证状态管理
  - **siteSlice.ts**: 站点信息状态管理
- **post/**: 帖子相关功能
- **comment/**: 评论相关功能
- **community/**: 社区相关功能
- **feed/**: 信息流相关功能
- **settings/**: 设置相关功能
- **user/**: 用户相关功能
- **inbox/**: 收件箱相关功能
- **media/**: 媒体处理相关功能
- **search/**: 搜索相关功能
- **share/**: 分享相关功能
- **icons/**: 图标组件

### 辅助函数目录 (helpers)

包含各种通用工具函数：

- **date.ts**: 日期处理函数
- **url.ts**: URL 处理函数
- **array.ts**: 数组操作函数
- **object.ts**: 对象操作函数
- **markdown.ts**: Markdown 处理函数
- **lemmy.ts**: Lemmy API 相关辅助函数
- **useAppNavigation.ts**: 导航相关 hook
- **useAppToast.tsx**: Toast 消息 hook
- **useHapticFeedback.ts**: 触觉反馈 hook
- **useSystemDarkMode.ts**: 系统暗色模式 hook

### 路由目录 (routes)

包含应用的路由定义和页面组件：

- **TabbedRoutes.tsx**: 主要路由配置
- **TabBar.tsx**: 底部标签栏组件
- **pages/**: 各个页面组件
- **tabs/**: 标签页组件
- **common/**: 路由间共享的组件

### 服务目录 (services)

包含与后端 API 交互的服务：

- **lemmy.ts**: Lemmy API 服务
- **db.ts**: 本地数据库服务
- **app.ts**: 应用级服务
- **lemmyverse.ts**: Lemmyverse API 服务
- **redgifs.ts**: RedGifs API 服务

## 静态资源目录 (public)

包含应用的静态资源文件：

- **alternateIcons/**: 应用的替代图标
- **badges/**: 应用商店和平台徽章
- **favicons/**: 网站图标
- **splash/**: 启动屏幕图像
- **screenshots/**: 应用截图

## 平台特定代码目录

### Android 目录 (android)

包含 Android 平台特定的代码和配置：

- **app/**: Android 应用代码
  - **src/**: Java/Kotlin 源代码
  - **build.gradle**: Gradle 构建配置

### iOS 目录 (ios)

包含 iOS 平台特定的代码和配置：

- **App/**: iOS 应用代码
  - **App/**: Swift/Objective-C 源代码
  - **VoyagerActionExtension/**: iOS 分享扩展
  - **VoyagerWatch Watch App/**: Apple Watch 应用

## 测试目录 (e2e)

包含端到端测试代码：

- **community-feed.spec.ts**: 社区信息流测试
- **testdata/**: 测试数据
- **ci/**: CI 环境配置

## 自动化部署目录 (fastlane)

包含自动化部署配置：

- **Fastfile**: Fastlane 任务配置
- **Appfile**: 应用标识符配置
- **metadata/**: 应用商店元数据

## 脚本目录 (scripts)

包含构建和部署脚本：

- **prebuild.sh**: 构建前准备脚本
- **prerelease.sh**: 发布前准备脚本
- **release.sh**: 发布脚本
- **disable_in_app_purchases.sh**: 禁用应用内购买脚本

## 资源目录 (resources)

包含原始资源文件：

- **icon-foreground.png**: 图标前景图像
- **icon-only.png**: 仅图标图像
- **splash.png**: 启动屏幕图像

## 文档目录 (manuall-docs)

包含项目文档：

- **Voyager PWA应用新手指南.md**: 新手入门指南
- **代码规范.md**: 代码规范文档
- **团队协作流程.md**: 团队协作流程文档
- **架构文档和开发规范.md**: 架构和开发规范文档
- **测试与发布规范.md**: 测试和发布规范文档
- **项目结构与资源说明.md**: 项目结构说明文档
- **新需求实现文档模板.md**: 新需求实现文档模板