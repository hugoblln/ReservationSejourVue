<script setup>

const props = defineProps({
    hebergement:String
})

</script>

<template>
     <div class="col-4">

<div class="card" style="width: 18rem;">
  <img :src="'src/assets/img/' + hebergement + '.jpg'" class="card-img-top" alt="">
<div class="card-body">
  <h6 class="card-title text-center">150€</h6>
</div>
</div>

</div>
</template>

<style scoped></style>
