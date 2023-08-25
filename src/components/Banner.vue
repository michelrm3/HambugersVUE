<template>
  <div id="main-banner">
    <h1>Make Your Burger</h1>
  </div>
</template>
<script>
export default {
  name: "Banner",
};
</script>
<style scoped>
#main-banner {
  background-image: url("/public/img/burger1.jpg");
  background-position: right;
  background-repeat: no-repeat;
  background-size: 100% auto;
  height: 400px;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}
#main-banner h1{
    color: #F2A74B;
    text-align: center;
    font-size: 60px;
    background-color: #591902;
    padding: 20px 40px;
    border-radius: 0px 20px 20px 0px;
}
</style>
