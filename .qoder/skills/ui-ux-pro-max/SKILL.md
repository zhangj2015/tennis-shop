---
name: ui-ux-pro-max
description: 生成高质量的微信小程序和移动端 UI/UX 设计原型。使用场景包括：用户需要设计小程序页面、移动端应用界面、数据看板、表单页面等。当用户提到"设计"、"原型"、"UI"、"界面"、"页面布局"等关键词时自动调用。
---

# UI/UX Pro Max - 专业界面设计

## 核心能力

本 Skill 用于生成符合微信小程序设计规范的 UI/UX 原型，支持：
- 微信小程序页面设计
- 数据看板/仪表盘设计
- 表单页面设计
- 列表页面设计
- 移动端 H5 页面设计

## 设计风格规范

### 默认配色方案
- **主色调**: 深蓝色 `#1e3a5f`
- **强调色**: 亮蓝色 `#3b82f6`
- **背景色**: 浅灰色 `#f5f5f5`
- **卡片背景**: 白色 `#ffffff`
- **文字主色**: 深灰 `#1f2937`
- **文字次色**: 中灰 `#6b7280`

### 字体规范
- 使用系统默认字体栈
- 标题: 18-20px, font-weight: 600
- 正文: 14-16px, font-weight: 400
- 辅助文字: 12px, font-weight: 400

### 间距规范
- 页面边距: 16px (px-4)
- 卡片内边距: 16px (p-4)
- 模块间距: 16px (space-y-4)
- 元素间距: 8-12px

## 组件库

### 1. 顶部导航栏
```html
<header class="bg-gradient-to-r from-blue-900 to-blue-700 text-white">
  <div class="px-4 py-4">
    <h1 class="text-xl font-bold">页面标题</h1>
  </div>
</header>
```

### 2. 数据卡片（今日数据）
```html
<div class="bg-gradient-to-br from-blue-50 to-blue-100 rounded-xl p-4 border border-blue-200">
  <div class="text-sm text-gray-600">指标名称</div>
  <div class="text-2xl font-bold text-blue-900">数值</div>
  <div class="text-xs text-green-600">趋势信息</div>
</div>
```

### 3. 数据卡片（汇总数据）
```html
<div class="bg-gradient-to-br from-gray-50 to-gray-100 rounded-xl p-4 border border-gray-200">
  <div class="text-sm text-gray-600">指标名称</div>
  <div class="text-2xl font-bold text-gray-800">数值</div>
  <div class="text-xs text-blue-600">辅助信息</div>
</div>
```

### 4. 底部导航栏
```html
<div class="fixed bottom-0 left-0 right-0 bg-white border-t border-gray-200">
  <div class="flex justify-around py-2 pb-safe">
    <div class="flex flex-col items-center">
      <svg class="w-6 h-6 text-blue-600"></svg>
      <span class="text-xs text-blue-600">首页</span>
    </div>
    <!-- 更多导航项 -->
  </div>
</div>
```

### 5. 图表容器
```html
<div class="bg-white rounded-xl p-4 shadow-sm">
  <h2 class="text-lg font-semibold mb-4">图表标题</h2>
  <div class="h-48">
    <canvas id="chartId"></canvas>
  </div>
</div>
```

## 交互规范

### 点击反馈
所有可点击元素必须添加 `:active` 状态：
```css
.tap-feedback:active {
  opacity: 0.7;
  transform: scale(0.98);
}
```

### 刷新按钮
- 位置：右上角悬浮
- 图标：刷新/循环箭头
- 交互：点击后旋转动画

### 维度切换
- 样式：分段控制器 (Segmented Control)
- 位置：图表标题右侧
- 选项：日/周/月

## 输出格式

根据用户需求，输出以下格式之一：

### 1. uni-app 项目代码（Vue3 + uni-app）
- 完整的 `.vue` 单文件组件
- 使用 uni-app 内置组件（view、text、image、scroll-view 等）
- 使用 uni.scss 变量或自定义 CSS
- 使用 uCharts 或 eCharts-for-weixin 实现图表
- 支持微信小程序、H5、App 多端运行

### 2. HTML 原型文件（可预览）
- 完整的 HTML 文件
- 使用 Tailwind CSS
- 包含 Chart.js 图表
- 响应式设计

### 3. 设计规范文档
- 组件标注
- 尺寸规范
- 颜色值
- 交互说明

### 4. 微信小程序 WXML
- 小程序原生组件
- WXSS 样式
- JS 交互逻辑

## uni-app 开发规范

### 技术栈
- **框架**: uni-app (Vue3)
- **UI 组件**: uni-ui 或自定义组件
- **图表库**: uCharts（推荐）或 eCharts-for-weixin
- **样式**: SCSS/CSS + uni.scss 变量

### 组件映射
| HTML 元素 | uni-app 组件 |
|-----------|-------------|
| div | view |
| span/text | text |
| img | image |
| button | button |
| scroll 区域 | scroll-view |
| 列表 | 使用 v-for + view |

### 样式规范
```scss
// 使用 SCSS
.page-container {
  min-height: 100vh;
  background-color: #f5f5f5;
  padding-bottom: constant(safe-area-inset-bottom);
  padding-bottom: env(safe-area-inset-bottom);
}

// 主色调变量
$primary-blue: #1e3a5f;
$accent-blue: #3b82f6;
$light-blue: #e8f4fc;
$gray-bg: #f5f5f5;

// 卡片样式
.card-today {
  background: linear-gradient(135deg, #e8f4fc 0%, #d1e9f7 100%);
  border: 1rpx solid #bfdbfe;
  border-radius: 16rpx;
  padding: 32rpx;
}

.card-month {
  background: linear-gradient(135deg, #f5f5f5 0%, #e8e8e8 100%);
  border: 1rpx solid #d1d5db;
  border-radius: 16rpx;
  padding: 32rpx;
}
```

### 图表实现（uCharts）
```vue
<template>
  <view class="chart-container">
    <qiun-data-charts 
      type="line"
      :opts="opts"
      :chartData="chartData"
      @click="onChartClick"
    />
  </view>
</template>

<script setup>
import { ref } from 'vue';

const opts = ref({
  color: ['#3b82f6', '#10b981'],
  padding: [15, 10, 0, 15],
  legend: { show: true },
  xAxis: { disableGrid: true },
  yAxis: { gridType: 'dash' }
});

const chartData = ref({
  categories: ['1/1', '1/2', '1/3', ...],
  series: [
    { name: '订单量', data: [120, 132, 101, ...] },
    { name: '订场数', data: [30, 35, 28, ...] }
  ]
});
</script>
```

### 页面生命周期
```javascript
// 使用 uni-app 生命周期
onLoad(() => {
  // 页面加载时获取数据
  fetchData();
});

onPullDownRefresh(() => {
  // 下拉刷新
  fetchData().finally(() => {
    uni.stopPullDownRefresh();
  });
});

onReachBottom(() => {
  // 上拉加载更多
  loadMore();
});
```

### 路由跳转
```javascript
// 保留当前页面，跳转到应用内的某个页面
uni.navigateTo({ url: '/pages/order/order' });

// 关闭当前页面，跳转到应用内的某个页面
uni.redirectTo({ url: '/pages/order/order' });

// 跳转到 tabBar 页面
uni.switchTab({ url: '/pages/index/index' });
```

## 设计流程

1. **分析需求**
   - 确定页面类型（首页/列表/表单/详情）
   - 识别核心功能模块
   - 确认数据展示需求

2. **布局规划**
   - 从上至下规划模块顺序
   - 确定网格布局（2列/3列/4列）
   - 规划导航结构

3. **组件选择**
   - 根据模块功能选择对应组件
   - 应用正确的配色方案
   - 添加必要的交互反馈

4. **细节完善**
   - 添加数据更新时间
   - 添加趋势指示（上升/下降）
   - 添加辅助说明文字

5. **输出交付**
   - 生成可运行的 HTML 文件
   - 或生成设计规范文档
   - 确保代码可直接使用

## 注意事项

- 所有数据字段需标注数据来源
- 图表需支持点击查看详情
- 列表需支持下拉刷新和上拉加载
- 按钮需有明确的交互反馈
- 遵循微信小程序设计规范
