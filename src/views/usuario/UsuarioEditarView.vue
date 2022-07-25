<template>
  <div class="perfil">
    <h1>Perfil do Usuário</h1>
    <UsuarioForm>
      <button class="btn" @click.prevent="atualizarUsuario">Atualizar Usuário</button>
    </UsuarioForm>
  </div>
</template>

<script>
import UsuarioForm from '@/components/UsuarioForm.vue';
import { api } from '@/services.js'

export default {
  name: "UsuarioEditarView",
  components: {
    UsuarioForm
  },
  computed: {
    usuario() {
      return this.$store.state.usuario;
    }
  },
  methods: {
    atualizarUsuario() {
      api.put(`/usuario/${this.$store.state.usuario.id}`, this.$store.state.usuario)
        .then(() => {
          this.$store.dispatch("getUsuario", this.$store.state.usuario.id);
          this.$router.push({ name: "usuario" });
        }).catch((err) => console.log(err))
    }
  }
}
</script>

<style scoped>
.perfil {
  margin: 40px 0 32px 32px;
}

h2 {
  margin: 16px 0;
}

span {
  font-weight: 300;
  font-size: 1rem;
  display: inline-block;
  width: 100px;
}
</style>