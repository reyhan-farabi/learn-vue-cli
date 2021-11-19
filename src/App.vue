<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h3>
    Hello,
    <a :href="gitlink">{{ fullname }} </a>
  </h3>
  <h1>Welcome to Vue JS</h1>

  <button v-on:click="inputName">Click Here to Change Name</button>

  <p class="todo-label">What you want todo now?</p>

  <form>
    <input
      v-model="randtext"
      type="text"
      placeholder="Just type here"
      v-on:keyup.enter.prevent="addList"
    />
    <button v-on:click.prevent="addList">Add</button>
  </form>

  <ul>
    <li v-for="(list, index) in todolist" :key="index">
      {{ list }}
    </li>
  </ul>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstname: "Reyhan",
      lastname: "Farabi",
      gitlink: "https://github.com/reyhan-farabi/",
      randtext: "",
      todolist: [],
    };
  },
  methods: {
    inputName() {
      this.firstname = prompt("Type your firstname");
      this.lastname = prompt("Type your lastname");
    },
    addList() {
      this.todolist.push(this.randtext);
      this.randtext = "";
    },
  },
  computed: {
    fullname() {
      return `${this.firstname} ${this.lastname}`;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  margin: 0;
}

h3 {
  margin: 0;
  font-weight: 200;
}

button {
  margin: 20px 0;
  padding: 10px 20px;
  cursor: pointer;
}

a {
  text-decoration: none;
  color: #2c3e50;
}

input {
  padding: 10px;
  margin: 0 10px;
  border: 1px solid #2c3e50;
  border-radius: 5px;
}

.todo-label {
  margin: 30px 0 0;
}
</style>
