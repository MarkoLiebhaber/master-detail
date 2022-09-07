<template>
  <div id="app">
    <MasterTable :items=posts :selectedItem=selectedItem ref="child"/>
    <hr class="container">
    <Transition>
      <DetailForm  v-if="selectedItem != null" v-show="show" :item=this.selectedItem />
    </Transition>
  </div>
</template>

  
<script>
import MasterTable from './components/MasterTable.vue'
import DetailForm from './components/DetailForm.vue'
import axios from "axios";

export default {
  name: 'App',
    components: {
    MasterTable,
    DetailForm
  },
  data() {
    return {
      posts: [],
      errors: [],
      selectedItem: null,
      show: false
    };
  },
  
  created() {
    axios.get(`https://fakestoreapi.com/products/`)
    .then(response => {
      this.posts = response.data
    })
    .catch(e => {
      this.errors.push(e)
    })
  },    
  mounted() {
    this.$watch(
      "$refs.child.selectedItem",
      (new_value) => {
        this.show = false;
        this.selectedItem = new_value;
        if(new_value != null )this.show = true;
      },
    );
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
  @import './assets/styles.css';

.v-enter-active,
.v-leave-active {
  transition: opacity 1.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
