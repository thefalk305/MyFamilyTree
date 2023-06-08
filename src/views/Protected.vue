<template>
  <div class="protected">
    <h1>Greetings, {{ username }}</h1>
    <button @click="logout">Logout</button>
    <router-link :to="{ name: 'invoices' }">
      <button>Invoices</button>
    </router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: window.user,
    };
  },
  methods: {
    logout() {
      window.user = null;
      this.$router.push({ name: "Index" });
    },
  },
};
</script>

<style scoped>
.protected {
  position: absolute;
  top: 0px;
}
h1 {
  left: 300px;
}
</style>
