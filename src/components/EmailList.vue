<template>
  <div class="EmailList">
    <div v-for="email in  emailList" v-bind:key="email" v-bind="$attrs">
      <span>{{ email }}</span>
    </div>
    <p>alo</p>
  </div>
</template>

<script>
export default {
  name: 'EmailList',
  props: {
    emailList: Array,
  },
  
  data() {
    return {
      list: [],
    }
  },

  methods() {

  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
