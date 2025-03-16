<script setup lang="ts">
import { ref } from 'vue'

const name = ref('')

const submitForm = () => {
    alert(`Hello, ${name.value}!`)
}

</script>

<template>
    <div>
        <h1>{{ name }}</h1>    
    </div>
    <div>
        <input type="text" placeholder="Enter your name" v-model="name" />
        <div>
            <button 
            @click="submitForm"
            :disabled="name.length == 0">
                Submit
            </button>
        </div>
    </div>
</template>

<style>
input[type="text"] {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    box-sizing: border-box;
}
button {
    width: 100%;
    background-color: #4CAF50;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    cursor: pointer;
}
button:hover {
    opacity: 0.8;
}
</style>