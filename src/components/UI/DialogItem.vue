<template>
<div class="dialog" v-if="show" @click.stop="hideDialog">
    <div @click.stop class="doalog__content">
        <slot></slot>
    </div>

</div>
</template>
<script>
import toggleMixin from '@/mixins/toggleMixin';

export default {
name: 'dialog-item',
mixins: [toggleMixin],

}
</script>

<style scoped>
.dialog {
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background-color: rgba(181, 241, 204, 0.5);
    position: fixed;
    display: flex;
    justify-content: center;
    align-items: center;
}
.dialog__content {
    margin: auto;
    background-color: #fff;
    border-radius: 12px;
    min-height: 50px;
    min-width: 300px;
}
</style>