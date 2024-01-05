<template lang="pug">
.main-week
  .main-week-btns
    button На неделю
    button(@click="getWeather('Tashkent')") Отменить
  .main-week-days
    PerDay(
      v-for="(day, i) in getDailyWeather" :key="i"
      :day="day"
    )
</template>
<script>
import PerDay from "@/components/PerDay.vue";
import { mapGetters, mapActions } from "vuex";
export default {
  components: { PerDay },
  methods: {
    ...mapActions(['getWeather'])
  },
  computed: {
    ...mapGetters(['getDailyWeather'])
  },
};
</script>
<style lang="scss">
.main-week {
  &-btns {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 50px 0 27px;
    button {
      padding: 7px 21px;
      background: #ffffff;
      box-shadow: 2px 5px 25px -3px rgba(180, 180, 180, 0.25);
      border-radius: 5px;
      font-size: 18px;
      color: black;
      outline: none;
      border: none;
      transition: 200ms;
      cursor: pointer;
      &:hover{
        background: #4793FF;
        color: white;
      }
    }
  }
  &-days{
    display: grid;
    grid-template-columns: repeat(8, 1fr);
    gap: 20px;
    background: #FFFFFF;
    box-shadow: 2px 5px 25px -3px rgba(180, 180, 180, 0.25);
    border-radius: 0px 0px 20px 20px;
    padding: 20px;
    @media (max-width: 1100px) {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
    }
    @media (max-width: 800px) {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
    }
  }
}
</style>