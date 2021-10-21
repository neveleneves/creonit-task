<template>
  <div class="product-card product-card__wrapper">
    <div class="product-card__content">
      <div class="product-card__image-wrapper">
        <img
          v-bind:src="[product.image.file.url]"
          v-bind:alt="[product.title]"
          class="product-card__img"
        />
      </div>
      <div class="product-card__body">
        <h5 class="product-card__title">{{ product.title }}</h5>
        <h6 class="product-card__subtitle">{{ product.price }} ₽</h6>
        <a
          href="#"
          class="product-card__link"
          v-bind:style="{ color: color.code }"
          v-for="color of product.colors"
          :key="color.id"
          >{{ color.title }}</a
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product"],
};
</script>

<style scoped>
.product-card {
  flex: 0 0 auto;
  width: 50%;
}
.product-card__wrapper {
  margin-bottom: 30px;
}
.product-card__content {
  position: relative;
  display: flex;
  flex-direction: column;
  min-width: 0;
  word-wrap: break-word;
  background-color: #fff;
  background-clip: border-box;
  border: 1px solid rgba(0, 0, 0, 0.125);
  border-radius: 0.25rem;
}
.product-card__image-wrapper {
  display: flex;
  width: 634px;
  height: 634px;
  justify-content: center;
  align-items: center;
}
.product-card__img {
  object-fit: fill;
  max-width: 634px;
  max-height: 634px;
  border-top-left-radius: calc(0.25rem - 1px);
  border-top-right-radius: calc(0.25rem - 1px);
}
.product-card__body {
  flex: 1 1 auto;
  padding: 1rem 1rem;
}
.product-card__title {
  margin-bottom: 0.5rem;
}
.product-card__subtitle {
  margin-top: -0.25rem;
  margin-bottom: 0.5rem;
  color: #6c757d;
}
.product-card__link {
  text-decoration: none;
}
.product-card__link + .product-card__link {
  margin-left: 1rem;
}
</style>
