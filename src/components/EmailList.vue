<template>
  <div class="container">
    <div class="messageBox" v-for="email in  emailList" v-bind:key="email" v-bind="$attrs">
      <div class="messages">
        <span>{{ email }}</span>
      </div>
      <div class="removes">
        <button :disabled="!remove" v-show="!undo" v-on:click="this.removeEmail(email), disabled()">Remove</button>
        <button :disabled="remove" v-show="undo" v-on:click="this.undoEmail(email), visible()">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 10h10a8 8 0 018 8v2M3 10l6 6m-6-6l6-6" />
        </svg>
          Undo
        </button>
      </div>
    </div>
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
      this.remove = false;
      this.undo = true;
    },

    visible() {
      this.remove = true;
      this.undo= false;
    }  
  }
}

</script>

<style scoped>
*::-webkit-scrollbar {
  width: 5px;
  border-radius: 20px;
}

::-webkit-scrollbar-track {
  background: #CDCFD7;
  border-radius: 20px;
}
 
::-webkit-scrollbar-thumb {
  background: #A4A9B7;
  border-radius: 50px;

}
 
::-webkit-scrollbar-thumb:hover {
  background: #999FB9; 
}

svg {
  width: 12px;
  height: 12px;
  margin: 1px;

}
.container {
  width: 400px;
  min-height: 200px;
  max-height: 200px;
  overflow: auto;
}

.messageBox {
  display: flex;
  justify-content: space-between;
}

button {
  display: flex;
  border: none;
  color: #CDCFD7;
  margin-left: 10px;
  margin-right: 10px;
  text-decoration: none;
  background-color: transparent;
  -webkit-appearance: none;
  -moz-appearance: none;
  cursor: pointer;
}

span {
  display: flex;
  color: #323A5A;
}

</style>
