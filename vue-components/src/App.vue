<template>
    <div id="app" class="container">
        <h1>Welcome to Vue</h1>
        <div>
            <div v-for="contact in contacts" :key="contact.name">
                <Contact
                    :name="contact.name"
                    :phone="contact.phone"
                    :email="contact.email"
                    :ownername="contact.ownername"
                    :isFavorite="contact.isFavorite"
                    @update-favorite="contact.isFavorite = onUpdateFavorite($event)"
                ></Contact>
            </div>
        </div>
        <ButtonCount></ButtonCount>
    </div>
</template>

<script setup>
import { reactive } from 'vue';
import Contact from './components/Contact.vue';
import ButtonCount from './components/ButtonCount.vue';

const contacts = reactive([
    { 
        name: "Michael", 
        phone: "034789528", 
        email: "bullshitmail@example.com",
        isFavorite: true,
    },
    { 
        name: "Jessica", 
        phone: "00421789023588", 
        email: "jessica@fakemail.com", 
        ownername: "Raincoat Company",
    },
    { 
        name: "Ben", 
        phone: "0123456789",
        isFavorite: true,
    },
]);
function onUpdateFavorite(isFavoriteFromChild) {
    return !isFavoriteFromChild;
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>