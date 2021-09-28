<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg=""  />
    <p v-for="element in emailList" :key="element"> {{ element }}</p>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HelloWorld
  },

  data: function () {
    return {
    emailList: [],
    email: 10,
    }
  },

  mounted() {
    console.log(axios);

    for (let i= 0; i < this.email; i++) {
         axios.get('https://flynn.boolean.careers/exercises/api/random/mail')
         .then((response) => {
              this.emailList.push(response.data.response);
              console.log(this.emailList);
    });
    }

    
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
