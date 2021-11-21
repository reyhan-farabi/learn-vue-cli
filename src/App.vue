<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h3>
    Hello<a :href="gitlink">{{ fullname }} </a>
  </h3>
  <h1>Welcome to Vue JS</h1>

  <button v-on:click="inputName">Click Here to Change Name</button>

  <p class="todo-label">What you want todo now?</p>

  <form>
    <input
      v-model="randtext"
      type="text"
      v-bind:placeholder="inputplaceholder"
    />
    <button v-on:click.prevent="addList">Add</button>
  </form>

  <div v-if="todolist.length != 0">
    <span id="listItem" v-for="(list, index) in todolist" :key="index">
      <p>{{ index + 1 }}) {{ list }} -</p>
      <a v-on:click="removeList(index)">
        <img src="https://img.icons8.com/color/48/000000/delete-forever.png" />
      </a>
    </span>
  </div>
  <p v-else>Anda tidak memiliki todolist untuk hari ini</p>
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
      inputplaceholder: "Type Something Here",
      todolist: [],
    };
  },
  methods: {
    inputName() {
      this.firstname = prompt("Type your firstname");
      this.lastname = prompt("Type your lastname");
    },
    addList() {
      if (this.randtext != "") {
        this.todolist.push(this.randtext);
        this.randtext = "";
      }
    },
    removeList(index) {
      this.todolist = this.todolist.filter(
        (item) => item != this.todolist[index]
      );
      console.log("Remove Logged");
      console.log(this.todolist);
    },
  },
  computed: {
    fullname() {
      if (!this.firstname && !this.lastname) {
        if (!this.firstname) {
          return `, ${this.lastname}`;
        } else if (!this.lastname) {
          return `, ${this.firstname}`;
        }
      }
      return `, ${this.firstname} ${this.lastname}`;
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

#listItem {
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

#listItem a img {
  max-width: 32px;
  cursor: pointer;
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
  margin-right: 10px;
  border: 1px solid #2c3e50;
  border-radius: 5px;
}

.todo-label {
  margin: 30px 0 0;
}
</style>
