<template>
  <div>
    <div>
      <input v-model="email" type="email" name="email" id="inputEmail" placeholder="Type email address here">
      <button v-on:click="addEmail" type="submit">Add</button>
    </div>
    <div class="message">
      <span>{{ saveMessage }}</span>
      <a v-on:click="dismissMessage">{{dismiss}}</a>
    </div>
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
        email: this.email
      })


      this.email = '';
      this.saveMessage = 'Ok! E-mail added.';
      this.dismiss = 'Dismiss.';
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

a {
  margin-left: 5px;
  color: #A4A9B7;
}

main {
  margin-top: 85px;
  margin-right: auto;
  margin-left: 50px;
}

main input {
  padding: 10px;
  width: 400px;
  border-radius: 10px;
  border: 1px solid #A4A9B7;
}

main button {
  background-color: #323A5A;
  color: #FFFFFF;
  margin-left: 10px;
  padding: 10px 25px;
  font-weight: bold;
  border-radius: 10px;
  border: none;
}

.message {
  margin-top: 15px;
  text-align: left;
}
span {
  color: #323A5A;
}
</style>
