<template>
  <h1>My email list</h1>
  <div v-on:add="console.log('foi')">
    <InputEmail :addEmailtoArray="addEmailtoArray"/>
    <EmailList :emailList="emailList"/>
  </div>
</template>

<script>
import InputEmail from './components/InputEmail.vue'
import EmailList from './components/EmailList.vue'

export default {
  name: 'App',
  components: {
    InputEmail,
    EmailList
  },

  data() {
    return {
      emailList: [],
    }
  },

  methods: {
    addEmailtoArray(param) {
      this.emailList.push(param);
    },

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
