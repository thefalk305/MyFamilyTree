<script >
import { ref, watchEffect, inject } from "vue";
import { useRouter, useRoute } from "vue-router";
import axios from "axios";
// import { exit } from "process";
const items = ref([]);
var record = ref([]);
const password = ref("");
const username = ref("");
const userPw = ref("");

var infoTable = ref([]);
infoTable.value = inject("infoTable");


export default {
  setup() {
    password.value = "";
    username.value = "";
    const url = ref("http://localhost:5001/products");
    const router = useRouter();
    const route = useRoute();
    const login = () => {
      // getRecord();
      for (var i = 0; i < items.value.length; i++) {
        if (username.value === items.value[i].username) {
          userPw.value = items.value[i].password;
          record.value = items.value[i];
          break;
        }
      }

      if (password.value === record.value.password) {
        window.user = username.value;
        const redirectPath = route.query.redirect || "/protected";
        router.push(redirectPath);
      } else alert("username and password do not match records");
    };
    // return { username, password, login, getRecord };
    return { username, password, login };
  },
};
// async function getRecord() {
//   try {
//     // const username = "thefalk";
//     const response = await axios.get("http://localhost:5001/products");
//     items.value = response.data;
//   } catch (err) {
//     console.log(err);
//   }
//   return record;
// }
// getRecord();
</script>

<template>
  <div class="login">
    <form @submit.prevent="login" class="form">
      <h1>Login</h1>
      <label for="username">Username</label>
      <input
        v-model="username"
        name="username"
        type="text"
        class="input"
        placeholder="username"
      />
      <label for="password">Password</label>
      <input
        v-model="password"
        name="password"
        type="password"
        class="input"
        placeholder="password"
      />
      <button v-if="username && password" class="btn">Login</button>
      <!-- <button class="btn">Login</button> -->
    </form>
  </div>
</template>

<style scoped>
.login {
  top: 200px;
}
.form {
  position: absolute;
  top: 20px;
}
</style>
