<template>
    <div class="container border rounded p-3 my-3">
        <h4>Click Counter</h4>
        <button class="btn btn-secondary" @click="count++">Clicked {{ count }} times</button>
    </div>
</template>
<script setup>
    import { ref } from 'vue';

    const count = ref(0);
</script>
