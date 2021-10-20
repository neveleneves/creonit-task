<template>
  <section class="container mb-5">
    <form @submit.prevent="onSubmit" class="mb-2">
      <div class="d-flex w-50 justify-content-between">
        <button type="submit" class="btn btn-primary">Вывести товары</button>
        <input
          type="text"
          name="category"
          v-model="category"
          class="form-control w-75"
          placeholder="ID категории"
        />
      </div>
    </form>
    <div class="row">
      <ProductCard
        v-for="product of productsItems"
        :key="product.id"
        v-bind:product="product"
      />
    </div>
  </section>
</template>

<script>
import "bootstrap/dist/css/bootstrap.min.css";
import ProductCard from "@/components/ProductCard.vue";

/**
 * Метод для получение товаров из категории
 * @todo Реализовать получение товаров
 * @param {string | number} category id/slug категории
 */

/**
 * Объект продукта
 * @typedef Product
 * @property {number} id айди
 * @property {string} title заголовок
 * @property {string} [image] ссылка на картинку
 * @property {Array <Object>} [colors] возможные цвета
 */

export default {
  name: "product-list",
  data: () => {
    return {
      products: null,
      category: null,
    };
  },
  methods: {
    Product(item) {
      this.id = item.id;
      this.title = item.title;
      this.image = item.image;
      this.colors = item.colors;
      this.price = item.price;
    },
    async onSubmit() {
      await this.todo(this.category);
    },
    async todo(category) {
      try {
        const res = await fetch(
          `https://vue-study.skillbox.cc/api/products?categoryId=${category}`
        );
        const data = await res.json();
        this.products = data.items.map((item) => new this.Product(item));
      } catch (error) {
        console.error(error);
      }
    },
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
