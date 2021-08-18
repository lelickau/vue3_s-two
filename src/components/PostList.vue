<template>
<div v-if="posts.length > 0">
    <h3 class="title">Список постов</h3>
    <transition-group name="post-list">
        <post-item
                v-for="post in posts"
                :post="post"
                :key="post.id"
                @remove="$emit('remove', post)"
                />
    </transition-group>

</div>
<div class="empty" v-else>
    <img class="empty__img" src="../../public/img/alert.svg" alt="alert"/>
    <h3 class="empty__title">Список постов пуст</h3>
</div>

</template>

<script>
import PostItem from './PostItem.vue'

export default {
    components: {
        PostItem,
    },
props: {
    posts: {
        type: Array,
        required: true,
    }
}
}
</script>

<style scoped>
.empty {
    border-radius: 10px;
    padding: 10px 25px;
    background-color: #DDF7EC;
    color: #7DCEF7;
    font-size: 16px;
    line-height: 20px;
    font-weight: 400;
    -webkit-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
-moz-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
display: flex;
align-items: center;
}
.empty__img {
    display: inline-block;
    width: 30px;
    height: 30px;
    margin-right: 20px;
}
.post-list-item {
  display: inline-block;
  margin-right: 10px;
}
.post-list-enter-active,
.post-list-leave-active {
  transition: all .4s ease;
}
.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
.post-list-move {
  transition: transform 0.4s ease;
}
</style>