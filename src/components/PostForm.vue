<template>
  <form class="form" @submit.prevent>
    <h4 class="title form__title">Создать пост</h4>
    <input-item
    v-focus
    class="form__input-title"
      v-model="post.title"
      type="text"
      placeholder="Название"
    />
    <input-item
    class="form__input-about"
      v-model="post.body"
      type="text"
      placeholder="Описание"
    />
	<button-item @click="creayePost">Отправить</button-item>
  </form>
</template>
<script>

export default {

  data: () => ({
    post: {
    title: "",
    body: "",
    },
  }),
  methods: {
    creayePost() {
        this.post.id = Math.ceil(Math.random() * 1000);
		this.$emit('create', this.post);
		this.post = {
			title: "",
			body: "",
		};

    },
  },
};
</script>

<style scoped>
.form {
  background-color: #FCFCFD;
  padding: 35px 40px;
  width: 500px;
  border: none;
  border-radius: 5px;
  -webkit-box-shadow: 0px 0px 8px 0px rgba(34, 80, 48, 0.2);
-moz-box-shadow: 0px 0px 8px 0px rgba(34, 80, 48, 0.2);
box-shadow: 0px 0px 8px 0px rgba(34, 80, 48, 0.2);
}
.form__title {
  text-align: center;
  margin-bottom: 15px;
}
.form__input-about {
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>