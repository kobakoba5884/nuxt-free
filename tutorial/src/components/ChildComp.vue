<script setup>

const emit = defineEmits(['response'])

emit('response', 'hello from child')

</script>

<template>
    <h2>child component</h2>
</template>