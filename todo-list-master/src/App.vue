<template>
  <div class="todolist">
    <form @submit.prevent class="todo-header">
      <h1 class="title">Список задач</h1>
      <input
        :value="task"
        @input="valueTask"
        class="todo-inputtype"
        tepe="text"
        placeholder="Укажите задачу"
      />
      <button @click="createTask" class="btn">+</button>
    </form>
    <div class="todo-main">
      <ul class="todo-list">
        <li v-bind:key="t" v-for="t in listTask" class="todo-item">
          {{ t.task }}
          <a
            :id="t.id"
            @click.prevent
            @click="delitTask"
            href="#"
            class="todo-list_delit"
          >
            удалить
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'

// import { title } from "process";

export default {
  data() {
    return {
      listTask: [
        { id: 1, task: "Выполнить дизайн" },
        { id: 1, task: "Сделать верстку" },
        { id: 1, task: "Загрузить" },
      ],
      task: "",
      data: 0,
    };
  },

  methods: {
    valueTask() {
      this.task = event.target.value;
    },
    createTask() {
      const newTask = {
        id: Date.now(),
        task: this.task,
      };
      console.log(newTask);
      this.listTask.push(newTask);
      this.task = "";
    },
    delitTask(event) {
      console.log(event.target);
    },
  },
};
</script>

<style scope>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(#f09ce9, #d00765);
  background-repeat: no-repeat;
}
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 100px;
  margin-top: 75px;
}
.title {
  margin-top: 20px;
  margin-bottom: 30px;
  font-size: 32px;
  text-align: center;
}
</style>
