---
title: Sass/SCSS 变量
desc: 如何使用 Quasar 预设的 Sass/SCSS 变量。
components:
  - style/SassVariables
---
Quasar 内置了一些 Sass/SCSS 变量，您可以根据需要使用/修改它们。

::: warning
这只适用于使用 Quasar CLI 创建的项目。
:::

## 用法
如果您是使用 Quasar CLI 创建的项目，那么您可以在项目的`*.vue`文件或者 `.sass/.scss` 文件中直接使用 Quasar 内置的 Sass/SCSS 变量，（例如：`$primary`, `$red-1`）。
也可以使用您在`/src/css/quasar.variables.scss`文件中自定义的 Sass/SCSS 变量（或者是`/src/css/quasar.variables.sass`文件）

```html
<!-- 注意 lang="sass" -->
<style lang="sass">
div
  color: $red-1
  background-color: $grey-5
</style>

<!-- 注意 lang="scss" -->
<style lang="scss">
div {
  color: $red-1;
  background-color: $grey-5;
}
</style>
```

::: tip
 `src/css/quasar.variables.sass` 或 `src/css/quasar.variables.scss`文件并不是必须的，只有您想自定义变量或者修改 Quasar 内置的变量时，您才需要创建他们
:::

::: danger
当您创建/删除 `src/css/quasar.variables.sass` 或 `src/css/quasar.variables.scss`文件后，您可能需要重启一次 Quasar，否则将看不到项目的变化。
:::

## 警告

sass/scss 文件中至少得有一个'$'字符才会被 Quasar CLI 自动注入内置的 Sass/SCSS 变量
所以您想在您导入的 sass/scss 文件中使用上述预设的变量，得先保证，这个文件中至少有一个'$'字符，或者，您可以使用一个简单的注释来处理这个问题(`// $`)
```html
<style lang="sass">
// $
//注意上一行的注释

@import 'some-file.sass'
// 由于上面的注释中带有一个$，
// 现在 'some-file.sass'文件中可以访问到上述的 Quasar 预设的 Sass/SCSS 变量了
</style>
```
在`quasar.config.js > css`中定义的 `.sass/.scss` 文件也需要这么做

## 自定义

如果您想修改/添加上述的变量，您需要在您的项目中创建一个`src/css/quasar.variables.sass` (或 `src/css/quasar.variables.scss`)文件，然后在这个文件中修改/新增变量，如果您在创建项目的时候勾选了 Sass 或者 SCSS，这个文件会在项目初始化的时候帮您创建好。**选择 scss 后者 sass 后缀都是可以的，他们的语法不同，取决于您更喜欢哪种，这个文件中的变量会被添加到项目中所有的 `sass/scss/.vue`文件中。**

::: tip
Quasar 的定制化已经非常高了，如果不是必须，我们不推荐您修改这个文件。事实上，若项目中不存在这个变量文件，quasar 将使用默认的变量，反而会加快构建速度。
:::

## Quasar's CSS
Quasar 的 css 是根据这个变量文件编译的（如果存在的话），下面是优先级
* 若 `src/css/quasar.variables.scss` 存在则优先使用它
* 否则，若 `src/css/quasar.variables.sass` 存在，则使用它
* 否者，使用预编译的 Quasar CSS

## 变量列表

<sass-variables />
