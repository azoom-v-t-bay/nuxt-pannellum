<template>
  <div id="pannellum" :style="styleRoot"></div>
</template>

<script>
import camelCase from 'lodash/camelCase'
if (process.client) {
  require('pannellum')
  require('pannellum/build/pannellum.css')
}
export default {
  name: 'VPannellum',
  props: {
    height: {
      type: [Number, String],
      default: 500,
    },
    width: {
      type: [Number, String],
      default: 700,
    },
    panorama: {
      type: String,
      default: null,
    },
    cubeMap: {
      type: Array,
      default: null,
    },
    multiRes: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      viewer: null,
    }
  },
  computed: {
    styleRoot() {
      return `height: ${this.height}px; width: ${this.width}px`
    },
    optionsAttrs() {
      const options = {}
      for (const attr in this.$attrs) {
        const property = camelCase(attr)
        if (this.$attrs[attr] === '') {
          options[property] = true
        } else {
          options[property] = this.$attrs[attr]
        }
      }
      return options
    },
    optionsProps() {
      const options = {}
      if (this.panorama) {
        options.type = 'equirectangular'
        options.panorama = this.panorama
      }
      if (this.cubeMap) {
        options.type = 'cubeMap'
        options.cubeMap = this.cubeMap
      }
      if (this.multiRes) {
        options.type = 'multiRes'
        options.multiRes = this.multiRes
      }
      return options
    },
  },
  mounted() {
    this.init()
  },
  beforeDestroy() {
    this.viewer.destroy()
  },
  methods: {
    init() {
      const options = { ...this.optionsAttrs, ...this.optionsProps }
      this.viewer = window.pannellum.viewer('pannellum', options)
      this.viewer.on('load', () => {
        this.$emit('load')
      })
      this.viewer.on('error', (err) => {
        this.$emit('error', err)
      })
    },
  },
}
</script>

<style scoped></style>
