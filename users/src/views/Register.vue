<template>
  <div>
    <h2>Registro de usuário!</h2>
    <hr />
    <div class="columns is-mobile is-centered">
      <div class="column is-half">
        <p>Nome</p>
        <input
          type="text"
          placeholder="Nome do usuário"
          class="input"
          v-model="name"
        />
        <p>E-mail</p>
        <input
          type="email"
          placeholder="email@email.com"
          class="input"
          v-model="email"
        />
        <p>Senha</p>
        <input
          type="password"
          name="*******"
          class="input"
          v-model="password"
        />
        <hr />
        <button type="submit" class="button is-success" @click="register">
          Cadastrar
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      name: "",
      password: "",
      email: "",
    };
  },
  methods: {
    register() {
        axios.post("http://localhost:8686/user",{
            name: this.name,
            password: this.password,
            email: this.email
        }).then(res =>{
            console.log(res)
        }).catch(err =>{
            var msgErro = err.response.data.err
            console.log(msgErro)
        })
    },
  },
};
</script>
<style scoped>
</style>