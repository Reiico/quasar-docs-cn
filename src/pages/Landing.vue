<template>
  <q-page class="landing">
    <h1 class="landing__title">Quasar Framework 中文网站</h1>
    <section class="landing__hero flex flex-center">
      <div class="row items-center justify-center landing__hero-inner">
        <div class="landing__hero-logo col-12 flex flex-center q-mb-lg">
          <img
            class="landing__logo-image"
            :src="`https://cdn.quasar.dev/logo-v2/svg/logo-vertical${
              $q.dark.isActive ? '-dark' : ''
            }.svg`"
          />
        </div>
        <div class="landing__hero-text col-12 column items-center">
          <div class="q-pb-lg text-grey-6 landing__hero-quote text-center">
            帮助您在短时间内快速构建高性能，高质量的
            <span class="text-bold text-no-wrap">Vue.js 3</span>
            应用程序
          </div>
          <div class="landing__hero-row q-gutter-sm row items-center">
            <q-btn
              color="brand-primary"
              unelevated
              no-caps
              to="/introduction-to-quasar"
              label="为何选择 Quasar ？"
            ></q-btn>
            <q-btn
              color="brand-primary"
              outline
              no-caps
              to="/start"
              label="Get Started"
            ></q-btn>
            <q-btn
              color="accent"
              unelevated
              no-caps
              to="/video-tutorials"
              label="视频教程"
            ></q-btn>
          </div>
          <div class="q-mt-lg text-grey-6 text-center">
            本中文网站持续翻译中,信息来自：
            <a
              target="_blank"
              class="doc-link text-no-wrap"
              href="https://quasar.dev"
            >
              英文官网
            </a>
            。 如果想了解翻译进度，或者参与翻译，请访问
            <a
              target="_blank"
              class="doc-link text-no-wrap"
              href="https://github.com/dongwa/quasar-docs-cn"
            >
              仓库地址
            </a>
            。 另外，我的B站账号中有
            <a
              target="_blank"
              class="doc-link text-no-wrap"
              href="https://www.bilibili.com/video/BV1pA4y197Zc"
            >
              quasar 的视频教程
            </a>
            ，欢迎观看👏
          </div>
          <div class="q-mt-lg text-grey-6 flex text-center content-center">
            目前，网站更新频繁，您每次访问时，可以清除缓存以防遗漏更新。
          </div>
        </div>
      </div>
    </section>
    <section class="text-center row justify-center">
      <div class="landing__features row">
        <div class="col-12 text-center">
          <h4>一套代码支持全平台</h4>
        </div>
        <div class="col-12 text-center q-my-xl">
          <div class="landing__features-icons q-gutter-lg">
            <q-icon :name="fabApple"></q-icon>
            <q-icon :name="fabWindows"></q-icon>
            <q-icon :name="fabLinux"></q-icon>
            <q-icon :name="fabAndroid"></q-icon>
            <q-icon :name="fabChrome"></q-icon>
            <q-icon :name="fabFirefox"></q-icon>
            <q-icon :name="fabEdge"></q-icon>
            <q-icon :name="fabSafari"></q-icon>
          </div>
        </div>
        <div class="col-12 text-center q-my-xl">
          <p>
            使用官网脚手架 @quasar/cli 创建的 quasar
            项目可以一套源代码编译成所有平台的应用程序，并提供最佳实践。您只需关注应用功能本身，忘记跨端带来的烦恼。
          </p>
        </div>
        <div class="col-12 row justify-center">
          <q-card
            :class="['q-px-lg q-py-sm', $q.dark.isActive ? '' : 'bg-grey-1']"
            bordered
            flat
          >
            <q-card-section horizontal>
              <q-card-section class="text-left column items-center q-gutter-sm">
                <q-badge
                  label="$ yarn global add @quasar/cli"
                  color="grey-8"
                ></q-badge>
                <q-badge label="$ yarn create quasar" color="grey-8"></q-badge>
              </q-card-section>
              <q-separator vertical></q-separator>
              <q-card-section class="text-left column items-center q-gutter-sm">
                <q-badge
                  label="$ npm i -g @quasar/cli"
                  color="grey-8"
                ></q-badge>
                <q-badge label="$ npm init quasar" color="grey-8"></q-badge>
              </q-card-section>
            </q-card-section>
          </q-card>
        </div>
      </div>
    </section>
    <section class="text-center">
      <div class="landing__features row items-start q-col-gutter-lg">
        <div class="col-12 text-center">
          <h4>令人印象深刻的用户界面组件</h4>
        </div>
        <div class="col-12 row">
          <div class="col-12 col-md-8 landing__features-section row text-left">
            <div
              class="col-12 text-left text-subtitle1 text-bold q-mt-lg q-mb-md q-mx-xs"
            >
              Vue 组件
            </div>
            <router-link
              class="landing__features-link col-6 col-sm-4"
              v-for="entry in features.comps"
              :key="entry.name"
              :to="entry.path"
            >
              {{ entry.name }}
            </router-link>
          </div>
          <div
            class="col-6 col-sm-4 col-md-2 landing__features-section column text-left"
          >
            <div
              class="text-left text-subtitle1 text-bold q-mt-lg q-mb-md q-mx-xs"
            >
              指令
            </div>
            <router-link
              class="landing__features-link"
              v-for="entry in features.dirs"
              :key="entry.name"
              :to="entry.path"
            >
              {{ entry.name }}
            </router-link>
          </div>
          <div
            class="col-6 col-sm-4 col-md-2 landing__features-section column text-left"
          >
            <div
              class="text-left text-subtitle1 text-bold q-mt-lg q-mb-md q-mx-xs"
            >
              插件
            </div>
            <router-link
              class="landing__features-link"
              v-for="entry in features.plugins"
              :key="entry.name"
              :to="entry.path"
            >
              {{ entry.name }}
            </router-link>
          </div>
        </div>
      </div>
    </section>
    <section class="text-center row justify-center">
      <div class="landing__features row">
        <div class="col-12 q-my-xl row items-center justify-center">
          <q-img
            class="col-12 col-sm-4 landing__icongenie-logo"
            src="https://cdn.quasar.dev/img/iconfactory.png"
          ></q-img>
          <div class="col-12 col-sm-8 column items-center">
            <h4>Quasar Icon Genie</h4>
            <div class="q-mt-lg q-mb-xl">
              只需一个源图标，然后自动克隆、缩放、裁剪生成所需要的100+图标和启动画面，并将其放置在正确的目录下
            </div>
            <q-btn
              color="brand-primary"
              unelevated
              no-caps
              no-wrap
              :icon-right="mdiLaunch"
              label="IconGenie"
              to="/icongenie/introduction"
            ></q-btn>
          </div>
        </div>
      </div>
    </section>
    <section class="landing__footer flex flex-center">
      <div class="text-center">
        <div class="landing__footer-icons row flex-center q-gutter-md">
          <a href="https://github.quasar.dev" target="_blank" rel="noopener">
            <q-icon :name="fabGithub"></q-icon>
          </a>
          <a href="https://blog.quasar.dev" target="_blank" rel="noopener">
            <q-icon :name="mdiPost"></q-icon>
          </a>
          <a href="https://chat.quasar.dev" rel="noopener" target="_blank">
            <q-icon :name="mdiChat"></q-icon>
          </a>
          <a href="https://forum.quasar.dev/" rel="noopener" target="_blank">
            <q-icon :name="mdiForum"></q-icon>
          </a>
          <a href="https://twitter.quasar.dev" target="_blank" rel="noopener">
            <q-icon :name="fabTwitter"></q-icon>
          </a>
          <a href="https://facebook.quasar.dev" target="_blank" rel="noopener">
            <q-icon :name="fabFacebook"></q-icon>
          </a>
          <a href="https://donate.quasar.dev" rel="sponsored" target="_blank">
            <q-icon :name="fasSuitcaseMedical"></q-icon>
          </a>
        </div>
        <div class="q-mt-lg">
          <doc-link
            to="https://github.com/quasarframework/quasar/blob/dev/LICENSE"
          >
            MIT LICENSE
          </doc-link>
          |
          <doc-link to="https://www.iubenda.com/privacy-policy/40685560">
            隐私政策
          </doc-link>
          |
          <doc-link to="https://github.com/quasarframework/quasar-art">
            优秀Quasar作品集
          </doc-link>
        </div>
        <div>
          <doc-link to="http://beian.miit.gov.cn/">
            鄂ICP备2022014971号-1
          </doc-link>
        </div>
      </div>
    </section>
  </q-page>
</template>

<script setup>
import { useMeta } from 'quasar'

import {
  fabGithub,
  fabTwitter,
  fabFacebook,
  fasSuitcaseMedical,
  fabApple,
  fabWindows,
  fabLinux,
  fabAndroid,
  fabChrome,
  fabFirefox,
  fabEdge,
  fabSafari
} from '@quasar/extras/fontawesome-v6'

import { mdiLaunch, mdiPost, mdiChat, mdiForum } from '@quasar/extras/mdi-v6'

import { useDocStore } from 'assets/doc-store.js'
import features from 'assets/features.js'

useMeta({
  title: 'Quasar 框架 V2 中文文档 | Quasar Framework V2 中文文档',
  titleTemplate: ''
})

const $store = useDocStore()
$store.toc = []
</script>

<style lang="sass">
.landing

  &__title
    font-size: 0
    line-height: 0
    opacity: 0
    margin: 0 !important

  > section
    display: flex
    justify-content: center
    padding: 70px 16px 100px

    > div
      position: relative
      max-width: 1040px
      width: 100%

  &__hero
    min-height: 400px

    &-inner
      max-width: 650px !important

    &-text-main
      font-size: 24px

    &-quote
      padding-top: 70px
      font-size: 16px

    .text-h1
      font-size: 5.2rem
      line-height: 5.2rem

  &__logo-image
    width: 280px
    height: 280px

  &__icongenie-logo
    max-width: 220px !important

  &__front

    > div
      max-width: 700px !important

  &__video
    width: 530px
    max-width: 100%

  &__logo
    max-width: 170px
    max-height: 170px

  &__features

    h4, h6
      margin: 26px 0

    h6
      margin-top: 18px

    p
      opacity: .6
      font-size: 16px

    &-icons
      font-size: 64px

    &-link
      color: $grey-9
      text-decoration: none !important
      padding: 2px 3px

      &:hover
        color: $brand-primary

  &__footer
    padding-top: 72px !important
    padding-bottom: 72px !important

  &__footer-icons
    font-size: 28px

    a
      text-decoration: none
      outline: 0
      color: $brand-primary
      transition: color .28s

      &:hover
        color: $teal

@media (max-width: 1092px)
  .landing
    &__hero
      &-quote
        padding-top: 40px
      .text-h1
        font-size: 3.5rem
        line-height: 4.05rem

@media (max-width: 1023px)
  .landing

    &__logo-image
      width: 190px
      height: 190px

    &__hero
      text-align: center

      &-row
        justify-content: center

      &-logo
        padding-right: 0
        justify-content: center

      &-text
        text-align: center

      &-quote
        margin-left: auto
        margin-right: auto

    > section.padding
      padding-top: 90px
      padding-bottom: 90px

    .landing__feature-item
      text-align: center
</style>
