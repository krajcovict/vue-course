<template>
    <div class="rounded m-2 p-4 bg-info-subtle">
        <div class="row">
            <div class="col-6">
                <h4>Name: {{ name }}</h4>
                <p>Email: {{ email }}</p>
                <p>Phone: {{ phone }}</p>
            </div>
            <div class="col-4">
                <button :class="isFavorite? 'btn btn-warning' : 'btn btn-outline-warning'"
                @click="toggleFavorite">
                    {{ isFavorite? 'Remove from ' : 'Add to ' }}Favorite
                </button>
            </div>
        </div>
        <span class="float-end small" v-if="ownername != null">
            *this contact belongs to: {{ ownername }}
        </span>
    </div>
</template>

<script setup>
import { defineProps, ref } from 'vue';
// const email = ref("ourmail@example.com"); this local variable would have priority over props
const props = defineProps({
    name: { type: String, required: true },
    email: { type: String, required: false, default: "-n/a-"},
    phone: { type: String},
    ownername: { type: String },
    isFavorite: { type: Boolean, default: false },
});

const emit = defineEmits(['update-favorite']);

function toggleFavorite() {
    emit('update-favorite', props.isFavorite);
}
</script>

<style scoped>
/* Styles go here */
</style>