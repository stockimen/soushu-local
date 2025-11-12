# 搜书吧: 大図書館 - 小说阅读器

> 基于 [soushu-local](https://github.com/nekonamic/soushu-local) 增强版本

一个纯前端的在线小说阅读和搜索应用，支持本地txt文件的全文搜索和阅读体验优化。在原项目基础上新增了繁简转换、文本乱码处理、章节优化等高级功能。



## 🌟 特性

### 原项目功能

- **全文搜索**: 支持标题和内容的快速搜索，智能匹配排序
- **大文件支持**: 优化的分块加载机制，支持大型 txt 文件阅读
- **API 模式**：向后端请求获取文件

### 🆕 增强功能

- **使用两种模式**：**纯前端模式** 和 **API 模式**

- **繁简转换**: 支持7种转换模式（简繁体、港台繁体等）
- **文本乱码处理**: 自动检测和修复编码乱码问题
- **增加目录功能**: **正则**识别章节标题，点击跳转位置
- **随机推荐**：随机获取 9 / 20 本小说推荐
- **增加缓存/下载功能**：缓存保存在 indexedb，可离线阅读；支持 txt 文件下载
- **支持三种方式添加小说**：本地上传到浏览器缓存；URL 直链下载 txt 文件；自定义 URL 解析（GET 请求），可解析 json 返回数据
- **搜索历史删除**：提供单条与一键删除搜索历史功能
- **缓存管理**：**对缓存内容进行管理**
- **完全离线支持**：离线后，已缓存的小说仍旧能直接阅读

#### 纯前端模式

部署简易，可不使用使用后端服务器与数据库。

将 txt 文件直接放到 public/novels 文件夹里，使用 `npm run generate-record`，进行生成路径索引。

```
# 文件服务器地址（如果为空则使用当前域名）
VITE_FILE_SERVER_BASE=https://example.com
```

可在环境变量设置文件地址，将使用此地址进行 txt 文件获取。

文件获取时链接为：`{文件服务器地址}/{novels里保存的相对地址}`

#### API模式

可搭建或使用别人的后端服务器，这里使用 **[nekonamic](https://github.com/nekonamic)** 提供的后端地址 `https://soushu.inf.li/`，进行搜索与下载。

## 🛠 技术栈

### 原项目技术栈
- **前端框架**: Vue 3 + TypeScript
- **UI组件**: PrimeVue + Tailwind CSS
- **构建工具**: Vite
- **状态管理**: Pinia
- **PWA**: Vite PWA Plugin

## 📁 项目结构

```
frontend/
├── public/
│   └── 轻小说/              # 小说文件存放目录
│       ├── record.json      # 小说索引文件
│       └── [作者]/          # 按作者分类的小说txt文件
├── src/
│   ├── api/
│   │   └── main.ts          # API接口（前端实现）
│   ├── components/
│   │   ├── HomeTopBar.vue   # 首页顶部导航
│   │   └── ViewerTopBar.vue # 阅读器顶部导航
│   ├── data/
│   │   └── novels.ts        # 小说数据管理器
│   ├── store/
│   │   ├── novel.ts         # 小说状态管理
│   │   └── search.ts        # 搜索状态管理
│   ├── utils/
│   │   ├── fileLoader.ts    # 文件加载器
│   │   └── cacheManager.ts  # 缓存管理器
│   └── views/
│       ├── Home.vue         # 首页
│       ├── SearchDoc.vue    # 搜索页面
│       └── Viewer.vue       # 阅读器页面
└── package.json
```

## 🚀 快速开始

### 安装依赖

```shell
cd frontend
pnpm install
```

### 开发模式

```shell
pnpm dev
```

应用将在 http://localhost:5173 启动

### 构建生产版本

```shell
pnpm build
```

构建后的文件将输出到 `frontend/dist/` 目录

### 预览生产版本

```shell
pnpm preview
```

## 📚 小说文件管理

### 添加小说

1. 将txt文件放入 `frontend/public/轻小说/` 目录
2. 按作者创建子目录分类存放
3. 更新 `record.json` 文件添加小说索引

### record.json 格式

```json
[
  [
    "小说标题~~文件大小",
    "作者/文件名.txt"
  ]
]
```

示例：
```json
[
  [
    "关于我转生变成史莱姆这档事01~~420KB",
    "伏濑/关于我转生变成史莱姆这档事01.txt"
  ]
]
```

## 🌐 PWA 支持

应用支持渐进式Web应用（PWA），可以：

- 安装到桌面或主屏幕
- 离线使用已缓存的内容
- 后台更新检查
- 响应式图标和启动画面

## 🔧 配置选项

### 缓存设置

- **内容缓存**: 小于5MB的文件会自动缓存
- **缓存时间**: 默认24小时过期（手动缓存不会过期）
- **存储限制**: 最大50MB缓存空间

### 搜索设置

- **搜索历史**: 保存最近50条搜索记录
- **结果数量**: 每页显示20个结果

## 📝 注意事项

### 原项目注意事项
1. **文件格式**: 目前仅支持UTF-8编码的txt文件
2. **文件大小**: 建议单个文件不超过50MB以保证最佳体验
3. **浏览器兼容**: 需要支持现代ES6+特性的浏览器
4. **存储空间**: 大量缓存可能占用较多本地存储空间

### 🆕 增强功能注意事项
- **繁简转换**: 首次使用转换功能时需要加载转换库（约200-500ms）
- **乱码处理**: 自动处理常见编码问题，保持原文格式
- **性能优化**: 转换器按需加载，不影响首次加载速度
- **兼容性**: 保持与原项目完全兼容，所有原有功能正常工作

## 🤝 贡献

### 对原项目的贡献
欢迎为原项目 [soushu-local](https://github.com/nekonamic/soushu-local) 提交Issue和Pull Request！

## 📄 许可证

本项目基于原项目 [soushu-local](https://github.com/nekonamic/soushu-local) 进行修改增强。

使用 GPL-3.0 license 许可协议。

## 🙏 致谢

### 原项目作者
- **[nekonamic](https://github.com/nekonamic)** - 感谢提供优秀的开源项目基础

### 技术致谢
- [OpenCC](https://github.com/BYVoid/OpenCC) - 高质量的中文转换库
- [Vue.js](https://vuejs.org/) 和相关生态
- 所有开源社区的支持
