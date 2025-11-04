<template>
    <div id="app" class="container text-center bg-light">
        <h1 class="py-3">Welcome to Vue 2</h1>
        
        <div class="py-4 border bg-body-secondary rounded-4">
            Hello
        </div>

        
        <ButtonCount></ButtonCount>

        <div class="col-12 border rounded-4 bg-body-secondary p-4">
            <button class="btn btn-primary"
            @click="newVersion=!newVersion">
                Toggle Component
            </button>
            <br>
            <button class="btn btn-secondary m-2"
            @click="newVersion=false">Lucky Number V1</button>
            <button class="btn btn-secondary m-2"
            @click="newVersion=true">Lucky Number V2</button>
        </div>
        <div class="col-12 py-4">
            <keep-alive>
                <component :is="currentComponent"></component>
            </keep-alive> <!-- cache compponent instance when switchin between components -->
        </div>
        <slot name="mySlot"></slot>
    </div>
</template>

<script setup>
import { reactive, ref, provide, computed } from 'vue';
import ButtonCount from './ButtonCount.vue';
import LuckyNumber from './LuckyNumber.vue';
import LuckyNumberV2 from './LuckyNumberV2.vue';

const maxNumber = ref(100);

provide('maxLuckyNumber', maxNumber);

const newVersion = ref(false);

const currentComponent = computed(() => {
    return newVersion.value ? LuckyNumberV2 : LuckyNumber;
});
</script>

<style scoped>
</style>
