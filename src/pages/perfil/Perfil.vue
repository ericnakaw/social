<template>

  <site-template-vue>

    <span slot="menuesquerdo">
      <img :src="usuario.imagem" alt="" class="responsive-img">
    </span>

    <span slot="principal">

      <h2>Perfil</h2>

      <input type="text" placeholder="Nome" v-model="name">
      <input type="text" placeholder="E-mail" v-model="email">
      <div class="file-field input-field">
        <div class="btn">
          <span>Imagem</span>
          <input type="file" v-on:change="salvaImagem">
        </div>
        <div class="file-path-wrapper">
          <input class="file-path validate" type="text">
        </div>
      </div>
      <textarea class="materialize-textarea" placeholder="Descrição" v-model="descricao"></textarea>
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
        descricao:'',
        password:'',
        password_confirmation:'',
        imagem:''
      }
    },
    created(){
      let usuarioAux = sessionStorage.getItem('usuario');
      if(usuarioAux){
        this.usuario = JSON.parse(usuarioAux);
        this.name = this.usuario.name;
        this.email = this.usuario.email;
        this.descricao = this.usuario.descricao;
      }
    },
    methods:{
      salvaImagem(e){

        let arquivo = e.target.files || e.dataTransfer.files;
        if(!arquivo.length){
          return;
        }

        let reader = new FileReader();
        reader.onloadend = (e) => {
          this.imagem = reader.result;
        }

        reader.readAsDataURL(arquivo[0]);

      },
      perfil(){
        axios.put(`http://webservice.social/api/perfil`, {
          name: this.name,
          email: this.email,
          descricao: this.descricao,
          password: this.password,
          password_confirmation: this.password_confirmation,
          imagem: this.imagem
        },{"headers":{"authorization":"Bearer " + this.usuario.token}})
        .then(response => {
          if(response.data.token){

            this.usuario = response.data;
            sessionStorage.setItem('usuario', JSON.stringify(response.data));
            alert('Perfil atualizado!');

          }else{
            //Erros de validação
            let erros = '';
            for(let erro of Object.values(response.data)){
              erros += erro + " ";
            }
            alert(erros);
          }
          

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