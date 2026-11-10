# 项目说明

## 项目概况

- 项目名称：禾间餐厅（HÉJIAN）
- 项目类型：面向餐厅顾客的中文单页展示网站，介绍餐厅理念、当季菜品和到店信息。
- 当前实现：Vue 3 单文件组件，由 Vite 提供开发与构建能力；页面文案、菜品数据和大部分样式集中在 `src/App.vue`。
- 页面语言：简体中文（`index.html` 的 `lang` 为 `zh-CN`）。
- 当前页面内容包含顶部公告、品牌导航、主视觉、理念滚动条、当季菜单、餐厅故事、地址与营业信息、页脚。

## 技术栈与常用命令

- 运行时依赖：Vue `^3.5.13`。
- 开发依赖：Vite `^6.0.5`、`@vitejs/plugin-vue` `^5.2.1`。
- 项目采用原生 JavaScript ES Modules（`package.json` 中 `type` 为 `module`）。
- 安装依赖：`npm install`
- 启动开发服务器：`npm run dev`
- 生产构建：`npm run build`
- 本地预览构建产物：`npm run preview`
- 当前未配置 lint、测试或类型检查脚本；不要假设这些命令可用。

## 目录结构

```text
.
├── index.html          # HTML 外壳、页面标题、字体与应用挂载点
├── vite.config.js      # Vite 配置及 Vue 插件
├── package.json        # 依赖与 npm 脚本
└── src/
    ├── main.js         # 创建 Vue 应用并挂载到 #app
    └── App.vue         # 单页内容、菜品数据、交互逻辑及全局/响应式样式
```

## 页面与实现约定

- 应用入口在 `src/main.js`，Vue 根组件为 `src/App.vue`，挂载点是 `index.html` 中的 `#app`。
- 目前没有路由器或后端 API；导航通过 `#home`、`#menu`、`#story`、`#visit` 等页内锚点跳转。
- 菜品信息定义在 `App.vue` 的 `dishes` 数组，并通过 Vue `v-for` 渲染。增删或修改菜品时，保持每项包含 `name`、`price`、`description`、`image`、`alt` 字段。
- 移动端导航由 `menuOpen` 响应式状态控制；点击导航项会关闭菜单。保持菜单按钮的 `aria-expanded` 与状态同步，并为图片提供有意义的替代文本。
- 样式目前集中在 `App.vue` 的 `<style>` 中，使用 CSS 自定义属性统一颜色，并以 `850px`、`620px` 作为响应式断点。没有使用 CSS 框架。
- 字体通过 `index.html` 从 Google Fonts 加载（DM Sans 与 Noto Serif SC）；页面菜品及场景图片使用 Unsplash 外链。外链资源需要网络连接，避免在无需求时改为本地资源或新增图片依赖。
- 餐厅地址、电话、营业时间、价格、季节标签和版权年份都是页面展示数据，变更时注意保持各处信息一致。

## 修改指引

- 文案、菜品、页面区块或布局调整优先在 `src/App.vue` 完成；HTML 元信息、页面标题和字体资源调整在 `index.html` 完成。
- 新增依赖前先确认现有 Vue/Vite 能力无法满足需求，并同步更新锁文件。
- 保持中文界面、当前自然简洁的餐厅品牌风格，以及桌面和窄屏下的可用性。
- 不要把示例餐厅展示内容误认为已接入真实预订、地图、社交媒体或数据服务；目前预约入口是电话链接，地图卡片和社交链接是展示性内容。
- 构建命令为 `npm run build`。只有在任务要求验证或修改需要验证时再运行检查；仓库目前没有独立测试套件。
