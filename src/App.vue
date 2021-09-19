<template>
  <div id="app">
    <h1>Hello VUE</h1>
    <p>Välkommen {{ user.firstName }} {{ user.lastName }}!</p>

    <div>
      Du har klickat {{ clicked }} gånger!
      <button @click="onClick">Klicka</button>  

    <div v-if="clicked > 5">
      Bra klickat!
    </div>

      <UserForm :user="user" @save="handleSubmit"/>

      <Pokemon />

    </div>

  </div>
</template>

<script>

import UserForm from "./components/UserForm.vue";
import Pokemon from "./components/Pokemon.vue";

export default {
  name: 'App',
  
  data() {
    return {
      user: {firstName: localStorage.getItem("firstName"), lastName: localStorage.getItem("lastName")},
      clicked: 0,
      
    }
  },
  components: { UserForm, Pokemon },
  methods: {
    onClick() {
      console.log("Klick på knappen!");
      this.clicked ++
    },
    handleSubmit(event) {
      event.preventDefault();
      console.log("Formulär sparat!", event.target.firstName.value);

      localStorage.setItem("firstName", event.target.firstName.value);
      localStorage.setItem("lastName", event.target.lastName.value);


    }
  }

}



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
</style>
