
<template>
    <v-container>
      
        <div align="center">
            <h1>Satış Sayfası</h1>
        </div>

        <v-row>
          <v-col cols="12">
            <v-card>
              <v-card-title>Ürün Sepeti</v-card-title>
              <v-card-text>
                <v-container>
                  <v-row v-for="(product, index) in products" :key="index">
                    <v-col cols="6" class="py-2">{{ product.ürün }}</v-col>
                    <v-col cols="2" class="py-2">{{ product.miktar }}</v-col>
                    <v-col cols="2" class="py-2">{{ product.fiyat }}</v-col>
                    <v-col cols="2" class="py-2">{{ product.tarih }}</v-col>
                  </v-row>
                </v-container>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>

       
              
    </v-container>
  </template>
  
  <script>
  import Sepet from "@/components/Sepet";
  export default {
    components : {
      Sepet,
    },

    data() {
      return {
        products: [],
      };
    },

    created() {
      this.init();
    },

    methods : {
      init() {
        this.products = [
          {
          ürün : "Elma",
          miktar : 30,
          fiyat : 10,
          tarih : "21.01.2020"
          },
          {
          ürün : "Domates",
          miktar : 10,
          fiyat : 2,
          tarih : "01.08.2023"
          },
          {
          ürün : "Armut",
          miktar : 13,
          fiyat : 3,
          tarih : "30.12.2021"
          },
          {
          ürün : "Salatalık",
          miktar : 69,
          fiyat : 1,
          tarih : "11.09.2023"
          },
        ]
      }
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
  };
  </script>