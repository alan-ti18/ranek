<template>
  <div class="perfil">
    <h1>Perfil do Usuário</h1>
    <h2><span>Nome: </span>{{ usuario.nome }}</h2>
    <h2><span>E-mail: </span>{{ usuario.email }}</h2>
    <h2><span>Rua: </span>{{ usuario.rua }}</h2>
    <h2><span>Nº: </span>{{ usuario.numero }}</h2>
    <h2><span>Cidade: </span>{{ usuario.cidade }}</h2>
    <h2><span>Estado: </span>{{ usuario.estado }}</h2>
  </div>
</template>

<script>
export default {
  name: "UsuarioView",
  computed: {
    usuario() {
      return this.$store.state.usuario;
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