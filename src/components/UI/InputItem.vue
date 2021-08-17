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
    height: 55px;
    width: 100%;
    margin-top: 10px;
    padding: 5px 10px;
    border: #555585 1px solid;
    border-radius: 10px;
}
</style>