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
  display: block;
  margin-left: auto;
  margin-top: 20px;
  background-color: rgb(255, 91, 91);
  border: rgb(252, 114, 114) 1px solid;
  border-radius: 10px;
  padding: 10px;
  color: #fff;
  font-weight: 700;
  cursor: pointer;
}
</style>