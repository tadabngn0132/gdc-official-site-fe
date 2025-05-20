<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- <Header></Header> -->
    <!-- <Footer></Footer> -->
    <!-- <CannotAccess></CannotAccess> -->
    <!-- <Loading></Loading>
    <div class="submit">
      <ButtonLoading></ButtonLoading>
      <span class="submit__text">Save Changes</span>
    </div> -->
    <!-- <NotFound></NotFound> -->

    <Slider></Slider>
    <Tooltip></Tooltip>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Header from '@/components/layout/Header.vue';
import Footer from '@/components/layout/Footer.vue';
import CannotAccess from '@/components/common/CannotAccess.vue';
import Loading from '@/components/common/Loading.vue';
import ButtonLoading from '@/components/common/ButtonLoading.vue';
import NotFound from '@/components/common/NotFound.vue';
import Slider from '@/components/common/Slider.vue';
import Tooltip from '@/components/common/Tooltip.vue';

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    Header,
    Footer,
    CannotAccess,
    Loading,
    ButtonLoading,
    NotFound,
    Slider,
    Tooltip
  }
}
</script>

<style scoped lang="scss">
.home {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  .submit {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    margin-top: 20px;
    background-color: black;
    width: fit-content;
    padding: 0.5em 1em;
    border-radius: 0.75em;

    &__text {
      color: white;
      font-weight: 450;
    }
  }
}

</style>
