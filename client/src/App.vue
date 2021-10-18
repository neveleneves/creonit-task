<template>
  <main>
    <Form />
    <ProductList />
  </main>
</template>

<script>
import Form from "@/components/Form.vue";
import ProductList from "@/components/ProductList.vue";

export default {
  name: "app",
  components: {
    Form,
    ProductList,
  },
};
</script>
