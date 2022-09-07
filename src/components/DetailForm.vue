  <template>
    <div class="container">
        <ul class="responsive-table">
            <li class="table-header">
                <div>Auswahl</div>
            </li>
            <li class="table-row">
                <div class="col col-1" style="text-align: left">Artikelnummer</div>
                <div class="col col-5" style="text-align: left">{{item.id}}</div>
            </li>
            <li class="table-row">
                <div class="col col-1" style="text-align: left">Bezeichnug</div>
                <div class="col col-5" style="text-align: left">{{item.title}}</div>
            </li>
            <li class="table-row">
                <div class="col col-1" style="text-align: left">Preis</div>
                <div class="col col-5" style="text-align: left">{{item.price}}</div>
            </li>
            <li class="table-row">
                <div class="col col-1" style="text-align: left">Beschreibung</div>
                <div class="col col-5" style="text-align: left">{{item.description}}</div>
            </li>
            <li class="table-row">
                <img :src="item.image" width="150"  height="150"/>
            </li>
        </ul>
    </div>
</template>

<script>

export default {
  name: "DetailForm",
  props: {
    item: null
  }

};
</script>