---
title: Material Ripples
desc: 帮您轻松实现 material design 中的涟漪动画的 Vue 指令。
keys: material-ripple
---

Quasar 提供了`v-ripple`指令，您可以使用它轻松的为 DOM/组件添加一个 Material design 中的涟漪动画（点击元素后有一个水波效果）

::: danger
不要在已经有涟漪效果的组件中使用此指令，（例如： `QBtn`），他们都有一个`ripple`属性来控制涟漪效果。
:::

## Ripple API

<doc-api file="Ripple" />

## 用法

::: warning
使用前，请确保目标 DOM/组件设置了`position: relative` CSS，或者直接使用 `relative-position` Quasar CSS 辅助类。
:::

### 基础

<doc-example title="常规" file="Ripple/Basic" />

### 着色

Material Ripple 默认采用文本的 CSS 颜色，但这是可配置的：

<doc-example title="着色" file="Ripple/Colored" />

### 定位

您也可以配置涟漪效果从何处展开，默认从点击处展开，您可以配置始终从 DOM 中心展开：

<doc-example title="定位" file="Ripple/Positioning" />

### 提前触发

默认情况下，Ripple 指令在点击或按键时被触发。但是，您可以更改它并使其在第一次用户交互(mousedown, touchstart, keydown)时更早的触发。请注意，在大多数情况下，事件集可能会重叠(第一次和最后一次用户交互之间的小延迟)，用户的感知没有差异，但在某些情况下，这可能会导致误导用户。

这在触摸屏上尤其明显，如果用户在触控启动后不小心移动了手指，它有时会被解释为一个非常小的滚动事件，而不是点击事件，所以点击事件没有被触发，但仍然有一个波纹。

<doc-example title="Triggering immediately" file="Ripple/Early" />

### 禁用

如果出于某些原因，您有一个场景需要禁用波纹，那么您可以为指令分配一个布尔值，来开启/禁用它

<doc-example title="禁用" file="Ripple/Disable" />

### 视频讲解
若仍有疑惑，请观看[视频讲解](https://www.bilibili.com/video/BV1j94y1U7qo)
