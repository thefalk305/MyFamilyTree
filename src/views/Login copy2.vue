<template>
  <div class="login">
    <form @submit.prevent="login" class="form">
      <h1>Login</h1>
      <label for="username">Username</label>
      <input v-model="username" name="username" type="text" class="input" />
      <label for="password">Password</label>
      <input v-model="password" name="password" type="password" class="input" />
      <button v-if="username" class="btn">Login</button>
      <!-- <button class="btn">Login</button> -->
    </form>
  </div>
</template>

<script>
import { ref, watchEffect } from "vue";
import { useRouter, useRoute } from "vue-router";
import axios from "axios";
// import { exit } from "process";
const items = ref([]);
var record = ref([]);
const password = ref("");
const username = ref("");
export default {
  setup() {
    const url = ref("http://localhost:5001/products");
    const userPw = ref("");
    const router = useRouter();
    const route = useRoute();
    const login = () => {
      getRecord();
      if (password.value === record.value.password) {
        window.user = username.value;
        const redirectPath = route.query.redirect || "/protected";
        router.push(redirectPath);
      } else alert("username and password do not match records");
    };
    return { username, password, login, getRecord };
    async function getRecord() {
      try {
        // const username = "thefalk";
        const response = await axios.get("http://localhost:5001/products");
        items.value = response.data;
        console.log(items.value);
      } catch (err) {
        console.log(err);
      }
      for (var i = 0; i < items.value.length; i++) {
        if (username.value === items.value[i].username) {
          userPw.value = items.value[i].password;
          record.value = items.value[i];
          break;
        }
      }
      return record;
    }
  },
};
// getRecord();
</script>

<style scoped>
.login {
  top: 200px;
}
.form {
  position: absolute;
  top: 20px;
}
</style>
