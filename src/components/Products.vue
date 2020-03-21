<template>
  <div id="product-items">
     <img alt="sales rep icon" src="../assets/sales_rep.png" />
     <p>Hello, my name is {{store_data.SalesRep.FirstName}} {{store_data.SalesRep.LastName}}!</p>
    <p v-html="store_data.Message"></p>
    <p><a v-bind:href="'mailto:' + store_data.SalesRep.EmailAddress" target="_top">{{store_data.SalesRep.EmailAddress}}</a></p>
    <ul>
    <li v-for="item in store_data.items" v-bind:key="item.ProductID">
      <input type="checkbox" v-bind:id="item.ProductID" v-bind:value="item" v-model="selectedItems">
      <label v-bind:for="item.ProductID">{{ item.ItemName }}</label>
      <span>{{item.BasePrice | currency}}</span>
       <img title="Click on image to view more details" v-bind:alt="item.ItemName" v-bind:src="item.PhotoName | resizeImage" @click="showProductDetails(item)"/>
       <p>Manufacturer: {{store_data.CompanyName}} </p>
       <img v-bind:alt="store_data.CompanyName" v-bind:src="populateManufactureLogo(store_data.ManufacturerID)"/>
    </li>
    </ul>
    <div v-if="selectedItems.length">    
      <span>Selected Items: </span>
      <ul>
        <li v-for="selectedItem in selectedItems" v-bind:key="selectedItem.ProductID">
          <span>{{selectedItem.ItemName}}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import json from "../assets/data.json";
import DialogBox from '@/components/DialogBox.vue';
import { create } from 'vue-modal-dialogs';

const dialogBox = create(DialogBox, 'content');


export default {
  name: "Products",
  data(){
    return{
      store_data: json,
      selectedItems: []
    }
  },
  methods: {
    showProductDetails (item) {
      dialogBox(item)
    },
    populateManufactureLogo (id) {
      let logoURL = "//images.repzio.com/productimages/" + id + "/logo" + id + "_lg.jpg?width=70";
      return logoURL;
    }
  },
  filters: {
    resizeImage: function (value) {
    return value + "?format=png&width=100";
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
.test {
  &-two {
    background:blue;
  }
}


</style>
