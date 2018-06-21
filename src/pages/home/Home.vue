<template>
  <card-conteudo-vue perfil="https://materializecss.com/images/yuna.jpg" nome="Maria Silva" data="20/06/2018 22:30">

    <div class="card-image">
      <img src="https://materializecss.com/images/sample-1.jpg">
      <span class="card-title">Card Title</span>
    </div>
    <div class="card-content">
      <p>I am a very simple card. I am good at containing small bits of information.
      I am convenient because I require little markup to use effectively.</p>
    </div>

  </card-conteudo-vue>
</template>

<script>
  import CardConteudoVue from '@/components/social/CardConteudoVue'
  export default {
    name: "Home",
    components: {
      CardConteudoVue
    },
    data() {
      return {};
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>