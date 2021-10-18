<template>
  <section class="container mb-5">
    <form @submit="checkForm" action="" method="post">
      <div class="form-group">
        <label class="d-block">
          <div class="mb-2">Представьтесь</div>
          <input
            type="text"
            name="fullName"
            v-model="fullName"
            class="form-control is-invalid"
          />
          <div class="invalid-feedback">Ошибка</div>
        </label>
      </div>
      <div class="form-group">
        <label class="d-block">
          <div class="mb-2">Адрес доставки</div>
          <input
            type="text"
            name="adress"
            v-model="adress"
            class="form-control"
          />
        </label>
      </div>
      <div class="form-group">
        <label class="d-block">
          <div class="mb-2">Телефон</div>
          <input
            type="tel"
            name="telephone"
            v-model="telephone"
            class="form-control"
          />
        </label>
      </div>
      <div class="form-group">
        <label class="d-block">
          <div class="mb-2">Эл. почта</div>
          <input
            type="email"
            name="email"
            v-model="email"
            class="form-control"
          />
        </label>
      </div>
      <div class="form-group">
        <label class="d-block">
          <div class="mb-2">Комментарий</div>
          <textarea
            class="form-control"
            name="comment"
            v-model="comment"
          ></textarea>
        </label>
      </div>
      <button type="submit" class="btn btn-primary">Отправить</button>
    </form>
  </section>
</template>

<script>
export default {
  name: "form-custom",
  data: () => {
    return {
      fullName: "",
      adress: "",
      telephone: "",
      email: "",
      comment: "",
    };
  },
  methods: {
    checkForm: (e) => {
      e.preventDefault();

      console.log(this.fullName);
    },
  },
  //   components: {
  //     ProductCard,
  //   },
  //   computed: {
  //     /**
  //      * @returns {Array <Product> | null}
  //      */
  //     productsItems() {
  //       return this.products;
  //     },
  //   },
};
</script>
