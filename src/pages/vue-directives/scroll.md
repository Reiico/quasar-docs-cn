---
title: v-scroll 指令
desc: 用户滚动页面时触发的 Vue 指令。
keys: scroll
related:
  - /vue-directives/scroll-fire
  - /vue-components/scroll-observer
---

这是一个 Vue 指令，它接受一个参数(一个函数)，当用户滚动包含该 DOM 节点的页面时触发。

::: tip 提示
* 使用此指令的另一种选择是在页面上放置 QScrollObserver [QScrollObserver](/vue-components/scroll-observer) 组件。
* 还有一个与滚动相关的指令，叫做 [Scroll Fire](/vue-directives/scroll-fire).
:::

## Scroll API

<doc-api file="Scroll" />

## 用法

```vue
<template>
  ...
  <div v-scroll="onScroll">...</div>
  ...
</template>

<script>
export default {
  setup () {
    function onScroll (position) {
      // 当这个方法被调用时，代表用户已经将页面滚动到`position`的位置
      //
      // `position`是一个整数，表示当前滚动的位置，单位像素
    }

    return { onScroll }
  }
}
</script>
```

```js
import { debounce } from 'quasar'

export default {
  setup () {
    function onScroll (position) {
      // 当这个方法被调用时，代表用户已经将页面滚动到`position`的位置
      //
      // `position`是一个整数，表示当前滚动的位置，单位像素
    }

    return {
      onScroll: debounce(onScroll, 200) // 防抖 for 200ms
    }
  }
}
```

### 确定要附加滚动事件的容器
请阅读 [这里](/vue-components/scroll-observer#确定滚动的容器) 了解 Quasar 如何 确定要附加滚动事件的容器。
