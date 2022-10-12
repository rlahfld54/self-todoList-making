<template>
    <div style="margin-top: 50px;">
        <h2>Child component</h2>
    </div>
</template>
<script>
export default {
    name: 'Child',
    // declare emitted events
    emits: ['response'],
    created() {
        // emit with argument
        this.$emit('response', '현주')
    },
}
</script>