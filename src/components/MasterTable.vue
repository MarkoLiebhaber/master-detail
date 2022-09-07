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
      <div class="col col-1"><input name="select" type="checkbox" v-bind:value="item.id" v-model="selectedItem_"  @change="uniqueCheck"/></div>
      <div class="col col-2">{{item.id}}</div>
      <div class="col col-3">{{item.title}}</div>
      <div class="col col-4">{{item.price}}</div>
    </li>
    </div>
  </ul>
</div>
</template>

<script>
export default {
  name: 'MasterTable',
  props: {
    items: null
  },
  data() {
    return {
      selectedItem_: [],
      selectedItem: null
    }
  },
  methods: {
    uniqueCheck(e){
      this.selectedItem_ = [];
      if (e.target.checked) {
          this.selectedItem_.push(e.target.value);
          this.selectedItem = this.items.find(function(elem){
            if(elem.id == e.target.value) return elem});
      } else {
        this.selectedItem = null;
      }
    }
  }

}
</script>