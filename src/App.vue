<template>
  <navbar-component :logo="logo_src" :alt="app_name"/>
  <banner-component/>
  <router-view/>
  <footer-component/>

</template>

<script>
import NavbarComponent from './components/NavbarComponent.vue';

import BannerComponent from './components/BannerComponent.vue';

import FooterComponent from './components/FooterComponent.vue';

export default {
  components: {
    NavbarComponent,
    BannerComponent,
    FooterComponent,
  },
  data(){
    return {
      logo_src: "img/logo.png",
      app_name: "Make Your Burger"
    }
  }
  
}
</script>

<style>
* {
  font-family: Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}

h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>