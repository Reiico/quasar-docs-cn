---
title: 屏幕插件
desc: Quasar 提供了屏幕插件来帮助开发者通过 js 开发出动态的响应式的页面
---
Quasar 提供了屏幕插件来帮助开发者通过 Javascript 开发出动态的响应式的页面。出于性能的原因，我们更推荐您使用 CSS 方案[responsive CSS classes](/style/visibility#window-width-related)来实现响应式的 UI。

## 安装
不需要安装，这个插件可以直接使用。

## 用法
注意下面的`$q.screen`，这里只是一个简单的示例

```html
<q-list :dense="$q.screen.lt.md">
  <q-item>
    <q-item-section>John Doe</q-item-section>
  </q-item>

  <q-item>
    <q-item-section>Jane Doe</q-item-section>
  </q-item>
</q-list>
```

```js
// vue 组件的 js 部分
import { useQuasar } from 'quasar'
import { computed } from 'vue'

export default {
  setup () {
    const $q = useQuasar()
    const buttonColor = computed(() => {
      return $q.screen.lt.md
        ? 'primary'
        : 'secondary'
    })

    return { buttonColor }
  }
}
```

我们也可以在 vue 文件之外使用 Screen 组件：

```js
import { Screen } from 'quasar'

// Screen.gt.md
// Screen.md
// Screen.name ('xs', 'sm', ...)
```

## Body classes

如果您开启了 Body classes 这个特性（请查看下面的如何开启部分），您也可以使用 CSS 类名类为不同尺寸的屏幕设置不同的样式：`screen--xs`, `screen--sm`, ..., `screen-xl`.

```css
body.screen--xs {
  .my-div {
    color: #000;
  }
}

body.screen--sm {
  .my-div {
    color: #fff;
  }
}
```

Or a sexy variant in Sass:

```sass
.my-div
  body.screen--xs &
    color: #000
  body.screen--sm &
    color: #fff
```

### 如何开启 body classes

开启它需要像下面这样修改 `/quasar.config.js` 文件，请注意开启后会增加一些第一次渲染时间。

```js
// file: /quasar.config.js

framework: {
  config: {
    screen: {
      bodyClasses: true // <<< add this
    }
  }
}
```

## 配置

下面也有一些方法来控制 Screen 插件的工作方式：

| 方法名 | 描述 | 示例 |
| --- | --- | --- |
| setSizes(Object) | 修改 window 断点，但是不会修改 css 的断点 | setSizes({ lg: 1024, xl: 2000 }) |
| setDebounce(Number) | 修改默认的 100ms 间隔 Change the default 100ms debounce to some other value. | setDebounce(500) // 500ms |

Examples:

```js
// 在 vue 组件之内:
import { useQuasar } from 'quasar'

setup () {
  const $q = useQuasar()

  $q.screen.setSizes({ sm: 300, md: 500, lg: 1000, xl: 2000 })
}

// 在 vue 组件之外:
import { Screen } from 'quasar'
Screen.setSizes({ sm: 300, md: 500, lg: 1000, xl: 2000 })
```

## API
<doc-api file="Screen" />
