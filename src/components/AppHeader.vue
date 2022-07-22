<template>
  <header>
    <nav>
      <router-link to="/?_page=1" class="logo">
        <img src="@/assets/ranek.svg" alt="ranek">
      </router-link>
      <router-link to="/login" class="btn">
        Vender | Login
      </router-link>
    </nav>
  </header>
</template>

<script>
export default {
  name: "AppHeader"
}
</script>

<style scoped>
nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px 20px;
  box-shadow: 0 2px 4px rgba(30, 60, 90, .1);
}

.logo {
  padding: 10px 0;
}

.logo img {
  width: 90px;
}
</style>