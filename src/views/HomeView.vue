<template>
  <main>
    <h1>Test SpinForEat</h1>
    <p>Pour ce test j'ai utilisé un plugin Vue que j'ai déjà utilisé auparavant : <a href="https://www.npmjs.com/package/vue-tel-input" target="_blank" rel="noopener noreferrer">Vue tel input</a></p>
    <p>Le composant <span class="green">PhoneInput.vue</span> contient le code, lorsque le numéro saisi est valide le composant émet l'event <span class="green">phoneData</span> avec les informations du pays detecté</p>
    <PhoneInput @phone-data="setPhoneData" />
    <h2>Data emit par le composant :</h2>
    <span class="green">{{phoneData}}</span>
  </main>
</template>

<script setup>
import { ref } from 'vue';
import PhoneInput from '../components/PhoneInput.vue';
const phoneData = ref({})
/**
 * Fonction appelée lors de l'Event phoneData du composant PhoneInput
 * @param {*} e Data du plugin vue tel input 
 */
function setPhoneData(e) {
  phoneData.value = e
}
</script>

<style scoped>
.green {
  color: #42d392;
}
</style>