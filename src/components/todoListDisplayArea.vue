<template>
  <div class="displayArea">
    <div class="doing">
      <div class="tittle">未完成</div>
      <ul>
        <li v-for="item in doing" :key="item.id">
          <el-checkbox
            :label="item.tittle"
            size="large"
            @change="changeChk($event, item.id)"
            :checked="item.done"
          />

          <el-button type="danger" @click="deleteItem(item.id)">删除</el-button>
        </li>
      </ul>
    </div>

    <div class="done">
      <div class="tittle">已完成</div>
      <ul>
        <li v-for="item in done" :key="item.id">
          <el-checkbox
            :label="item.tittle"
            size="large"
            @change="changeChk($event, item.id)"
            :checked="item.done"
          />

          <el-button type="danger" @click="deleteItem(item.id)">删除</el-button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";
let emit = defineEmits(["delItem", "changeChk"]);
let data = defineProps(["todos"]);

let doing = computed(() => {
  return data.todos.filter((item) => {
    return !item.done;
  });
});
let done = computed(() => {
  return data.todos.filter((item) => {
    return item.done;
  });
});

function deleteItem(id) {
  emit("delItem", id);
}

function changeChk(e, id) {
  emit("changeChk", e, id);
}
</script>
<style lang="scss" scoped>
.el-checkbox {
  color: aliceblue;
}
</style>
