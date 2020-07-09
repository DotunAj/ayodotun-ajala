<template>
  <div class="menu" :class="{ open_menu: menuOpened }">
    <div class="header">
      <span class="header-text">Ayodotun Ajala</span>
      <div class="header-line"></div>
    </div>
    <ul class="body">
      <li>
        <a href="#">Home</a>
      </li>
      <li>
        <a href="#">About</a>
      </li>
      <li>
        <a href="#">Portfolio</a>
      </li>
      <li>
        <a href="#">Contact me</a>
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
      menuOpened: false
    }
  },
  created() {
    this.$nuxt.$on('toggleMenu', () => {
      this.menuOpened = !this.menuOpened
    })
  }
}
</script>
