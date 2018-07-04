<template>
  <site-template-vue>
    <span slot="menuesquerdo">
      <div class="row valign-wrapper">
        <grid-vue tamanho="4">
          <img :src="usuario.imagem" alt="" class="circle responsive-img"> <!-- notice the "circle" class -->
        </grid-vue>
        <grid-vue tamanho="8">
          <span class="black-text">
            <h5>{{usuario.name}}</h5>
            {{usuario.descricao}}
          </span>
        </grid-vue>
      </div>
    </span>
    <span slot="principal">
      <publicar-conteudo-vue />
      <card-conteudo-vue :perfil="usuario.imagem" :nome="usuario.name" data="20/06/2018 22:30">
        <card-detalhe-vue img="https://materializecss.com/images/sample-1.jpg" titulo="" txt="I am a very simple card. I am good at containing small bits of information. I am convenient because I require little markup to use effectively.">
        </card-detalhe-vue>
      </card-conteudo-vue>
    </span>
    
  </site-template-vue>
</template>

<script>

  import SiteTemplateVue from '@/templates/SiteTemplateVue'
  import CardConteudoVue from '@/components/social/CardConteudoVue'
  import CardDetalheVue from '@/components/social/CardDetalheVue'
  import PublicarConteudoVue from '@/components/social/PublicarConteudoVue'
  import GridVue from '@/components/layouts/GridVue'

  export default {
    name: "Home",
    components: {
      SiteTemplateVue,
      CardConteudoVue,
      CardDetalheVue,
      PublicarConteudoVue,
      GridVue
    },
    data() {
      return {
        usuario:false
      }
    },
    created(){
      let usuarioAux = sessionStorage.getItem('usuario');
      if(usuarioAux){
        this.usuario = JSON.parse(usuarioAux);
      }
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>