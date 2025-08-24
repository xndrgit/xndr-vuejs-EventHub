<template>
  <header class="header">
    <img src="/assets/logo.png" alt="Fontenehuset Asker Logo" class="logo" />
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
}
</script>

<style scoped lang="scss">
.header {
  background-color: #ffffff;
  height: 10vh;
  display: flex;
  justify-content: center;
  align-items: center;
  border-bottom: 1px solid #d2d2d7;
}

.logo {
  max-height: 50px;
}
</style>
