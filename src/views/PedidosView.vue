<template>
  <div>
  <div class="main-container">
    <h1>Gerenciar Pedidos</h1>
    <DashboardComponent/>
  </div>
</div>
</template>

<script>

import DashboardComponent from '@/components/DashboardComponent.vue';

export default {
  name: "PedidosView",
  components: {
    DashboardComponent
  }
}

</script>
