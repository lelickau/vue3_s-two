<template>
  <form class="form" @submit.prevent>
    <h4>Создать пост</h4>
    <input-item
      v-model="post.title"
      type="text"
      placeholder="Название"
    />
    <input-item
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
  background-color: rgb(223, 223, 223);
  padding: 35px;
  width: 300px;
  border: #fff 1px solid;
  border-radius: 10px;
  -webkit-box-shadow: 1px 1px 8px 0px rgba(34, 60, 80, 0.2);
  -moz-box-shadow: 1px 1px 8px 0px rgba(34, 60, 80, 0.2);
  box-shadow: 1px 1px 8px 0px rgba(34, 60, 80, 0.2);
}

</style>