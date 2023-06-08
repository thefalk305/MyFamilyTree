<script setup>
//import axios
import axios from "axios";
import { onBeforeRouteLeave } from "vue-router";
import { ref, inject } from "vue";
import GoBack from "@/components/GoBack.vue";
import BackToTop from "@/components/BackToTop.vue";

const infoTable = ref([])
const items = ref([])
const keys = ref([])
// export default {
//   components: {
//     BackToTop,
//     GoBack,
//   },
//   data() {
//     return {
//       items: ref([]),
//       keys: ref([]),
//     };
//   },

//   created() {
//     this.getProducts();
//   },
//   methods: {
//     //get all products
//     async getProducts() {
//       try {
//         const response = await axios.get("http://localhost:5001/products");
//         this.items = response.data;
//         this.keys = Object.keys(this.items[0]); // get first record to extract field names
//         this.keys.shift(); // remove 'id' field
//         this.keys.push("Actions"); // add 'Actions' row heading
//         // for (const [key] of Object.entries(this.items[0])) {
//         //   this.keysArray.push({ key });
//         //   console.log({ key });
//         // }
//         // this.keysArray.shift(); // remove 'id' field
//         // console.log(this.keysArray);
//       } catch (err) {
//         console.log(err);
//       }
//     },
//     //delete product
//     async deleteProduct(id) {
//       const answer = window.confirm("Are you sure you want to delete this product?");
//       if (!answer) return;
//       try {
//         await axios.delete(`http://localhost:5001/products/${id}`);
//         this.getProducts();
//       } catch (err) {
//         console.log(err);
//       }
//     },
//   },
// };

infoTable.value = inject("infoTable");
items.value = infoTable.value;
keys.value = Object.keys(items.value[0]); // get first record to extract field names
keys.value.shift(); // remove 'id' field
keys.value.push("Actions"); // add 'Actions' row heading

</script>

<template>
  <div id="infotable">
    <router-link :to="{ name: 'Create' }" class="button is-success mt-5" :items="items"
      >Add New</router-link
    >
    <!-- <GoBack /> -->
    <table class="table is-striped is-bordered mt-2">
      <thead class="tblHeading">
        <tr>
          <th>{{ keys[0] }}</th>
          <th>{{ keys[1] }}</th>
          <th class="has-text-centered">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id">
          <td>{{ item.name }}</td>
          <td>{{ item.birthplace }}</td>
          <td class="has-text-centered">
            <router-link
              :to="{ name: 'Edit', params: { id: item.id } }"
              class="button is-info is-small"
              :items="items"
              >Edit</router-link
            >
          </td>
        </tr>
      </tbody>
    </table>
    <p align="center">
      <GoBack />
    </p>
  </div>
  <BackToTop />
</template>

<style scoped>
/* @import "~bulma/css/bulma.css"; */

#infotable {
  position: absolute;
  left: 200px;
  top: 40px;
}
.table {
  margin: auto;
}
</style>
