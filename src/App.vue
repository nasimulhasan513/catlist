<template>
  <div id="app" :class="mode ? 'light' : 'dark'">
    <div class="logo">
      <img src="./assets/cat.png" alt="" height="100px" />
    </div>
    <div>
      <button @click="toggleMode" class="togglebutton">
        <transition name="fade">
          <ion-icon
            :name="mode ? 'moon-outline' : 'sunny-outline'"
            size="large"
            :style="mode ? '' : 'color: white'"
          ></ion-icon>
        </transition>
      </button>
    </div>

    <AddUsers title="Cats list" @addUserFrom="addUser" />
    <Users :users="users" @removeUser="removeUser" :mode="mode" />
  </div>
</template>
<script>
import AddUsers from "./components/AddUsers";
import Users from "./components/Users";
export default {
  components: { AddUsers, Users },

  data() {
    return {
      users: ["deep", "marina", "sayem"],
      mode: true,
    };
  },

  methods: {
    addUser(username) {
      this.users.push(username);
    },
    removeUser(user) {
      this.users.splice(user, 1);
    },
    toggleMode() {
      this.mode = !this.mode;
    },
  },
};
</script>
<style lang="scss" >
* {
  margin: 0;
  padding: 0;
}
#app {
  padding-top: 20px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.dark {
  color: white;
  background: rgba(black, 0.9);
  height: 100vh;
  width: 100vw;
  transition: all 1s ease;
}
.togglebutton {
  position: absolute;
  top: 20px;
  right: 20px;

  background: transparent;

  border: none;
  outline: none;
  padding: 10px;
  border-radius: 4px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

button {
  cursor: pointer;
}
</style>
