<template>
  <div class="home">
    <button v-on:submit="handleSubmit" v-on:click="tooglePetForm" class="btn btn-primary">
      Add new pet
    </button>
    <b-form v-on:submit="handleSubmit" v-if="showPetForm">
      <b-form-group id="petNameGroup" label="Pet name:" label-for="petName">
        <b-form-input id="petName"
        type="text"
        v-model="pet.name"
        required
        placeholder="Enter pet name" />
      </b-form-group>
      <b-form-group id="petSpeciesGroup" label="Pet species:" label-for="petSpecies">
        <b-form-select id="petSpecies"
        v-bind:options="speciesChoice"
        v-model="pet.species"
        required/>
      </b-form-group>
      <b-form-group id="petAgeGroup" label="Pet age:" label-for="petAge">
        <b-form-input id="petAge"
        type="number"
        v-model="pet.age"
        required
        placeholder="Enter pets age" />
      </b-form-group>
      <b-button type="submit" variant="primary">Add</b-button>
    </b-form>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  name: 'home',
  data () {
    return {
      pet: {
        name: '',
        species: '',
        age: null
      },
      speciesChoice: [
        { text: 'Cat', value: 'cats' },
        { text: 'Dog', value: 'dogs' }
      ],
      showPetForm: false
    }
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    tooglePetForm: function () {
      this.showPetForm = !this.showPetForm
    },
    handleSubmit: function (e) {
      e.preventDefault()
      const { name, species, age } = this.pet
      const payload = {
        species,
        pet: {
          name,
          age
        }
      }
      this.addPet(payload)
      this.pet.name = ''
      this.pet.species = null
      this.pet.age = null
    }
  }
}
</script>
