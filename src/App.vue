<template>
<div class="app">
    <h1>Страница с постами</h1>
    <button-item @click="showDialog">Создать пост</button-item>
    <dialog-item v-model:show="dialogVisible">
        <PostForm @create="addPost"/>
    </dialog-item>

    <PostList :posts="posts" @remove="removePost"/>
</div>
</template>

<script>
import PostList from './components/PostList.vue';
import PostForm from './components/PostForm.vue';

export default {
    components: {
        PostList,
        PostForm,
    },

    data: () => ({
        posts: [
            {id: 154, title: 'Инструменты разработчика', body: 'На данный момент в бета-тестировании — интеграция с Vuex и Router в разработке'},
            {id: 169, title: 'CDN', body: 'Для production рекомендуется указывать конкретную версию и сборку, чтобы избежать неожиданных поломок при выходе новых версий'},
            {id: 184, title: 'Скачивание и самостоятельный хостинг', body: 'Если нужно избежать использования систем сборки, но нет возможности использовать CDN в production — в таком случае можно скачать соответствующий .js файл и разместить его на собственном веб-сервере. После чего подключать его, с помощью тега <script>, точно также, как и при подключении с CDN.'},
            {id: 124, title: 'npm', body: 'npm — рекомендованный способ установки при создании больших приложений на Vue. Он прекрасно сочетается с системами сборки, такими как webpack (opens new window)или Rollup (opens new window).'},
        ],
        dialogVisible: false,

    }),
    methods: {
        addPost(post) {
            this.posts.push(post);
            this.dialogVisible = false;
        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id);
        },
        showDialog() {
            this.dialogVisible = true;
        },
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.app {
    padding: 50px;
}
</style>