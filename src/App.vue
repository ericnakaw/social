<template>
  <span>
    <header>
      <nav-bar-vue logo="Social" url="#" cor="green darken-1" />
    </header>

    <main>
      <div class="container">
        <router-view/>
      </div>
    </main>

  </span>
</template>

<script>
import NavBarVue from '@/components/layouts/NavBarVue'

export default {
  name: "App",
  components:{
    NavBarVue
  }
};
</script>

<style>
</style>
