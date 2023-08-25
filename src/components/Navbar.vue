<template>
  <div id="nav">
    <router-link to="/" id="logo-url">
        <img :src="logo" :alt="alt" id="logo">
    </router-link>
    <router-link to="/">Home</router-link>
    <router-link to="/pedidos">Pedidos</router-link>
  </div>
</template>
<script>
export default {
    name: "Navbar",
    props: ["logo", "alt"]
};
</script>
<style scoped>
  #nav {
    background-color: #0D0D0D;
    border-bottom: 20px solid #591902;
    padding: 15px 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    font-size: 20px;
  }
  #nav #logo-url{
    margin: auto;
    margin-left: 0;
  }
  #logo{
    width: 60px;
    height: 60px;
  }

  #nav a {
    color: #D96A29;
    text-decoration: none;
    margin: 12px;
    transition: .5s;
  }

  #nav a:hover{
    color: #D9BC9A;
  }
</style>
