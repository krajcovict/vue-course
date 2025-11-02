<template>
    <div class="container border rounded bg-danger-subtle p-3 my-3">
        <h4>Add New Contact</h4>
        <form @submit.prevent="addContact">
            <div class="row">
                <div class="col-6 pb-3">
                    <label for="name">Name:</label><br>
                    <input v-model="contact.name" id="name" required />
                </div>
                <div class="col-6 pb-3">
                    <label for="phone">Phone:</label><br>
                    <input v-model="contact.phone" id="phone" required />
                </div>
                <div class="col-6 pb-3">
                    <label for="email">Email:</label><br>
                    <input v-model="contact.email" id="email" type="email" />
                </div>
                <div class="col-6 pb-3">
                    <label for="ownername">Owner Name:</label><br>
                    <input v-model="contact.ownername" id="ownername" />
                </div>
                <div class="col-6 pb-3">
                    <label for="isFavorite">Favorite:</label>
                    <input class="mx-2" v-model="contact.isFavorite" id="isFavorite" type="checkbox" />
                </div>
                <div class="col-12">
                    <button type="submit" class="btn btn-secondary w-100">
                        Add Contact
                    </button>
                </div>
            </div>
        </form>
    </div>

</template>
<script setup>
import { reactive, defineEmits } from 'vue';

const emit = defineEmits(['add-contact']);

const contact = reactive({
    name: "",
    phone: "",
    email: "",
    ownername: "",
    isFavorite: false,
});

function addContact() {
    emit('add-contact', { ...contact });
    // Logic to add the contact
    console.log("Contact added:", contact);
    // Reset the form
    contact.name = "";
    contact.phone = "";
    contact.email = "";
    contact.ownername = "";
    contact.isFavorite = false;
}

</script>