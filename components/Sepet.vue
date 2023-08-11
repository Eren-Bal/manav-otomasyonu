<template>
    <v-container>
      <v-row>
        <v-col cols="6" class="py-2">Ürün Adı</v-col>
        <v-col cols="2" class="py-2">Ürün Miktarı (Kg)</v-col>
        <v-col cols="2" class="py-2">Birim Fiyatı (TL)</v-col>
        <v-col cols="2" class="py-2">Stok Tarihi (gg.aa.yy)</v-col>
      </v-row>
      <v-row v-for="(product, index) in products" :key="index">
        <v-col cols="6" class="py-2">{{ product.ürün }}</v-col>
        <v-col cols="2" class="py-2">{{ product.miktar }}</v-col>
        <v-col cols="2" class="py-2">{{ product.fiyat }}</v-col>
        <v-col cols="2" class="py-2">{{ product.tarih }}</v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    props: {

      products: {
        type: Array,
        required: true,
      },
    },
  };
  </script>
  
  <style>
  .v-container {
    border: 1px solid #ffffff;
    border-radius: 8px;
    padding: 16px;
  }
  </style>
  