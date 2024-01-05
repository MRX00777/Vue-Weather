<template lang="pug">
.main-week-day
  h2 {{dayTime}} {{ monthTime }}
  img(src="../assets/img/sun.svg" v-if="descr == 'ясно'")
  img(src="../assets/img/small_rain.svg" v-else-if="descr == 'небольшой дождь'")
  img(src="../assets/img/small_rain.svg" v-else-if="descr == 'легкий дождь'")
  img(src="../assets/img/oblochnost.png" v-else-if="descr == 'небольшая облачность'")
  img(src="../assets/img/oblochnost.png" v-else-if="descr == 'облачно с прояснениями'")
  img(src="../assets/img/oblochnost.png" v-else-if="descr == 'переменная облачность'")
  img(src="../assets/img/rain.svg" v-else-if="descr == 'дождь'")
  img(src="../assets/img/mainly_cloudy.svg" v-else-if="descr == 'пасмурно'")
  img(src="../assets/img/fog.webp" v-else-if="descr == 'туман'")
  img(src="../assets/img/снег.png" v-else-if="descr == 'небольшой снегопад'")
  img(src="../assets/img/снег.png" v-else-if="descr == 'небольшой снег'")
  img(src="../assets/img/снег.png" v-else-if="descr == 'снег'")
  img(src="../assets/img/dimka.png" v-else-if="descr == 'дымка'")
  img(src="../assets/img/sneganddojd.png" v-else-if="descr == 'снег с дождём'")
  img(src="../assets/img/sneganddojd.png" v-else-if="descr == 'дождь с снегом'")
  img(src="../assets/img/else.jpg" v-else)
  span {{ Math.round(day.temp.day) }}°
  p {{ Math.round(day.feels_like.day) }}°
  p {{ day.weather[0].description }}
</template>
<script>
// import { mapGetters } from "vuex";
import unix from '@/timestamp'
export default {
  props: {
    day: Object,
  },
  computed: {
    descr() {
      return this.day.weather[0].description 
    },
    dayTime(){
            return unix(this.day.dt, 'day')
        },
    monthTime(){
            return unix(this.day.dt, 'month')
        },
  },
};
</script>
<style lang="scss">
.main-week-day {
    border-radius: 10px;
    background: rgba(71, 147, 255, 0.20);
    padding: 11px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    color: #939CB0;

    img {
        width: 48px;
        height: 48px;
        display: block;
        margin: 12px 0 13px;
    }

    h2 {
        color: #000;
        font-weight: 500;
        font-size: 18px;
        margin-bottom: 7px;
    }

    p {
        font-size: 14px;
        text-align: center;
        height: 30px;
        &:last-child() {
            margin-top: 6px;
            font-size: 13px;
            
        }
    }

    span {
        color: #000;
        font-size: 18px;
        font-weight: 500;
    }
}
</style>