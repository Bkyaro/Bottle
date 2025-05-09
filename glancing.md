# Shopline "Bottle" 主题技术架构分析

## 技术栈

-   **模板引擎**：基于 GO 的 Sline
-   **Web 组件**：使用 Custom Elements API（例如 `<theme-cart-drawer>`, `<theme-modal>`）
-   **前端框架**：原生 JavaScript 与自定义的组件系统
-   **CSS**：模块化 CSS 结构，支持主题配色方案
-   **商务功能**：与 Shopline 电商平台的 API 集成

## 架构特点

### 组件化设计

-   使用 Web Components 实现模块化（`defineModule` 函数定义模块）
-   继承关系清晰（例如 `CartItems extends BaseElement`）
-   组件封装业务逻辑（如购物车操作）

### 主题可配置性

-   颜色方案配置（`theme.config.json` 和 `theme.schema.json`）
-   字体定制（支持字体大小、间距、行高配置）

### 目录结构

```text
/components     - 可复用UI组件
/layout         - 页面布局模板
/public         - 静态资源和JS脚本
/sections       - 页面区块
/templates      - 页面模板
/i18n           - 国际化
/blocks         - 可组合块
```

### 事件系统

-   自定义事件系统（`themeEventCenter.dispatch`, `ThemeEvent`）
-   防抖处理（`themeUtils.debounce`）

## 功能特性

### 购物车功能

-   抽屉式购物车（cart-drawer）
-   实时更新商品数量
-   错误处理机制
-   优惠券支持（`shop.cart_discount_enable` 判断）

### 响应式设计

-   模态框设计（`<theme-modal>`）支持移动端/桌面端

### 国际化支持

-   i18n 多语言（`window.Shopline.t` 翻译函数）
-   语言文件目录（`/i18n`）

## 优化特性

-   懒加载图片（带加载背景）
-   加载状态处理

## 主题定制

-   配色方案（`scheme-1` 到 `scheme-4`，颜色可自定义）
-   字体调整
-   边距与间距设置

## 开发特性

-   **构建工具**：模块化 asset 管理（`asset_url()` 函数）
-   **路由管理**：全局 `routes` 对象定义 API 路径
-   **组件生命周期**：自定义元素的注册管理
-   **错误处理**：友好错误提示和视觉反馈

> 这是一个具有现代化架构的电商主题，采用组件化设计以提供灵活的定制能力，通过主题配置文件可以实现外观的深度定制，同时保持与 Shopline 电商平台的紧密集成。
