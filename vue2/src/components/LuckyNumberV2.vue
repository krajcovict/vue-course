<template>
    <div class="container">
        <div class="col-12 p-10">
            <h4>Random Number Generator V2</h4>
            <button class="btn btn-outline-danger"
            @click="generateLuckyNumber()">
                <span v-if="luckyNumber ===0" class="small">
                    Generate Lucky Number
                    <br>
                    Range (1 - {{ maxNumber }})
                </span>
                <span v-else class="small">
                    Number is {{ luckyNumber }}
                    <br>
                    Click to generate new
                </span>
            </button>
        </div>
    </div>

            
</template>
<script setup>
import { ref, inject } from 'vue';

let luckyNumber = ref(0);

const maxNumber = inject('maxLuckyNumber');

function generateLuckyNumber() {
    luckyNumber.value = Math.floor(Math.random() * maxNumber.value) + 1
};


</script>