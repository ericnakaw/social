<template>

  <login-template-vue>

    <h2>Login</h2>

    <input type="text" placeholder="E-mail" value="">
    <input type="text" placeholder="Password" value="">
    <button type="button" class="btn">Entrar</button>

  </login-template-vue>

</template>

<script>

  import LoginTemplateVue from '@/templates/LoginTemplateVue'
  import SiteTemplateVue from '@/templates/SiteTemplateVue'
  import CardConteudoVue from '@/components/social/CardConteudoVue'
  import CardDetalheVue from '@/components/social/CardDetalheVue'
  import PublicarConteudoVue from '@/components/social/PublicarConteudoVue'

  export default {
    name: "Login",
    components: {
      LoginTemplateVue,
      SiteTemplateVue,
      CardConteudoVue,
      CardDetalheVue,
      PublicarConteudoVue
    },
    data() {
      return {};
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>