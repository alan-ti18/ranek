<template>
  <div>
    <section>
      <h2>Adicionar Produto</h2>
      <ProdutoAdicionar />
      <h2>Seus Produtos</h2>
      <transition-group v-if="usuario_produtos && usuario_produtos.length > 0" tag="ul" name="list">
        <li v-for="(produto, index) in usuario_produtos" :key="index">
          <ProdutoItem :produto="produto">
            <p>{{ produto.descricao }}</p>
            <button class="deletar" @click="deletarProduto(produto)">Deletar Produto</button>
          </ProdutoItem>
        </li>
      </transition-group>
      <p v-else-if="usuario_produtos.length == 0">Não há produtos a serem listados.</p>
    </section>
  </div>
</template>

<script>
import ProdutoAdicionar from '@/components/ProdutoAdicionar.vue'
import ProdutoItem from '@/components/ProdutoItem.vue'
import { api } from '@/services.js'
import { mapState, mapActions } from 'vuex'

export default {
  name: "UsuarioProdutosView",
  components: {
    ProdutoAdicionar,
    ProdutoItem
  },
  computed: {
    ...mapState(["login", "usuario", "usuario_produtos"])
  },
  methods: {
    ...mapActions(["getUsuarioProdutos"]),
    deletarProduto(produto) {
      const confirmar = window.confirm(`Deseja realmente excluir ${produto.nome}?`)
      if (confirmar) {
        api.delete(`/produto/${produto.id}`)
          .then(() => {
            this.getUsuarioProdutos();
            window.alert("Produto excluído com sucesso!");
          }).catch(err => console.log(err))
      }
    }
  },
  created() {
    if (this.login) {
      this.getUsuarioProdutos();
    }
  },
  watch: {
    login() {
      this.getUsuarioProdutos();
    }
  }
}
</script>

<style scoped>
h2 {
  margin-bottom: 20px;
}

.deletar {
  position: absolute;
  top: 0;
  right: 0;
  background: url("../../assets/remove.svg") no-repeat center center;
  width: 24px;
  height: 24px;
  text-indent: -140px;
  overflow: hidden;
  border: none;
  cursor: pointer;
}

.list-enter-active,
.list-leave-active {
  transition: all .3s;
}

.list-enter,
.list-leave-to {
  opacity: 0;
  transform: translate3d(20px, 0, 0);
}
</style>