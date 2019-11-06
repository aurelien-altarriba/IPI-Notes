<template>
  <div id="app">
    <Header/>
    <Liste/>
    <Footer/>
  </div>
</template>

<script>
import Liste from './components/Liste.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  name: 'app',
  components: {
    Liste,
    Header,
    Footer
  }
}
</script>

<style>
#app {
  font-family: Verdana, Arial, sans-serif;
  background: linear-gradient(150deg, #eef, #eed);

  display: flex;
  flex-direction: column;
  align-items: center;

  width: 100%;
  min-height: 100vh;
  padding-bottom: 2rem;
}
</style>
