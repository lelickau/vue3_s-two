<template>
    <input
        class="input"
        type="text"
        :value="modelValue"
        @input="updateInput"
    />
</template>
<script>
export default {
    name: 'input-item',
    props: {
        modelValue: [String, Number]
    },
    methods: {
        updateInput(e) {
            this.$emit('update:modelValue', e.target.value)
        }
    }
}
</script>

<style scoped>
.input {
    width: 100%;
    height: 35px;
    padding: 5px 10px;
    font-size: 16px;
    line-height: 22px;
    font-weight: 200;
    border: none;
    border-radius: 10px;
    -webkit-box-shadow: 0px 0px 8px 0px rgba(34, 80, 48, 0.2);
-moz-box-shadow: 0px 0px 8px 0px rgba(34, 80, 48, 0.2);
box-shadow: 0px 0px 8px 0px rgba(34, 80, 48, 0.2);
}
</style>