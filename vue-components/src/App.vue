<template>
    <div id="app" class="container text-center bg-light">
        <h1 class="py-3">Welcome to Vue</h1>
        <div class="py-3">Choose maximum for Lucky Number:
            <input class="text-center w-25" v-model.number="maxNumber">
        </div>
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
        <AddContact @add-contact="onAddContact"></AddContact>
        <ButtonCount></ButtonCount>
        <LuckyNumber :max-number=10></LuckyNumber>
        <hr>
    </div>
</template>

<script setup>
import { reactive, ref, provide } from 'vue';
// import Contact from './components/Contact.vue'; component in main.js
import ButtonCount from './components/ButtonCount.vue';
import AddContact from './components/AddContact.vue';
import LuckyNumber from './components/LuckyNumber.vue';

const maxNumber = ref(100);

provide('maxLuckyNumber', maxNumber);

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

function onAddContact(contact) {
    contacts.push(contact);
}

function onUpdateFavorite(isFavoriteFromChild) {
    return !isFavoriteFromChild;
}
</script>

<style>
#app {
    color: #2c3e50;
}
</style>