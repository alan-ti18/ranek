<template>
  <section class="login">
    <h1>Login</h1>
    <form action="">
      <label for="email">E-mail</label>
      <input type="email" id="email" name="email" v-model="login.email">
      <label for="senha">Senha</label>
      <input type="senha" id="senha" name="senha" v-model="login.senha">
      <button class="btn" @click.prevent="logar">Logar</button>
    </form>
    <p class="perdeu">
      <a href="/" target="_blank">Perdeu a senha? Clique aqui.</a>
    </p>
    <LoginCriar />
  </section>
</template>

<script>
import LoginCriar from '@/components/LoginCriar.vue'

export default {
  name: "LoginView",
  data() {
    return {
      login: {
        email: "",
        senha: ""
      }
    }
  },
  components: {
    LoginCriar
  },
  methods: {
    logar() {
      this.$store.dispatch("getUsuario", this.login.email)
      this.$router.push({ name: "usuario" });
    }
  }
}
</script>

<style scoped>
.login {
  max-width: 500px;
  margin: 0 auto;
  padding: 0 20px;
}

h1 {
  text-align: center;
  font-size: 2rem;
  margin-top: 40px;
  color: #87f;
}

form {
  display: grid;
}

label {
  margin-bottom: 8px;
  margin-top: 16px;
}

.btn {
  width: 100%;
  max-width: 300px;
  margin-left: auto;
  margin-right: auto;
}

.perdeu {
  text-align: center;
  margin: 20px auto 0 auto;
}

.perdeu a:hover {
  color: #87f;
  text-decoration: underline;
}
</style>