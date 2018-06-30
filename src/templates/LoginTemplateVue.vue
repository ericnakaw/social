<template>
  <span>
    <header>
      <nav-bar-vue logo="Social" url="/" cor="green darken-1">
        <li v-if="!usuario"><router-link to="/login">Entrar</router-link></li>
        <li v-if="!usuario"><router-link to="/cadastro">Cadastre-se</router-link></li>
        <li v-if="usuario"><router-link to="/perfil">{{usuario.name}}</router-link></li>
        <li v-if="usuario"><a v-on:click="logout()">Sair</a></li>
      </nav-bar-vue>
    </header>

    <main>
      <div class="container">
        <div class="row">
          <grid-vue tamanho="8">
            <card-menu-vue>
              <slot name="menuesquerdo" />
            </card-menu-vue>
          </grid-vue>
          <grid-vue tamanho="4">
            <slot name="principal" />
          </grid-vue>
        </div>
      </div>
    </main>

    <footer-vue cor="green darken-1" logo="Social" descricao="Teste de descrição" ano="2018">
      <li><a class="grey-text text-lighten-3" href="#!">Home</a></li>
      <li><a class="grey-text text-lighten-3" href="#!">Link 2</a></li>
      <li><a class="grey-text text-lighten-3" href="#!">Link 3</a></li>
      <li><a class="grey-text text-lighten-3" href="#!">Link 4</a></li>
    </footer-vue>

  </span>
</template>

<script>
  import NavBarVue from "@/components/layouts/NavBarVue"
  import FooterVue from "@/components/layouts/FooterVue"
  import GridVue from "@/components/layouts/GridVue"
  import CardMenuVue from "@/components/layouts/CardMenuVue"

  export default {
    name: "LoginTemplateVue",
    components: {
      NavBarVue,
      FooterVue,
      GridVue,
      CardMenuVue
    },
    methods:{
      logout(){
        sessionStorage.clear();
        this.usuario = false;
      }
    },
    data(){
      return {
        usuario: false
      }
    },
    created(){
      console.log('created');
      let usuarioAux = sessionStorage.getItem('usuario');
      if(usuarioAux){
        this.usuario = JSON.parse(usuarioAux);
        this.$router.push('/');
      }
    }
  };
</script>

<style>
</style>
