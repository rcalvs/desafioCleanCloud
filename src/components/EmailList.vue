<template>
  <div class="EmailList">
    <div v-for="email in  emailList" v-bind:key="email" v-bind="$attrs">
      <span>{{ email }}</span>
      <button :disabled="!remove" v-show="!undo" v-on:click="this.removeEmail(email), disabled()">Remove</button>
      <button :disabled="remove" v-show="undo" v-on:click="this.undoEmail(email), visible()">Undo</button>
    </div>
    <p>alo</p>
  </div>
</template>

<script>
export default {
  name: 'EmailList',
  props: {
    emailList: Array,
    removeEmail: Function,
    undoEmail: Function
  },
  
  data() {
    return {
      list: [],
      remove: true,
      undo: false
    }
  },

  methods: {
    disabled() {
      this.remove = false
      this.undo = true
    },

    visible() {
      this.remove = true
      this.undo= false
    }
  
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
