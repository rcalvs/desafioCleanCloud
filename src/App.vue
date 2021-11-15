<template>
  <div class="father">
    <aside>
      <div class="imgContainer">
        <svg class="dotContainer">
          <circle cx="50" cy="50" r="5" fill="#CD3D5F" />
        </svg> 
        <svg class="dotContainer">
          <circle cx="50" cy="50" r="5" fill="#00E77B" />
        </svg> 
        <svg class="dotContainer">
          <circle cx="50" cy="50" r="5" fill="#FF835C" />
        </svg> 
        <img src="./assets/Logo-CleanCloud-39.png" alt="Logo da CleanCloud">
      </div>
      <div class="buttonContainer">
        <button :class="{selected: isActive}" @click='changeStyle(), currentView = "InputEmail"' type="submit">Create emails</button>
        <button :class="{selected: !isActive}" @click='changeStyle(), currentView = "EmailList"' type="submit">Emails list</button>
      </div>
    </aside>
    <main>
    <h1>My email list</h1>
      <component
        v-bind:is="currentView"
        :emailList="emailList"
        :removeEmail="removeEmail"
        :undoEmail="undoEmail"
        :addEmailtoArray="addEmailtoArray"
      />
    </main>

  <footer>
    This project was developed by Rafael Calvette.
  </footer>
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
      currentView:"InputEmail",
      removedEmail: '',
      isActive: true
    }
  },

  methods: {
    addEmailtoArray(param) {
      this.emailList.push(param);
    },

    changeStyle() {
      console.log(this.isActive);
      this.isActive === true ? this.isActive = false
        : this.isActive = true;
    },

    removeEmail(email) {
      this.removedEmail = email;
      const index = this.emailList.indexOf(email);
      this.emailList[index] = `user "${email}" was removed sucessfully.`;
    },
    
    undoEmail(email) {
      const index = this.emailList.indexOf(email);
      this.emailList[index] = this.removedEmail;
      this.removedEmail = '';
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

* {
  padding: 0;
  margin: 0;
}

#app {
  font-family: 'Poppins', sans-serif;;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.father {
  display: flex;
    padding: 0;
  margin: 0;
}

aside {
  display: flex;
  height: 100vh;
  width: 30%;
  flex-direction: column;
  border-right: 1px solid #A4A9B7;
}

.imgContainer {
  margin-top: 70px;
}

.buttonContainer {
  margin-top: 50px
}

aside button {
  padding: 5px;
  width: 100%;
  margin-bottom: 10px;
  border: none;
  padding: 14px 28px;
  font-size: 16px;
  cursor: pointer;
  text-align: center;

}

.selected {
  background-color: #323A5A;
  color: #FFF;
}

main {
  margin-top: 85px;
  margin-right: auto;
  margin-left: 50px;
}

h1 {
  text-align: left;
  margin-bottom: 50px;
  margin-top: 25px;

}

footer {
  color: #CDCFD7;
  position: absolute;
  bottom: 50px;
  left: 0;
  right: 0;
}

.dotContainer {
  position: absolute;
  top: -40px;
  left: -40px;
}

.dotContainer:nth-child(2) {
  position: absolute;
  top: -40px;
  left: 0;
}

.dotContainer:nth-child(3) {
  position: absolute;
  top: -40px;
  left: -20px;
}
</style>
