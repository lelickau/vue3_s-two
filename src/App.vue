<template>
  <div class="app">
    <h1 class="title title__main">Страница с постами</h1>
    <div class="header">
      <input-item class="header__search" v-model="searchQuery" placeholder="Найти..." />
      <div class="header__options">
        <select-item :options="sortOptions" v-model="selectedSort"></select-item>
      </div>
      <button-item class="header__btn" @click="showDialog">Написать</button-item>
    </div>

    <dialog-item v-model:show="dialogVisible">
      <PostForm @create="addPost" />
    </dialog-item>

    <PostList v-if="!isPostsLoading" :posts="sortedAndSearchedPosts" @remove="removePost" />
    <div class="loading" v-else>
      <img class="loading__img" src="../public/img/alert.svg" alt="alert" />
      <h3 class="loading__title">Загрузка ...</h3>
    </div>
    <div class="page__box">
      <div class="page__number" :class="{'page--active': page === pageNumber}" @click="changePage(pageNumber)" v-for="pageNumber in totalPages" :key="pageNumber" >{{pageNumber}}</div>
    </div>
  </div>
</template>

<script>
import PostList from "./components/PostList.vue";
import PostForm from "./components/PostForm.vue";
import axios from "axios";

export default {
  components: {
    PostList,
    PostForm,
  },

  data: () => ({
    posts: [],
    dialogVisible: false,
    isPostsLoading: false,
    selectedSort: '',
    sortOptions: [
      {value: 'title', name: 'По названию'},
      {value: 'body', name: 'По описанию'},
    ],
    searchQuery: '',
    page: 1,
    limit: 10,
    totalPages: 0,
  }),
  methods: {
    addPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts", {
            params: {
            _limit: this.limit,
            _page: this.page,
            }
          }
        );
        this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit);
        this.posts = response.data;
      } catch (err) {
        alert("Error");
      } finally {
        this.isPostsLoading = false;
      }
    },
    changePage(pageNumber) {
      this.page = pageNumber;
    },
  },
  mounted() {
    this.fetchPosts();
  },
  computed: {
    sortedPosts() {
      return [...this.posts].sort((post1, post2) => {
        return post1[this.selectedSort]?.localeCompare(post2[this.selectedSort]);
      });
    },
    sortedAndSearchedPosts() {
      return this.sortedPosts.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
    }
  },
  watch: {
    page() {
      this.fetchPosts();
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  color: #22252e;
  font-family: "Nunito", sans-serif;
  font-size: 18px;
  line-height: 25px;
  background-color: #fcfcfd;
}
.title {
  font-size: 22px;
  line-height: 30px;
  font-weight: 700;
  margin-top: 20px;
  margin-bottom: 30px;
}
.title__main {
  text-align: right;
}
.header {
  display: flex;
  justify-content: flex-end;
}
.header__btn {
  margin-left: 25px;
}
.header__search {
  margin-right: 30px;
}
.app {
  max-width: 1000px;
  border-radius: 10px;
  background-color: #fcfdfd;
  margin: 0 auto;
  padding: 30px;
  margin-top: 35px;
  -webkit-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
  -moz-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
  box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
}
.loading {
  border-radius: 10px;
  padding: 10px 25px;
  background-color: #ddf7ec;
  color: #7dcef7;
  font-size: 16px;
  line-height: 20px;
  font-weight: 400;
  -webkit-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
  -moz-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
  box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
  display: flex;
  align-items: center;
}
.loading__img {
  display: inline-block;
  width: 30px;
  height: 30px;
  margin-right: 20px;
}

.page__number {
  width: 40px;
  height: 40px;
  font-size: 13px;
  line-height: 18px;
  font-weight: 700;
  background-color: rgb(83,203,168);
  color: #fcfcfd;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  border: none;
  border-radius: 20px;
}
.page__box {
  display: flex;
  justify-content: space-around;
}
.page--active {
  background-color: rgb(39, 228, 124);
}
</style>