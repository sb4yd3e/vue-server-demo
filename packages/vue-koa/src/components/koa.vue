<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
import koa from 'koa'

export default {
  provide () {
    return {
      app: this.app
    }
  },

  data () {
    return {
      app: new koa()
    }
  },

  created () {
    this.app.on('error', err => {
      console.error('Koa error', err)
    })
  }
}
</script>
