<template>
  <footer class="footer">
    <p>&copy; 2025 Fontenehuset Asker. All rights reserved.</p>
    <nav>
      <a href="/privacy">Privacy Policy</a> |
      <a href="/terms">Terms of Service</a> |
      <a href="/contact">Contact Us</a>
    </nav>
  </footer>
</template>

<script>
export default {
  name: 'FooterComponent',
}
</script>

<style scoped lang="scss">
.footer {
  background-color: #ffffff;
  border-top: 1px solid #d2d2d7;
  padding: 16px;
  text-align: center;
  font-size: 0.875rem;
  color: #6e6e73;
  height: 10vh;
}

.footer nav {
  margin-top: 8px;
}

.footer a {
  color: #0071e3;
  text-decoration: none;
  margin: 0 8px;
}

@media (max-width: 768px) {
  .footer {
    padding: 12px;
    font-size: 0.8125rem;
  }
}
</style>
