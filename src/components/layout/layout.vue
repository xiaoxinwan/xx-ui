<template>
    <div class="x-layout" :class="layoutClass">
        <slot></slot>
    </div>
</template>

<script>
    export default {
        name: "XLayout",
        data() {
            return {
                layoutClass: {
                    hasSider: false
                }
            }
        },
        mounted() {
            this.$children.forEach((vm) => {
                if (vm.$options.name === 'XSider') {
                    this.layoutClass.hasSider = true
                }
            })
        }
    }
</script>

<style lang="scss" scoped>
    .x-layout{
        flex-grow: 1;
        display: flex;
        flex-direction: column;
        &.hasSider{
            flex-direction: row;
        }
    }
</style>
