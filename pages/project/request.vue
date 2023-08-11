<template>
  <v-container>
    <v-row>
      <v-col>
        <v-text-field v-model="product.name" label="Ürün Adı"
        dense
        hide-details></v-text-field>
      </v-col>
      <v-col>
        <v-text-field
          v-model="product.quantity"
          label="Ürün Miktarı (Kg)"
          dense
          hide-details
        ></v-text-field>
      </v-col>
      <v-col>
        <v-text-field
          v-model.number="product.price"
          label="Birim Fiyatı (TL)"
          hide-details        
          dense
        ></v-text-field>
      </v-col>
      <v-col>
        <v-text-field
          v-model="product.date"
          label="Stok Tarihi (gg.aa.yy))"
          dense      
          hide-details
        ></v-text-field>
      </v-col>
      <v-col>
        <v-btn @click="addProduct" color="grey"><v-icon>mdi-plus</v-icon></v-btn>
      </v-col>
      <v-col>
        <v-btn @click="sales" color="grey"><v-icon>mdi-plus</v-icon></v-btn>
      </v-col>
    </v-row>

    <v-data-table :headers="headers" :items="products">
      <template v-slot:item.action="{ item }">
        <v-btn @click="deleteProduct(item)" color="red">
          <v-icon>mdi-delete</v-icon>
        </v-btn>
      </template>
    </v-data-table>
    <v-switch :label="varMi ? 'Var' : 'Yok'"></v-switch>
  </v-container>
</template>

<script>

import SelectDate from "~/components/SelectDate"

class Product {
  constructor(name, quantity, price, date) {
    this.name = name;
    this.quantity = quantity;
    this.price = price;
    this.date = date;
  }
}

export default {
  data() {
    return {
      product: new Product(),
      products: [],
      headers: [
        { text: "Ürün Adı", value: "name" },
        { text: "Ürün Miktarı", value: "quantity" },
        { text: "Birim Fiyatı", value: "price" },
        { text: "Stok Tarihi", value: "date" },
        { text: "İşlemler", value: "action", sortable: false },
      ],
    };
  },
  methods: {
    addProduct() {
      this.products.push(this.product);
      this.product = new Product();
      //axios POST kodunu yazarım içerisinde this.product u gönderirirm gelen sonuca göre push işlemi yaparım en sonunda ise yeni ürün objesi oluştururum
      /*
      this.$axios
        .post("/backçinin-verdiği-url", this.product)
        .then((res) => {
          //this.products.push(this.product);// idbilgisi dönmez düz oluşturulan objeyi productsa kaydedersin ÖNERİLMEZ
          this.products.push(res.data); //id bilgisi veritabanından geri döner
          this.product = new Product();
        })
        .catch((err) => {
          console.error(err);
        });
        */
    },
    deleteProduct(product) {
      const index = this.products.indexOf(product);
      if (index !== -1) {
        this.products.splice(index, 1);
      }
    },
    components : {
      SelectDate,
    }
  },
};
</script>
