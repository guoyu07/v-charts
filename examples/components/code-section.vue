<template>
  <pre :class="langClass"><code :class="langClass" v-html='innerCode'></code></pre>
</template>

<script>
import Prism from 'prismjs'
import 'prismjs/themes/prism.css'
console.log(Prism.languages)

export default {
  name: 'CodeSection',

  props: {
    content: [String, Object],
    lang: { type: String, default: 'javascript' },
    json: { type: Boolean, default: false }
  },

  computed: {
    innerCode () {
      const content = this.json ? JSON.stringify(this.content, null, 2) : this.content
      return Prism.highlight(content, Prism.languages[this.lang])
    },

    langClass () {
      return { [`language-${this.lang}`]: true }
    }
  }
}
</script>

<style>
pre[class*="language-"] {
  padding: 5px !important;
  font-size: 12px;
}
</style>
