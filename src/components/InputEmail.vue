<template>
  <div class="InputEmail">
    <div>
      <input v-model="email" type="email" name="email" id="inputEmail" placeholder="Type email address here">
      <button v-on:click="addEmail" type="submit">Add</button>
    </div>
    <div>
      <span>{{ saveMessage }}</span>
      <a v-on:click="dismissMessage">{{dismiss}}</a>

    </div>

    <br>
    <br>
    <br>
    <br>
    <br>
  </div>
</template>

<script>
export default {
  name: 'InputEmail',
  emits: ['add'],
  props: {
    addEmailtoArray: Function,
  },

  data() {
    return {
      email: '',
      saveMessage: '',
      dismiss: '',
    }
  },
  
  methods: {
    addEmail(e) {
      this.addEmailtoArray(this.email)
      if (this.email.trim() === '') {
        return;
      }
      e.preventDefault();

      this.$emit('add', {
        email: this.email,
      })


      this.email = '';
      this.saveMessage = 'Ok! E-mail added.'
      this.dismiss = 'Dismiss.'
    },

    dismissMessage(e) {
      e.preventDefault();
      this.saveMessage= '';
      this.dismiss= '';
    }
}
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
