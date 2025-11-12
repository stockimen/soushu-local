# 搜书吧: 大図書館 - 小说阅读器

> 基于 [soushu-local](https://github.com/nekonamic/soushu-local) v1.0.3 上修改

支持免数据库使用，直接放置 txt 文件到目录。支持调用 API 进行搜索与获取文件。

一个纯前端的在线小说阅读和搜索应用，支持本地txt文件的全文搜索和阅读体验优化。在原项目 v1.0.3 基础上新增了繁简转换、文本乱码处理、目录列表、下载缓存、缓存管理、文件上传、随机推荐等功能。

<img width="80%"  alt="PixPin_2025-11-12_17-35-20" src="https://github.com/user-attachments/assets/bcc2ae9a-72a3-47b2-bb3e-c226276fa25b" />

<details>
    <summary>手机端预览</summary>
<table style="width: 100%; border-collapse: collapse;">
  <tr>
    <td style="width: 20%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img alt="PixPin_2025-11-12_17-06-46" src="https://github.com/user-attachments/assets/4ff4dcd5-1c77-4014-a39a-fb41ac947af1" />
    </td>
    <td style="width: 20%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img alt="PixPin_2025-11-12_17-08-19" src="https://github.com/user-attachments/assets/2cdbcd84-7824-41b9-ae4c-41373c672f9b" />
    </td>
    <td style="width: 20%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img  alt="PixPin_2025-11-12_17-18-31" src="https://github.com/user-attachments/assets/d4a9a5f1-77d8-472d-b429-a8d5fe53710d" />
    </td>
    <td style="width: 20%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img  alt="PixPin_2025-11-12_17-18-13" src="https://github.com/user-attachments/assets/a3f0ca88-cadb-407b-b564-38ba5546c7f7" />
    </td>
    <td style="width: 20%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img  alt="PixPin_2025-11-12_17-17-10" src="https://github.com/user-attachments/assets/0315bf78-3a84-46dc-9264-7fd431dac43b" />
    </td>
  </tr>
</table>
</details>
    

<details>
    <summary>桌面端预览</summary>
    <table style="width: 100%; border-collapse: collapse;">
  <tr>
    <td style="width: 33%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img  alt="PixPin_2025-11-12_17-26-48" src="https://github.com/user-attachments/assets/464cd901-22ed-48aa-9118-8a1bce9ec39f" />
    </td>
    <td style="width: 33%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img  alt="PixPin_2025-11-12_17-27-26" src="https://github.com/user-attachments/assets/db9fa3aa-042f-4c1b-bfc8-d23f7aa19f82" />
    </td>
    <td style="width: 33%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img  alt="PixPin_2025-11-12_17-33-38" src="https://github.com/user-attachments/assets/b70eeb64-c67a-424a-bba1-65a1e8d30b87" />
    </td>
  </tr>
  <tr>
    <td style="width: 33%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img  alt="PixPin_2025-11-12_17-27-48" src="https://github.com/user-attachments/assets/f746d7c5-e31e-4ac0-aee0-9cc39b0760fb" />
    </td>
    <td style="width: 33%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img  alt="PixPin_2025-11-12_17-29-22" src="https://github.com/user-attachments/assets/9af051dc-c32f-4c5e-9b08-c149039c4576" />
    </td>
    <td style="width: 33%; text-align: center; padding: 10px; border: 1px solid #ddd;">
      <img  alt="PixPin_2025-11-12_17-31-05" src="https://github.com/user-attachments/assets/3d253a33-47f7-4665-839d-b4a958e72d8e" />
    </td>
  </tr>
</table>


</details>



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
soushu-local/
├── README.md                           # 项目说明文档
├── .gitignore                         # Git 忽略文件配置
├── Dockerfile                        # Docker 容器配置文件
├── backend/                           # 后端 Rust 服务目录
│   ├── Cargo.lock                    # Rust 锁定依赖文件
│   ├── Cargo.toml                    # Rust 项目配置文件
│   └── src/                          # Rust 源代码
│       └── main.rs                   # 主程序入口
└── frontend/                         # 前端 Vue 应用目录
    ├── .env                          # 环境变量配置
    ├── .env.example                  # 环境变量示例
    ├── package.json                  # 前端项目配置
    ├── vite.config.ts                # Vite 构建配置
    ├── public/                       # 静态资源目录
    │   ├── img/                      # 公共图片
    │   └── novels/                   # 小说文件存放目录
    │       ├── record.json           # 小说索引文件
    │       └── [作者]/               # 按作者分类的小说txt文件
    ├── scripts/                      # 脚本文件目录
    │   ├── generate-record.js        # 生成记录脚本
    │   └── update-version.js         # 更新版本脚本
    └── src/                          # 源代码目录
        ├── api/                      # API 接口封装
        │   └── main.ts               # 主要 API 接口
        ├── assets/                   # 静态资源
        │   └── main.css              # 主样式文件
        ├── components/               # Vue 组件
        │   ├── AddNovelDialog.vue    # 添加小说对话框
        │   ├── ApiSettingsDialog.vue # API 设置对话框
        │   ├── HomeTopBar.vue        # 首页顶部导航
        │   ├── TocRulesManager.vue   # 目录规则管理器
        │   └── ViewerTopBar.vue      # 阅读器顶部导航
        ├── composables/              # Vue 组合式函数
        │   └── useLayout.ts          # 布局管理函数
        ├── data/                     # 数据文件
        │   └── novels.ts             # 小说数据管理
        ├── router/                   # Vue Router 路由配置
        │   └── index.ts              # 主路由配置
        ├── store/                    # Pinia 状态管理
        │   ├── app.ts                # 应用状态管理
        │   ├── novel.ts              # 小说状态管理
        │   └── search.ts             # 搜索状态管理
        ├── stores/                   # Pinia store 配置
        │   └── auth.ts               # 认证状态管理
        ├── types/                    # TypeScript 类型定义
        │   ├── Fav.ts                # 收藏类型定义
        │   ├── Progress.ts           # 进度类型定义
        │   └── opencc-js.d.ts        # OpenCC 类型声明
        ├── utils/                    # 工具函数
        │   ├── cacheManager.ts       # 缓存管理器
        │   └── chineseConverter.ts   # 中文转换器
        ├── views/                    # Vue 页面组件
        │   ├── CacheManager.vue      # 缓存管理页面
        │   ├── Home.vue              # 首页
        │   ├── SearchDoc.vue         # 搜索页面
        │   └── Viewer.vue            # 阅读器页面
        ├── App.vue                   # 应用根组件
        ├── main.ts                   # 应用入口文件
        └── env.d.ts                  # 环境变量类型定义
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
    "作者/文件名.txt",
    "大小",
    "字数"
  ]
]
```

示例：
```json
[
  [
    "测试/繁体转简体测试.txt",
    "2.25KB",
    "827字"
  ],
  [
    "测试/乱码测试.txt",
    "2.67KB",
    "1044字"
  ],
  [
    "测试/record.txt",
    "146B",
    "112字"
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

## ⚠️ 免责声明

本项目仅作为技术交流和学习研究之用，不提供任何形式的小说资源或内容。

- **内容来源**：用户需自行提供小说文件，本软件仅为阅读工具
- **版权责任**：使用者应遵守相关法律法规，尊重知识产权
- **使用限制**：请勿将本软件用于任何商业用途或非法传播
- **技术目的**：本项目旨在展示前端技术能力，促进技术交流学习

使用本软件所产生的一切后果由使用者自行承担，项目开发者不承担任何责任。
