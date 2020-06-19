<template>
  <div>
    <Menu />
    <Navigation />
    <nuxt />
  </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import Menu from '@/components/Menu'
export default {
  components: {
    Navigation,
    Menu
  }
}
</script>
