<template>
  <div class="menu" :class="{ open_menu: menuOpened }">
    <div class="header">
      <span class="header-text">Ayodotun Ajala</span>
      <div class="header-line"></div>
    </div>
    <ul class="body">
      <li>
        <nuxt-link :class="{ active: isHomeActive }" to="/">Home</nuxt-link>
      </li>
      <li>
        <nuxt-link :class="{ active: isAboutActive }" to="/about"
          >About</nuxt-link
        >
      </li>
      <li>
        <nuxt-link to="/">Portfolio</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/">Contact me</nuxt-link>
      </li>
    </ul>
    <div class="menu-footer">
      <div class="footer-line"></div>
      <ul class="footer-links">
        <li>
          <a href="#" class="twitter" target="_blank"></a>
        </li>
        <li>
          <a href="#" class="github" target="_blank"></a>
        </li>
        <li>
          <a href="#" class="linkedin" target="_blank"></a>
        </li>
      </ul>
      <div class="footer-line"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menuOpened: false,
      isHomeActive: false,
      isAboutActive: false
    }
  },
  created() {
    this.$nuxt.$on('toggleMenu', () => {
      this.menuOpened = !this.menuOpened
    })
  }
}
</script>
