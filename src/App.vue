<template>
  <div class="main">
    <div class="mask">
      <timeComponentsVue></timeComponentsVue>
      <ToDoListComponents></ToDoListComponents>
      <div>常用网址</div>
    </div>
  </div>
</template>

<script setup>
import timeComponentsVue from "./components/timeComponents.vue";
import ToDoListComponents from "./components/toDoListComponents.vue";
</script>

<style lang="scss">
.mask {
  position: absolute;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(10px);
  & > div {
    color: aliceblue;
    text-align: center;
    margin: 0 auto;
    width: 1200px;
  }
}
</style>
