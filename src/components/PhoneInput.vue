<!-- eslint-disable prettier/prettier -->

<template>
    <vue-tel-input v-model="phone" @on-input="phoneEvent"></vue-tel-input>
    <p v-if="country != ''">L'indicatif du numéro vient du pays : <span class="country">{{ country }}</span></p>
    <p v-else class="warning">Veuillez saisir un numéro valide</p>
</template>

<script setup>
import { ref } from "vue";
const emit = defineEmits(['phoneData'])
/**
 * 
 * @param string number Le numéro de téléphone
 * @param object phoneObject Un object contenant toute les données du pays
 */
function phoneEvent(number, phoneObject) {
  if (phoneObject.valid) {
    country.value = phoneObject.country.name;
    emit('phoneData', phoneObject)
  } else {
    country.value = ''
    emit('phoneData', {})
  }
}

const phone = ref("");
const country = ref("");
</script>

<style scoped>
.country {
  color: red;
}
.warning {
    color: orange;
}
</style>
