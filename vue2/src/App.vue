<template>
    <LuckyNumberParentComponent>
            <p>You can choose max number and generate number here.</p>

        <template v-slot:mySlot>
            <div class="rounded bg-warning">Hello, this is slot named "mySlot".</div>
        </template>
    </LuckyNumberParentComponent>
</template>

<script setup>
import LuckyNumberParentComponent from './components/LuckyNumberParentComponent.vue';

</script>

<style>
#app {
    color: #2c3e50;
}
</style>