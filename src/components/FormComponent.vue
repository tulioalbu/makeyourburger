<template>
  <div>
    <form id="form-component">
      <div class="input-container">
        <label for="nome">Nome do Cliente: </label>
        <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
      </div>
      <div class="input-container">
        <label for="pao">Escolha o tipo de pão</label>
        <select name="pao" id="pao" v-model="pao">
            <option value="">Selecione o seu pão</option>
            <option value="integral">Integral</option>
        </select>
      </div>

    </form>
  </div>
</template>


<script>
export default {
  name: "FormComponent"
  
}
</script>

<style scoped>

</style>
