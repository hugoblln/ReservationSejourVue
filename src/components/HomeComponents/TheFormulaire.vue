<script setup>
import { ref } from 'vue'

const nom = ref('')
const prenom = ref('')
const hebergement = ref('default')


let errorMessage = ''

const emit = defineEmits(['onContinueClick'])

const verification = () => {
    if (!nom.value || !prenom.value || hebergement.value === 'default' || !hebergement.value) {
        errorMessage = 'Erreur, merci de sélectionner un hébergement'
    } else {
        errorMessage = ''
        console.log(nom.value,prenom.value,hebergement.value)
    }
}

const hebergementHandler = () => {
    emit('onContinueClick', hebergement.value)
}

const options = () => {
    if (hebergement.value === 'default' || !hebergement.value) {
        return true
    } else {
        return false
    }
}





console.log(nom.value, prenom.value, hebergement.value)

</script>

<template>
    <div class="col-8">
        <div class="card mb-4 shadow-sm">
            <div class="card-header">
                <h4 class="my-0 font-weight-normal">Configurer votre séjour</h4>
            </div>
            <div class="card-body">

                <div class="row mb-2">
                    <div class="col">
                        <input type="text" class="form-control" placeholder="Nom" v-model="nom">
                    </div>
                    <div class="col">
                        <input type="text" class="form-control" placeholder="Prénom" v-model="prenom">
                    </div>
                </div>



                <!-- Select   -->
                <label for="type">Type d'hebergement : </label>
                <select class="custom-select d-btypelock w-100" id="type" v-model="hebergement" @change="hebergementHandler">
                    <option value="default">Choisissez...</option>
                    <option value="tente">Emplacement Tentes</option>
                    <option value="toile">Camp</option>
                    <option value="pierre">Pierre</option>
                </select>

                <hr class="mb-4">
                <!-- Checkboxes button  -->
                <h4 class="my-2">Les options de séjour </h4>
                <div class="custom-control custom-checkbox">
                    <input type="checkbox" class="custom-control-input" name="optionsSejour" value="kayak" id="ok-kayak"
                        :disabled="options()">
                    <label class="custom-control-label" for="ok-kayak">Location Kayak (+30€)</label>
                </div>
                <div class="custom-control custom-checkbox">
                    <input type="checkbox" class="custom-control-input" name="optionsSejour" value="draps" id="ok-draps"
                        :disabled="options()">
                    <label class="custom-control-label" for="ok-draps">Draps (+5€) </label>
                </div>
                <h4 class="mt-3">Petit Déjeuner</h4>

                <div class="d-block my-3">
                    <div class="custom-control custom-radio">
                        <input id="ouiPetitDej" name="petitDej" type="radio" class="custom-control-input"
                            :disabled="options()">
                        <label class="custom-control-label" for="ouiPetitDej">Oui (+10€)</label>
                    </div>
                    <div class="custom-control custom-radio">
                        <input id="nonPetitDej" name="petitDej" type="radio" class="custom-control-input"
                            :checked="options()" :disabled="options()">
                        <label class="custom-control-label" for="nonPetitDej">Non</label>
                    </div>
                </div>
                <div class="alert alert-warning" role="alert">
                    {{ errorMessage }}
                </div>
                <div class='mt-2'>
                    <button id="submitButton" type="button" class="btn btn-lg btn-block btn-primary"
                        @click="verification()">Ok</button>
                </div>

            </div>
        </div>
    </div>
</template>

<style scoped></style>
