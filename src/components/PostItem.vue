<template>
    <div class="post">
        <div>
            <div><strong>Название:</strong> {{post.title}}</div>
            <div><strong>Описание:</strong> {{post.body}}</div>
        </div>
        <div class="post-btn">
            <button-item @click="$emit('remove', post)">Удалить</button-item>
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
    margin-top: 15px;
    padding: 15px;
    border: 2px solid #555585;
    -webkit-box-shadow: 1px 1px 8px 0px rgba(34, 60, 80, 0.2);
    -moz-box-shadow: 1px 1px 8px 0px rgba(34, 60, 80, 0.2);
    box-shadow: 1px 1px 8px 0px rgba(34, 60, 80, 0.2);
}

</style>