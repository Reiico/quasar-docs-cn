<template>
  <q-card class="doc-installation q-my-lg" flat bordered>
    <q-tabs v-model="currentTab" align="left" indicator-color="brand-primary" dense :breakpoint="0">
      <q-tab v-for="tab in ['Quasar CLI', 'Vite plugin / Vue CLI', 'UMD']" :key="`installation-${tab}`" :name="tab"
        :label="tab" no-caps></q-tab>
    </q-tabs>
    <q-separator></q-separator>
    <q-tab-panels v-model="currentTab" animated>
      <q-tab-panel class="q-pa-none" name="Quasar CLI">
        <doc-code :code="QuasarCli"></doc-code>
      </q-tab-panel>
      <q-tab-panel class="q-pa-none" name="Vite plugin / Vue CLI">
        <doc-code :code="ExternalCli"></doc-code>
      </q-tab-panel>
      <q-tab-panel class="q-pa-none" name="UMD">
        <doc-code :code="UMD"></doc-code>
      </q-tab-panel>
    </q-tab-panels>
  </q-card>
</template>

<script>
import { ref, computed } from 'vue'
import DocCode from './DocCode.vue'

export default {
  name: 'DocInstallation',

  components: {
    DocCode
  },

  props: {
    components: [ Array, String ],
    directives: [ Array, String ],
    plugins: [ Array, String ],
    config: String
  },

  setup (props) {
    const currentTab = ref('Quasar CLI')

    function nameAsString (name, indent, quotes = true) {
      const wrapper = quotes
        ? str => `'${str}'`
        : str => str

      return Array.isArray(name)
        ? name.map(wrapper).join(',\n' + ''.padStart(indent, ' '))
        : wrapper(name)
    }

    const quasarConf = computed(() => {
      return props.config !== void 0
        ? `${props.config}: { /* look at QuasarConfOptions from the API card */ }`
        : null
    })

    const QuasarCli = computed(() => {
      if (props.plugins === void 0 && quasarConf.value === null) {
        return `/*
 * No installation step is necessary.
 * It gets installed by default by @quasar/app.
 */`
      }

      const parts = []

      if (props.plugins !== void 0) {
        parts.push(`plugins: [
      ${nameAsString(props.plugins, 6)}
    ]`)
      }

      if (quasarConf.value !== null) {
        parts.push(`config: {
      ${quasarConf.value}
    }`)
      }

      return `// quasar.config.js

return {
  framework: {
    ${parts.join(',\n    ')}
  }
}`
    })

    const UMD = computed(() => {
      const config = quasarConf.value !== null
        ? `

// Optional;
// Place the global quasarConfig Object in a script tag BEFORE your Quasar script tag
app.use(Quasar, {
  config: {
    ${quasarConf.value}
  }
}`
        : ''

      const content = `/*
 * No installation step is necessary.
 * It gets installed by default.
 */`

      return content + config
    })

    const ExternalCli = computed(() => {
      const types = [], imports = []

        ;[ 'components', 'directives', 'plugins' ].forEach(type => {
        if (props[ type ] !== void 0) {
          imports.push(nameAsString(props[ type ], 2, false))
          types.push(`${type}: {
    ${nameAsString(props[ type ], 4, false)}
  }`)
        }
      })

      if (quasarConf.value !== null) {
        types.push(`config: {
    ${quasarConf.value}
  }`)
      }

      return `// main.js

import {
  Quasar,
  ${imports.join(',\n  ')}
} from 'quasar'

app.use(Quasar, {
  ${types.join(',\n  ')}
})`
    })

    return {
      currentTab,

      QuasarCli,
      UMD,
      ExternalCli
    }
  }
}
</script>
