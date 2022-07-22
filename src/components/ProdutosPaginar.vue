<template>
  <div class="paginacao" v-if="paginasTotal > 1">
    <ul>
      <li v-for="pagina in rangePaginas" :key="pagina">
        <router-link :to="{ query: query(pagina) }">{{ pagina }}</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ProdutosPaginar",
  props: {
    produtosPorPagina: {
      type: Number,
      default: 1
    },
    produtosTotal: {
      type: Number,
      default: 1
    }
  },
  computed: {
    paginasTotal() {
      const total = this.produtosTotal / this.produtosPorPagina
      return (total !== Infinity) ? Math.ceil(total) : 0
    },
    rangePaginas() {
      const atual = this.$route.query._page;
      const range = 9;
      const offset = Math.ceil(range / 2)
      const total = this.paginasTotal;
      const pagesArray = [];

      for (let i = 1; i <= total; i++) {
        pagesArray.push(i);
      }
      pagesArray.splice(0, atual - offset);
      pagesArray.splice(range, total);
      return pagesArray;
    }
  },
  methods: {
    query(pagina) {
      return {
        ...this.$route.query,
        _page: pagina
      }
    }
  }
}
</script>

<style scoped>
.paginacao {
  text-align: center;
  grid-column: 1 / -1;
}

li {
  display: inline-block;
}

li a {
  padding: 2px 8px;
  border-radius: 2px;
  margin: 4px;
}

li a.router-link-exact-active,
li a:hover {
  background: #87f;
  color: #fff;
  border-radius: 2px;
}
</style>