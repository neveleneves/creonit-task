<template>
  <section class="container mb-5">
    <form @submit.prevent="onSubmit">
      <div class="form-group">
        <label class="d-block">
          <div class="mb-2">Представьтесь</div>
          <input
            type="text"
            name="fullName"
            v-model="values.fullName"
            v-bind:class="[
              error.name ? 'form-control is-invalid' : 'form-control',
            ]"
          />
          <div class="invalid-feedback">{{ error.name }}</div>
        </label>
      </div>
      <div class="form-group">
        <label class="d-block">
          <div class="mb-2">Адрес доставки</div>
          <input
            type="text"
            name="address"
            v-model="values.address"
            v-bind:class="[
              error.address ? 'form-control is-invalid' : 'form-control',
            ]"
          />
          <div class="invalid-feedback">{{ error.address }}</div>
        </label>
      </div>
      <div class="form-group">
        <label class="d-block">
          <div class="mb-2">Телефон</div>
          <input
            type="tel"
            name="telephone"
            v-model="values.telephone"
            v-bind:class="[
              error.phone ? 'form-control is-invalid' : 'form-control',
            ]"
          />
          <div class="invalid-feedback">{{ error.phone }}</div>
        </label>
      </div>
      <div class="form-group">
        <label class="d-block">
          <div class="mb-2">Эл. почта</div>
          <input
            type="email"
            name="email"
            v-model="values.email"
            v-bind:class="[
              error.email ? 'form-control is-invalid' : 'form-control',
            ]"
          />
          <div class="invalid-feedback">{{ error.email }}</div>
        </label>
      </div>
      <div class="form-group">
        <label class="d-block">
          <div class="mb-2">Комментарий</div>
          <textarea
            name="comment"
            v-model="values.comment"
            class="form-control"
          ></textarea>
          <div class="invalid-feedback">{{ error.comment }}</div>
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
      values: {
        fullName: "",
        address: "",
        telephone: "",
        email: "",
        comment: "",
        accessKey: "",
      },
      error: {
        name: "",
        address: "",
        phone: "",
        email: "",
        comment: "",
      },
    };
  },
  methods: {
    async onSubmit() {
      await this.getAccessKey();
      await this.sendForm();
    },
    async sendForm() {
      try {
        const body = JSON.stringify({
          name: this.values.fullName,
          address: this.values.address,
          phone: this.values.telephone,
          email: this.values.email,
          comment: this.values.comment,
        });
        const headers = { "Content-Type": "application/json" };

        const res = await fetch(
          `https://vue-study.skillbox.cc/api/orders?userAccessKey=${this.accessKey}`,
          {
            method: "POST",
            body,
            headers,
          }
        );
        const data = await res.json();
        this.error = { ...data.error.request };
      } catch (error) {
        console.error(error);
      }
    },
    async getAccessKey() {
      try {
        const res = await fetch(
          "https://vue-study.skillbox.cc/api/users/accessKey",
          {
            method: "GET",
          }
        );
        const data = await res.json();
        this.accessKey = data.accessKey;
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
