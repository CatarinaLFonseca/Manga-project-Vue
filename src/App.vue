<template>
  <div id="app">
  <Header />
  <Section  />
  <Footer />    
  </div>
  
</template>

<script>
import Header from './components/Header.vue'
import Section from './components/Section.vue'
import Footer from './components/Footer.vue'

export default {
  components: { Header, Section, Footer }

}
</script>

<style>
  @font-face {
    font-family: 'gibi preto';
    src: url('../fonte-decorativa/KGSummerSunshineShadow.ttf') format('truetype');
    font-weight: normal;
  }

  * {
    margin: 0px;
    padding: 0px;
}

body {
    font-family: 'Roboto', cursive;
    background-image: url('../imagens/fundo0.jpg');
    background-size: 100% 100%;
    background-attachment: fixed;

}

</style>