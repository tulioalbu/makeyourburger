<template>
  <div id="main-banner">
    <h1>Make Your Burger</h1>
  </div>
</template>


<script>
export default {
  name: "BannerComponent"
}
</script>


<style scoped>
 #main-banner {
  background-image: url('../../public/img/burger.jpg');
  background-size: cover;
  background-position: center;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
 }

 #main-banner h1 {
  color: #FFF;
  text-align: left;
  font-size: 60px;
  background-color: rgba(0, 0, 0, 0.5);
  background-clip: border-box;
  padding: 20px 40px;
  font-weight: 700;
  border-radius: 5px;
  margin: 30px auto;
  letter-spacing: 2px;
  border: 2px solid #FFF;
  border-radius: 5px;
  padding: 10px;
 }
</style>