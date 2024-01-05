<template lang="pug">
.main-content
  .main-content-left
    p {{ Math.round(getFullWeather.current.temp) }}°
    p Сегодня
    p {{descr}}
    p Город: {{ getFullWeather.name }}
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
  .main-content-right
    div 
      .border
        img(src="../assets/img/temp.svg", alt="")
      span Температура
      p {{ Math.round(getFullWeather.current.temp) }}° - ощущается как {{ Math.round(getFullWeather.current.feels_like) }}°
    div 
      .border
        img(src="../assets/img/pressure.svg", alt="")
      span Давление
      p {{getFullWeather.current.pressure}} мм ртутного столба
    div 
      .border
        img(src="../assets/img/precipitation.svg", alt="")
      span Влажность
      p {{getFullWeather.current.humidity}} %
    div 
      .border
        img(src="../assets/img/wind.svg", alt="")
      span Ветер
      p {{getFullWeather.current.wind_speed}} м/с
    img(src="../assets/img/cloud.svg", alt="")
</template>
<script>
import { mapGetters } from "vuex";
// import unix from '@/timestamp'
export default {
  computed: {
    ...mapGetters(['getFullWeather']),
    descr() {
      return this.getFullWeather.current.weather[0].description
    },
    getTime() {
      return unix(this.getFullWeather.dt, 'day')
    }

  },
};
</script>
<style lang="scss">
.main-content {
  display: flex;
  justify-content: space-between;
  user-select: none;
  gap: 20px;
  @media (max-width: 800px) {
    flex-wrap: wrap;
    justify-content: center;
  }

  &-left {
    border-radius: 20px;
    background: #FFF;
    box-shadow: 2px 5px 25px -3px rgba(180, 180, 180, 0.25);
    padding: 20px;
    width: 400px;
    position: relative;

    p {
      font-size: 25px;
      color: #939CB0;
      margin-top: 14px;
      z-index: 999;
      &:nth-child(1) {
        color: #4793FF;
        font-size: 96px;
        font-weight: 500;
        margin-top: 0;
        z-index: 999;
      }

      &:nth-child(2) {
        color: #000;
        font-size: 40px;
        font-weight: 400;
        margin-bottom: 31px;
        margin-top: 0;
        z-index: 999;
      }
    }

    img {
      position: absolute;
      top: 28px;
      right: 20px;
      width: 100%;
      max-width: 150px;
      z-index: 0;

      @media (max-width: 450px) {
        max-width: 100px;
      }
    }
  }

  &-right {
    max-width: 750px;
    padding: 42px 0 41px 32px;
    width: 100%;
    border-radius: 20px;
    background: #FFF;
    box-shadow: 2px 5px 25px -3px rgba(180, 180, 180, 0.25);
    display: flex;
    flex-direction: column;
    position: relative;
    gap: 22px;
    z-index: 0;
    @media (max-width: 400px) {
      padding: 10px 0 10px 10px;
        }
    >img {
      position: absolute;
      right: 0;
      top: 0;
      z-index: -1;
      width: 100%;
      
    }

    div {
      display: flex;
      align-items: center;
      gap: 23px;

      .border {
        width: 38px;
        height: 38px;
        background: #fff;
        box-shadow: 1px 4px 10px -1px rgba(71, 147, 255, 0.2);
        padding: 10px;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 50%;
       
      }

      span {
        width: 96px;
        font-size: 14px;
        color: #939CB0;
      }

      p {
        font-size: 16px;
        color: black;
      }
    }
  }
}</style>