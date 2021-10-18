<template>
  <section class="container mb-5">
    <div class="row">
      <ProductCard />
      <ProductCard />
    </div>
  </section>
</template>

<script>
import "bootstrap/dist/css/bootstrap.min.css";
// import axios from "axios";

// /**
//  * Метод для получение товаров из категории
//  * @todo Реализовать получение товаров
//  * @param {string | number} category id/slug категории
//  */
// axios
//   .get("https://vue-study.skillbox.cc/api/products", {
//     params: {
//       categoryId: 3,
//     },
//   })
//   .then((response) => {
//     console.log(response);
//   });

// /**
//  * Объект продукта
//  * @typedef Product
//  * @property {number} id айди
//  * @property {string} title заголовок
//  * @property {string} [image] ссылка на картинку
//  * @property {Array <Object>} [colors] возможные цвета
//  */

import ProductCard from "@/components/ProductCard.vue";

export default {
  name: "product-list",
  data() {
    return {
      products: null,
    };
  },
  components: {
    ProductCard,
  },
  computed: {
    /**
     * @returns {Array <Product> | null}
     */
    productsItems() {
      return this.products;
    },
  },
};
</script>
