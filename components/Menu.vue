<template>
  <div class="menu" :class="{ open_menu: menuOpened }">
    <div class="header">
      <span class="header-text">Ayodotun Ajala</span>
      <div class="header-line"></div>
    </div>
    <ul class="body">
      <li>
        <a :class="{ active: isHomeActive }" @click="removeMenu('/')">Home</a>
      </li>
      <li>
        <a :class="{ active: isAboutActive }" @click="removeMenu('/about')"
          >About</a
        >
      </li>
      <li>
        <a
          :class="{ active: isPortfolioActive }"
          @click="removeMenu('/portfolio')"
          >Portfolio</a
        >
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
      isAboutActive: false,
      isPortfolioActive: false
    }
  },
  created() {
    this.$nuxt.$on('toggleMenu', () => {
      this.menuOpened = !this.menuOpened
      this.setActiveMenu()
    })
  },
  methods: {
    removeMenu(path) {
      this.$router.push(path)
      this.$nuxt.$emit('toggleMenu')
    },
    setActiveMenu() {
      if (this.$route.name === 'index') {
        this.isHomeActive = true
        this.isAboutActive = false
        this.isPortfolioActive = false
      } else if (this.$route.name === 'about') {
        this.isAboutActive = true
        this.isHomeActive = false
        this.isPortfolioActive = false
      } else if (this.$route.name === 'portfolio') {
        this.isAboutActive = false
        this.isHomeActive = false
        this.isPortfolioActive = true
      }
    }
  }
}
</script>
