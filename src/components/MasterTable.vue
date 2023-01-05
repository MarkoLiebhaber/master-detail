<template>
  <div class="container">
  <h2>Fake Store</h2>
  <ul class="responsive-table">
    <li class="table-header">
      <div class="col col-1">Auswahl</div>
      <div class="col col-2">Nummer</div>
      <div class="col col-3">Bezeichnung</div>
      <div class="col col-4">Preis</div>
    </li>
    <div style="overflow-y: scroll; height:400px;">
    <li class="table-row" v-for="(item, id) in items" :key="id">
      <div class="col col-1"><input name="select" type="checkbox" v-bind:value="item.id" :checked="selectedItem === item" @change="emit('toggleItem', item)"/></div>
      <div class="col col-2">{{item.id}}</div>
      <div class="col col-3">{{item.title}}</div>
      <div class="col col-4">{{item.price}}</div>
    </li>
    </div>
  </ul>
</div>
</template>


<script setup>
import {defineProps, defineEmits} from "vue";

defineProps({
  items: Array,
  selectedItem: Object
})

const emit = defineEmits( ["toggleItem"])

</script>