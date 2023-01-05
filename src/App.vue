<template>
  <div id="app">
    <MasterTable :items=posts :selectedItem="selectedItem" @toggleItem="toggleSelectedItem"/>
    <hr class="container">
    <Transition>
      <DetailForm  v-if="selectedItem != null"  :item=selectedItem :key="selectedItem"/>
    </Transition>
  </div>
</template>

<script setup>
import MasterTable from './components/MasterTable.vue'
import DetailForm from './components/DetailForm.vue'
import axios from "axios";
import {onMounted, ref} from "vue";

const posts = ref([])
const selectedItem = ref(null)

let errors = [];
const fetchData = () => {
  axios.get(`https://fakestoreapi.com/products/`)
      .then(response => {
        posts.value = response.data
      })
      .catch(e => {
        errors.push(e)
      });
}
function toggleSelectedItem(item) {
  if(selectedItem.value === item) {
    selectedItem.value = null;
  } else {
    selectedItem.value = item;
  }
}
onMounted(() => {
  fetchData()
})

</script>

<style>
@import '@/assets/styles.css';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 1.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
