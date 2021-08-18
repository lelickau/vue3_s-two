<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>
<script>
export default {
    name: 'button-item',
}
</script>

<style scoped>
.btn {
    background: rgb(83,203,168);
    background: linear-gradient(86deg, rgba(83,203,168,1) 0%, rgba(63,211,142,1) 100%);
    border-radius: 25px;
    border: none;
    padding: 10px 20px;
    color: #f3fdf9;
    font-weight: 200;
    font-size: 16px;
    line-height: 18px;
    cursor: pointer;
}
</style>