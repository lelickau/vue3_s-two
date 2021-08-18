<template>
    <div class="post">
        <div>
            <div><strong>Название:</strong> {{post.title}}</div>
            <div><strong>Описание:</strong> {{post.body}}</div>
        </div>
        <div class="post-btn">
            <button-item class="post__btn" @click="$emit('remove', post)">Удалить</button-item>
        </div>
    </div>
</template>

<script>

export default {

props: {
    post: {
        type: Object,
        required: true,
    }
}
}
</script>

<style scoped>
.post {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    background-color: #F0FBF7;
    margin-top: 25px;
    padding: 15px;
    border: none;
    -webkit-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
-moz-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
}
.post__btn {
    margin-left: 20px;
}
</style>