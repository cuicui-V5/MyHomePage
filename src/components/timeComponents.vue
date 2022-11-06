<template>
  <div class="timeArea">
    <div class="time">{{ current.time }}</div>
    <div class="date">{{ current.date }}</div>
  </div>
</template>

<script setup>
import { reactive } from "vue";
import moment from "moment";
let current = reactive({
  date: moment().format("YYYY 年 MM 月 DD 日"),
  time: moment().format("h:mm:ss"),
});

setInterval(() => {
  current.date = moment().format("YYYY 年 MM 月 DD 日");
  current.time = moment().format("h:mm:ss");
}, 500);
</script>

<style lang="scss" scoped>
.timeArea {
  .time {
    font-size: 70px;
  }
  .date {
    margin-top: -10px;
    font-size: 18px;
  }
}
</style>
