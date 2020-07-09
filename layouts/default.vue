<template>
  <div>
    <Menu />
    <Navigation />
    <nuxt />

    <footer class="footer">
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
      <p>© Ayodotun A. Ajala</p>
    </footer>
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
