<template>
  <div class="navigation">
    <a href="/">Ayodotun A. Ajala</a>
    <div class="hamburger" :class="{ close: showClose }" @click="openMenu">
      <div></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showClose: false
    }
  },
  created() {
    this.$nuxt.$on('toggleMenu', () => {
      this.toggleClose()
    })
  },
  methods: {
    toggleClose() {
      this.showClose = !this.showClose
    },
    openMenu() {
      this.$nuxt.$emit('toggleMenu')
    }
  }
}
</script>
