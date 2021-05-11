<template>
  <div class="container">
    <ul>
      <transition-group name="fade">
        <li
          v-for="(user, i) in users"
          :key="i"
          @click="removeUser(i)"
          :class="mode ? '' : 'darklistitem'"
        >
          {{ user }}
        </li>
      </transition-group>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    users: {
      type: Array,
    },
    mode: {
      type: Boolean,
    },
  },
  methods: {
    removeUser(user) {
      this.$emit("removeUser", user);
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  justify-content: center;
  align-content: center;
}
ul {
  list-style-type: none;
  li {
    background: rgba(rgb(72, 212, 53), 0.8);

    font-weight: bold;
    margin-bottom: 10px;
    padding: 10px;
    border-radius: 4px;
    max-width: 400px;
    min-width: 300px;
    .darklistitem {
      background: rgba(rgb(76, 207, 35), 0.5) !important;
      box-shadow: 0 4px 4px rgba(white, 0.8);
    }
  }
}
</style>