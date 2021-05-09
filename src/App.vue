<template>
  <div id="app">
    <h1 class="title">To Do List</h1>
    <div class="bg-image hover-zoom">
      <img
        src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRYaO9PuYOM-RHeBgJeLZPrQdFF2jVdHHye6g&usqp=CAU"
        width="400"
        height="400"
        alt="IU"
      />
    </div>
    <input
      type="text"
      class="form-control-sm"
      placeholder="할 일 입력"
      v-model="userInput"
      @keyup.enter="addList"
    />
    <p>할 일 &#11015;</p>

    <div class="list-group">
      <button
        class="list-group-item"
        v-for="todo in todoList.filter((todo) => todo.state === 'yet')"
        :key="todo.id"
        @click="moveDoneList(todo)"
      >
        {{ todo.label }}
      </button>
    </div>
    <p>한 일 &#11015;</p>
    <div
      class="list-group-item"
      v-for="todo in todoList.filter((todo) => todo.state === 'done')"
      :key="todo.id"
    >
      {{ todo.label }}
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      userInput: "",
      todoList: [],
    };
  },
  methods: {
    addList() {
      this.todoList.push({
        label: this.userInput,
        state: "yet",
      });
      this.userInput = "";
    },
    moveDoneList(todo) {
      todo.state = todo.state === "yet" ? "done" : "yet";
    },
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #020202;
  margin-top: 30px;
}
.title:hover {
  color: aqua;
}
.list-group-item:hover {
  background-color: rgb(159, 247, 171);
}
.list-group-item {
  margin: 5px;
}
img {
  margin: 10px;
}
p {
  margin: 10px;
  font-size: 30px;
}
</style>
