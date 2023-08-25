<template>
  <div id="site">
    <Navbar :logo="logo_src" :alt="app_name" />
    <router-view />
    <Footer />
  </div>
</template>
<script>
import Navbar from "./components/Navbar.vue";
import Footer from "./components/Footer.vue";



export default {
  components: {
    Navbar,
    Footer,
    
  },
  data() {
    return {
      logo_src: "/img/logo1.png",
      app_name: "Make Your Burger",
    };
  },
};
</script>
<style>
#site{
  background-color: #D9BC9A;
}
.main-container{
  width: 100%;
  padding-right: 100px;
  padding-left: 100px;
  margin-right: auto;
  margin-left: auto;
  margin-top: 25px;
  margin-bottom: 25px;
  min-height: 650px;
}
* {
  font-family: Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

h1 {
  color: black;
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
}
body{
  background-color: #0D0D0D;
}
</style>
