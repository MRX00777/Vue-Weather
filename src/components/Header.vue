<template lang="pug">
header.header
  nav.header-nav
    a(href="#") 
      img(src="../assets/img/logo.svg", alt="")
      span MRX weather
    .header-nav-search
      img(src="../assets/img/raindrop.svg", alt="")
      input(type="text", placeholder="Выбрать город...", v-model="query" @keydown.enter="getWeather(query)")
</template>
<script>
import { mapActions } from "vuex";
export default {
  data() {
    return {
      query: "",
    };
  },
  methods: {
    ...mapActions(['getWeather'])
  },
};
</script>
<style lang="scss">
.header {
  padding: 20px 0 30px;
  &-nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    @media (max-width: 500px) {
          flex-wrap: wrap;
          gap: 20px;
        }
    a {
      display: flex;
      align-items: center;
      gap: 20px;
      font-size: 25px;
      line-height: 30px;
      text-transform: uppercase;
      color: #4793ff;
      span {
        font-weight: 700;
      }
    }
    &-search {
      display: flex;
      align-items: center;
      gap: 20px;
      input {
        background: rgba(71, 147, 255, 0.2);
        border-radius: 10px;
        padding: 9px;
        font-weight: 500;
        font-size: 16px;
        line-height: 20px;
        color: #000000;
        border: none;
        outline: none;
      }
    }
  }
}
</style>