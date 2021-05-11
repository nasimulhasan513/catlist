<template>
  <div>
    <h1>{{ title }}</h1>
    <div class="input__box">
      <input
        type="text"
        v-model="username"
        placeholder="Cat name"
        @keypress.enter="addUser"
      />
      <button class="add_user_button" @click="addUser">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
    },
  },
  data() {
    return {
      username: "",
    };
  },
  methods: {
    addUser() {
      if (this.username) {
        this.$emit("addUserFrom", this.username);
        this.username = "";
      } else {
        alert("Username can't be empty");
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.input__box {
  padding: 20px;
  input {
    padding: 10px;
    border-radius: 4px;
    border: 1px solid rgba(#000000, 0.8);
    outline: none;
  }
  .add_user_button {
    margin-left: 15px;
    padding: 12px 20px;
    border-radius: 4px;
    font-weight: bold;
    border: none;
    color: white;
    background: linear-gradient(rgb(22, 192, 135), green);
    transition: all 1s ease;
    box-shadow: 0 3px 4px rgba(rgb(63, 59, 59), 0.2);

    &:hover {
      background: linear-gradient(rgb(94, 91, 223), rgb(83, 69, 207));
      transform: translateY(-2px);
      box-shadow: 0 5px 4px rgba(rgb(155, 146, 146), 0.6);
    }
    &:active {
      transform: translateY(-1px);
    }
  }
}
</style>