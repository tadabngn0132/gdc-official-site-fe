<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- <Header></Header> -->
    <!-- <Footer></Footer> -->
    <CannotAccess></CannotAccess>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Header from '@/components/layout/Header.vue';
import Footer from '@/components/layout/Footer.vue';
import CannotAccess from '@/components/common/CannotAccess.vue';

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    Header,
    Footer,
    CannotAccess
  }
}
</script>
