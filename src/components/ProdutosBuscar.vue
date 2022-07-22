<template>
  <form>
    <input type="text" id="busca" name="busca" v-model="busca" placeholder="Buscar...">
    <input type="submit" value="Buscar" id="lupa" @click.prevent="buscarProdutos">
  </form>
</template>

<script>
export default {
  name: "ProdutosBuscar",
  data() {
    return {
      busca: null
    }
  },
  methods: {
    buscarProdutos() {
      this.$router.push({ query: { q: this.busca } })
    }
  }
}
</script>

<style scoped>
form {
  max-width: 600px;
  margin: 30px auto 60px;
  position: relative;
}

#busca {
  width: 100%;
  box-shadow: 0 4px 8px rgba(30, 60, 90, .1);
  padding: 20px;
  border: none;
}

#busca:focus,
#busca:hover {
  transform: scale(1.04);
}

#lupa {
  cursor: pointer;
  height: 62px;
  width: 62px;
  background: url("../assets/search.svg") no-repeat center center;
  border: none;
  text-indent: 200px;
  position: absolute;
  top: 0;
  right: 0;
  box-shadow: none;
}
</style>