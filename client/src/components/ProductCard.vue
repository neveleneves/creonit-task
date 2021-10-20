<template>
  <div class="col-6">
    <div class="card">
      <img
        v-bind:src="[product.image.file.url]"
        class="card-img-top"
        v-bind:alt="[product.title]"
      />
      <div class="card-body">
        <h5 class="card-title">{{ product.title }}</h5>
        <h6 class="card-subtitle mb-2 text-muted">{{ product.price }} ₽</h6>
        <a 
        href="#" 
        class="card-link" 
        v-bind:style="{color: color.code}"
        v-for="color of product.colors"
        :key="color.id"
        >{{color.title}}</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product"],
};
</script>
