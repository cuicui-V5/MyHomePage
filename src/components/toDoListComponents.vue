<template>
  <div class="todoListArea">
    <div class="addNew">
      <el-input
        v-model="mewTodoTittle"
        placeholder="Please input"
        @keydown.enter="addNewTodo"
      />
      <el-button type="primary" plain @click="addNewTodo">添加</el-button>

      <displayArea
        :todos="todos"
        @delItem="deleteItem"
        @changeChk="changeChk"
      ></displayArea>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

import displayArea from "./todoListDisplayArea.vue";

let todos = ref([
  {
    id: "001",
    tittle: "吃饭",
    done: false,
  },
  {
    id: "002",
    tittle: "睡觉",
    done: false,
  },
  {
    id: "003",
    tittle: "喝水",
    done: false,
  },
  {
    id: "004",
    tittle: "玩游戏",
    done: true,
  },
]);

let mewTodoTittle = ref("");

function addNewTodo() {
  if (mewTodoTittle.value !== "") {
    const newTodoItem = {
      id: Math.ceil(Math.random() * 100000),
      tittle: mewTodoTittle.value,
      done: false,
    };
    todos.value.push(newTodoItem);
  }
}

function deleteItem(id) {
  console.log(id);
  console.log(todos);
  todos.value = todos.value.filter((item) => {
    return item.id != id;
  });
}
function changeChk(chk, id) {
  console.log(chk, id);
  todos.value.forEach((item) => {
    if (item.id === id) {
      item.done = chk;
    }
  });
}
</script>

<style lang="scss">
.todoListArea {
  margin-top: 20px;
  .el-input {
    width: 200px;
  }
  .displayArea {
    width: 800px;
    margin: 0 auto;
    text-align: center;

    .doing,
    .done {
      margin: 10px;
      .tittle {
        font-size: 20px;
      }
    }
  }
}
</style>
