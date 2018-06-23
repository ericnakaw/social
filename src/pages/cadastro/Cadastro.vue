<template>

  <login-template-vue>

    <span slot="menuesquerdo">
      <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" alt="" class="responsive-img">
    </span>

    <span slot="principal">

      <h2>Cadastro</h2>

        <input type="text" placeholder="Nome" value="">
        <input type="text" placeholder="E-mail" value="">
        <input type="password" placeholder="Senha" value="">
        <input type="password" placeholder="Confirme sua senha" value="">
        <button class="btn">Enviar</button>
        <router-link class="btn orange" to="/login">Já tenho conta</router-link>
      </span>

    </span>

  </login-template-vue>

</template>

<script>

  import LoginTemplateVue from '@/templates/LoginTemplateVue'

  export default {
    name: "Cadastro",
    components: {
      LoginTemplateVue
    },
    data() {
      return {

      };
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>