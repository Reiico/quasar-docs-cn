---
title: 暗色/夜间模式
desc: 处理 Quasar 的暗色/夜间模式。
related:
  - /quasar-plugins/dark
  - /style/theme-builder
---
暗色模式是一种补充模式，该设计减少了设备屏幕发出的光，用于把 UI 变成深色，同时要页面的保持可读性。

暗色模式有一下优点：

* 缓解眼睛疲劳
* 在夜晚或者光线暗的环境下提供更舒服的阅读体验
* 可以减少 OLED 或者 AMOLED 屏幕的耗电量

## 它是如何工作的

1. 它会给页面设置一个默认的黑色背景（这个黑色是可以通过 `body.body--dark` css 选择器来自定义的)。
2. 所有的 Quasar 组件都有一个 `dark` 的属性，当切换为暗色模式时，这个属性会被自动的设置为 `true`。

自动检测的原理是动态监听 `prefers-color-scheme: dark` 媒体查询属性。如果浏览器或者系统切换为了暗色模式，Quasar 应用也会自动切换为暗色模式（在 dark mode 设置为 `auto` 的情况下）


## 如何使用

您可以通过 [Dark Plugin](/quasar-plugins/dark)来轻松的切换 Quasar 应用的暗色/亮色模式。

## 如何改变应用的样式

您可以通过 `body--light` 或 `body--dark` 这两个 css 类名来定制您的 app 在亮色/暗色模式下的表现。

```css
.body--light {
  /* ... */
}

.body--dark {
  /* ... */
}
```
例如，修改模式的暗色模式的背景色：

```css
body.body--dark {
  background: #000
}
```

## 视频讲解
[B 站视频讲解](https://www.bilibili.com/video/BV1pA4y197Zc?p=11)
