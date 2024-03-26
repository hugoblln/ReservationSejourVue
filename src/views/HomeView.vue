<script setup>
import TheFormulaire from '@/components/HomeComponents/TheFormulaire.vue'
import TheImageSejour from '@/components/HomeComponents/TheImageSejour.vue'
import { ref } from 'vue'

let hebergementData = ref({})

const onContinueClickHandler = (data) => {
hebergementData.value = data
}



</script>

<template>
  <main>
    <div class="container">

<div class="row" >
  <TheFormulaire 
  @onContinueClick="onContinueClickHandler"
  />
  <TheImageSejour  
  :hebergement = "hebergementData"
  />

</div>
    </div>
  </main>
  
</template>
