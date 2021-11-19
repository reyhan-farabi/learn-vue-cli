<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h3>
    Hello,
    <a :href="gitlink">{{ fullname }} </a>
  </h3>
  <h1>Welcome to Vue JS</h1>

  <button v-on:click="inputName">Click Here to Change Name</button>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstname: "Reyhan",
      lastname: "Farabi",
      gitlink: "https://github.com/reyhan-farabi/",
    };
  },
  methods: {
    inputName() {
      this.firstname = prompt("Type your firstname");
      this.lastname = prompt("Type your lastname");
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
  margin-top: 20px;
  padding: 10px 20px;
  cursor: pointer;
}

a {
  text-decoration: none;
  color: #2c3e50;
}
</style>
