<template>
  <div id="app">
    <AppHeader />
    <main>
      <transition mode="out-in">
        <router-view />
      </transition>
    </main>
    <AppFooter />
  </div>
</template>

<script>
import AppHeader from '@/components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'

export default {
  components: {
    AppHeader,
    AppFooter
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

ul {
  list-style: none;
}

body {
  font-family: "Avenir", Arial, Helvetica, sans-serif;
  color: #345;
  background: url('./assets/pattern.svg') repeat top;
}

a {
  color: #345;
  text-decoration: none;
}

img {
  /* deixa as imagens responsivas */
  max-width: 100%;
  display: block;
}

#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex: 1;
}

.btn {
  display: block;
  padding: 10px 30px;
  background: #87f;
  border-radius: 4px;
  color: white;
  text-align: center;
  font-size: 1rem;
  box-shadow: 0 4px 8px rgba(30, 60, 90, .2);
  transition: all 0.3s;
  border: none;
  font-family: "Avenir", Arial, Helvetica, sans-serif;
  cursor: pointer;
}

.btn:hover {
  background: #65d;
  transform: scale(1.1);
}

input,
textarea {
  border-radius: 4px;
  border: solid 1px white;
  padding: 15px;
  box-shadow: 0 4px 8px rgba(30, 60, 90, .1);
  transition: all .3s;
  font-size: 1rem;
  font-family: "Avenir", Helvetica, sans-serif, Arial;
  margin-bottom: 15px;
}

input:focus,
input:hover,
textarea:focus,
textarea:hover {
  outline: none;
  transform: scale(1.04);
  box-shadow: 0 6px 12px rgba(30, 60, 90, .2);
  border-color: #87f;
}

.v-enter,
.v-leave-to {
  opacity: 0;
}

.v-enter {
  transform: translate3d(0, -20px, 0);
}

.v-enter-active,
.v-leave-active {
  transition: all .3s;
}
</style>