<template>

  <login-template-vue>

    <span slot="menuesquerdo">
      <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" alt="" class="responsive-img">
    </span>

    <span slot="principal">

      <h2>Cadastro</h2>

        <input type="text" placeholder="Nome" v-model="name">
        <input type="text" placeholder="E-mail" v-model="email">
        <input type="password" placeholder="Senha" v-model="password">
        <input type="password" placeholder="Confirme sua senha" v-model="password_confirmation">
        <button class="btn" v-on:click="cadastro()">Enviar</button>
        <router-link class="btn orange" to="/login">Já tenho conta</router-link>
      </span>

    </span>

  </login-template-vue>

</template>

<script>

  import LoginTemplateVue from '@/templates/LoginTemplateVue'
  import axios from 'axios'

  export default {
    name: "Cadastro",
    components: {
      LoginTemplateVue
    },
    data() {
      return {
        name:'',
        email:'',
        password:'',
        password_confirmation:''
      };
    },
    methods:{
      cadastro(){
        console.log("ok");
        axios.post(`http://webservice.social/api/cadastro`, {
          name: this.name,
          email: this.email,
          password: this.password,
          password_confirmation: this.password_confirmation,
        })
        .then(response => {
          //console.log(response)
          if(response.data.token){
            //Login com sucesso
            console.log('Cadastro realizado com sucesso')
            sessionStorage.setItem('usuario', JSON.stringify(response.data));
            this.$router.push('/');
          }else if(response.data.status == false){
            //Erro no cadastro
            alert('Erro no cadastro')
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