<template>

  <site-template-vue>

    <span slot="menuesquerdo">
      <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" alt="" class="responsive-img">
    </span>

    <span slot="principal">

      <h2>Perfil</h2>

      <input type="text" placeholder="Nome" v-model="name">
      <input type="text" placeholder="E-mail" v-model="email">
      <div class="file-field input-field">
        <div class="btn">
          <span>Imagem</span>
          <input type="file">
        </div>
        <div class="file-path-wrapper">
          <input class="file-path validate" type="text">
        </div>
      </div>
      <input type="password" placeholder="Senha" v-model="password">
      <input type="password" placeholder="Confirme sua senha" v-model="password_confirmation">
      <button class="btn" v-on:click="perfil()">Atualizar</button>
    </span>

  </span>

</site-template-vue>

</template>

<script>

  import SiteTemplateVue from '@/templates/SiteTemplateVue'
  import axios from 'axios'

  export default {
    name: "Perfil",
    components: {
      SiteTemplateVue
    },
    data() {
      return {
        usuario:false,
        name:'',
        email:'',
        password:'',
        password_confirmation:''
      };
    },
    created(){
      let usuarioAux = sessionStorage.getItem('usuario');
      if(usuarioAux){
        this.usuario = JSON.parse(usuarioAux);
        this.name = this.usuario.name;
        this.email = this.usuario.email;
      }
    },
    methods:{
      perfil(){
        axios.put(`http://webservice.social/api/perfil`, {
          name: this.name,
          email: this.email,
          password: this.password,
          password_confirmation: this.password_confirmation,
        },{"headers":{"authorization":"Bearer " + this.usuario.token}})
        .then(response => {

            console.log(response.data);

        })
        .catch(e => {
          console.log(e)
          alert("Erro! Tente novamente mais tarde!")
        })
      }
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>