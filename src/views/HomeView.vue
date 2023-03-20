<template>
  <div class="main-container">
    <h1>Monte o seu burger</h1>
    <BurgerFormComponent/>
  </div>
</template>

<script>
import BannerComponent from '@/components/BannerComponent.vue';
import BurgerFormComponent from '@/components/BurgerFormComponent.vue';

export default {
  name: "HomeView",
  components: {
    BannerComponent,
    BurgerFormComponent
  }
}
</script>
