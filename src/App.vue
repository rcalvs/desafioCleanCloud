<template>
  <h1>My email list</h1>
    <div>
      <button @click='currentView = "InputEmail"' type="submit">Change A</button>
      <button @click='currentView = "EmailList"' type="submit">Change B</button>
    </div>
    <br>
    <div>
      <component v-bind:is="currentView" :emailList="emailList" :addEmailtoArray="addEmailtoArray"/>
    <!-- <InputEmail :addEmailtoArray="addEmailtoArray" />
    <EmailList :emailList="emailList" /> -->
  </div>
</template>

<script>
import InputEmail from './components/InputEmail.vue';
import EmailList from './components/EmailList.vue';

export default {
  name: 'App',
  components: {
    InputEmail,
    EmailList,
  },

  data() {
    return {
      emailList: [],
      currentView:"InputEmail"
    }
  },

  methods: {
    addEmailtoArray(param) {
      this.emailList.push(param);
    },

    changeView(param) {
      this.emailList = param;

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
