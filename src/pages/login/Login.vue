<template>

  <login-template-vue>

    <span slot="menuesquerdo">
      <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" alt="" class="responsive-img">
    </span>

    <span slot="principal">

     <h2>Login</h2>

     <input type="text" placeholder="E-mail" v-model="email">
     <input type="password" placeholder="Senha" v-model="password">
     <button class="btn" v-on:click="login()">Entrar</button>
     <router-link class="btn orange" to="/cadastro">Cadastre-se</router-link>

   </span>

 </login-template-vue>

</template>

<script>

  import LoginTemplateVue from '@/templates/LoginTemplateVue'
  import axios from 'axios'

  export default {
    name: "Login",
    data() {
      return {
        email:'',
        password:''
      };
    },
    components: {
      LoginTemplateVue
    },
    methods:{
      login(){
        console.log("ok");
        axios.post(`http://webservice.social/api/login`, {
          email: this.email,
          password: this.password
        })
        .then(response => {
          console.log(response)
          if(response.data.token){
            //Login com sucesso
            console.log('Login com sucesso')
          }else if(response.data.status == false){
            //Login invalido
            console.log('Login invalido')
            alert('Usuario ou Senha invalidos')
          }else{
            //Erros de validação
            console.log('Erros de validação')
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