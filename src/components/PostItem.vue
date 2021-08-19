<template>
    <div class="post">
        <div class="post__number"><div>{{post.id}}</div></div>
        <div>
            <div><strong>Название:</strong> {{post.title}}</div>
            <div><strong>Описание:</strong> {{post.body}}</div>
        </div>
        <div class="post__btns">
            <button-item class="post__btn" @click="$emit('remove', post)">Удалить</button-item>
            <button-item class="post__btn" @click="$router.push(`/posts/${post.id}`)">Перейти</button-item>
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
    padding-left: 35px;
    border: none;
    -webkit-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
-moz-box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
box-shadow: 0px 0px 8px 0px rgba(203, 223, 238, 0.2);
}
.post__btns {
    margin-left: 20px;
}
.post__btn + .post__btn {
    margin-top: 15px;
}
.post__number {
margin-left: -35px;
margin-top: -15px;
margin-right: 5px;
    display: flex;
    align-items: center;
    justify-content: center;
    min-width: 30px;
    height: 30px;
    font-size: 12px;
    line-height: 15px;
    color: #fff;
    font-weight: 200;
    background-color: #7dcef7;

}
</style>