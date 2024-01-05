<template>
<div class="container" v-if="getFullWeather">
  <Header/>
  <Main/>
</div>
<div class="loading" v-else>
  <div class="loading__element"></div>
</div>
</template>
<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import { mapGetters, mapActions } from "vuex";
export default {
  components: { Header, Main },
  methods: {
    ...mapActions(['getWeather'])
  },
  computed: {
    ...mapGetters(['getFullWeather'])
  },
  created() {
    this.getWeather('Tashkent')
  },
}
</script>
<style lang="scss">
  .loading{
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    &__element{
      position: relative;
      width: 100px;
      height: 100px;
      border-radius: 50%;
      border: 10px solid rgb(0, 123, 255);
      &::before{
        position: absolute;
        content: '';
        display: block;
        width: 100%;
        height: 100%;
        top: -10px;
        left: -10px;
        border: 10px solid transparent;
        border-top-color: yellow;
        border-radius: 50%;
        animation: 1s ball ease infinite;
      }
    }
  }

  @keyframes ball {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }

  /* https://www.figma.com/file/WRwZVv2g8oGSNRVzEoDwOD/Vue-weather?node-id=0%3A1&mode=dev */
</style>