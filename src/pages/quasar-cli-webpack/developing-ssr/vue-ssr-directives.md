---
title: Vue SSR 指令
desc: (@quasar/app-webpack) Managing the Vue directives for SSR in a Quasar app.
---

::: warning 警告
此页文档针对于 Quasar v2.6 及其以上的版本。
:::

由于 Vue3 的架构调整，普通的 Vue 指令需要做一些额外的工作后才能在 SSR 模式中正常运行。

SSR 构建服务端时需要所有的 Vue 指令都额外提供一个`getSSRProps()`方法。

::: tip 提示
*  您不需要担心 Quasar 提供的指令，因为它们都为 SSR 模式做了兼容，可以直接运行在 SSR 模式中。
* 然而，当您使用第三方库提供的 Vue 指令并且报错时，需要考虑作者是否考虑了 vue3 的 SSR 的兼容性（是否在指令的定义中添加了 getSSRProps()方法）
:::

## 如何声明一个指令


下面的内容来自[Vue.js 文档](https://vuejs.org/guide/scaling-up/ssr.html#custom-directives)：

> 因为大多数的自定义指令都包含了对 DOM 的直接操作，所以它们会在 SSR 时被忽略。但如果您想要自己控制一个自定义指令在 SSR 时应该如何被渲染 (即应该在渲染的元素上添加哪些 attribute)，您可以使用 getSSRProps 指令钩子：

```js
const myDirective = {
  mounted (el, binding) {
    // 客户端实现：
    // 直接更新 DOM
    el.id = binding.value
  },

  getSSRProps (binding) {
   // 服务端实现：
    // 返回需要渲染的 prop
    // getSSRProps 只接收一个 binding 参数
    return {
      id: binding.value
    }
  }
}
```
