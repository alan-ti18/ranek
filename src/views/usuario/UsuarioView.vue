<template>
  <section class="usuario">
    <nav class="sidenav">
      <ul>
        <li>
          <router-link :to="{ name: 'usuario' }">Produtos</router-link>
        </li>
        <li>
          <router-link :to="{ name: 'compras' }">Compras</router-link>
        </li>
        <li>
          <router-link :to="{ name: 'vendas' }">Vendas</router-link>
        </li>
        <li>
          <router-link :to="{ name: 'usuario-editar' }">Editar Usuário</router-link>
        </li>
        <li>
          <button @click.prevent="deslogar">Deslogar</button>
        </li>
      </ul>
    </nav>
    <transition mode="out-in">
      <router-view></router-view>
    </transition>
  </section>
</template>

<script>
export default {
  name: "UsuarioView",
  computed: {
  },
  methods: {
    deslogar() {
      this.$store.dispatch("deslogarUsuario");
      this.$router.push('/login');
    }
  }
}
</script>

<style scoped>
.usuario {
  display: grid;
  grid-template-columns: minmax(140px, 200px) 1fr;
  max-width: 900px;
  margin: 40px auto;
  grid-gap: 30px;
  padding: 20px;
}

.sidenav ul li a,
.sidenav button {
  padding: 10px 16px;
  display: block;
  background: #f4f7fc;
  margin-bottom: 10px;
  border-radius: 4px;
  transition: all .1s;
}

.sidenav ul li a:hover {
  border-left: 5px solid #87f;
}

.sidenav button:hover {
  background: #87f;
  color: #eee;
}

.sidenav a.router-link-exact-active {
  border-left: 5px solid #87f;
  color: #87f;
}

.sidenav button {
  border: none;
  width: 100%;
  font-size: 1rem;
  text-align: left;
    font-family: "Avenir", Arial, Helvetica, sans-serif;
    cursor: pointer;
  }
  
  @media screen and (max-width: 500px) {
    .usuario {
      grid-template-columns: 1fr;
      margin: 0 auto;
  
    }
}
</style>