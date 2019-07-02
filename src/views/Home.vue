<template>
  <div class="home">
    <button v-on:submit="handleSubmit" v-on:click="tooglePetForm" class="btn btn-primary">
      Add new pet
    </button>
    <b-form v-on:submit="handleSubmit" v-if="showPetForm">
      <b-form-group id="petNameGroup" label="Pet's name:" label-for="petName">
        <b-form-input id="petName"
        type="text"
        v-model="pet.name"
        required
        placeholder="Enter pet's name" />
      </b-form-group>

      <b-form-group id="petBreedGroup" label="Pet's breed:" label-for="petBreed">
        <b-form-input id="petBreed"
        type="text"
        v-model="pet.breed"
        required
        placeholder="Enter pet's breed" />
      </b-form-group>

      <b-form-group id="petSpeciesGroup" label="Pet's species:" label-for="petSpecies">
        <b-form-select id="petSpecies"
        v-bind:options="speciesChoice"
        v-model="pet.species"
        required/>
      </b-form-group>

      <b-form-group id="petGenderGroup" label="Pet's gender:" label-for="petGender">
        <b-form-select id="petGender"
        v-bind:options="genderChoice"
        v-model="pet.gender"
        required/>
      </b-form-group>

      <b-form-group id="petAgeGroup" label="Pet's age:" label-for="petAge">
        <b-form-input id="petAge"
        type="number"
        v-model="pet.age"
        required
        placeholder="Enter pet's age" />
      </b-form-group>

      <b-form-group id="petColorGroup" label="Pet's color:" label-for="petColor">
        <b-form-input id="petColor"
        type="text"
        v-model="pet.color"
        required
        placeholder="Enter pet's color" />
      </b-form-group>

      <b-form-group id="petWeightGroup" label="Pet's weight:" label-for="petWeight">
        <b-form-input id="petWeight"
        type="number"
        v-model="pet.weight"
        required
        placeholder="Enter pet's weight" />
      </b-form-group>

      <b-form-group id="petLocationGroup" label="Pet's location:" label-for="petLocation">
        <b-form-input id="petLocation"
        type="text"
        v-model="pet.location"
        required
        placeholder="Enter pet's location" />
      </b-form-group>

      <b-form-group id="petNotesGroup" label="Pet's notes" label-for="petNotes">
        <b-form-textarea 
          id="petNotes"
          v-model="pet.notes"
          placeholder="Enter pet's notes"
          rows="3"
          max-rows="6"
        >
        </b-form-textarea>
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
        breed: '',
        species: '',
        gender: '',
        age: null,
        color: '',
        weight: null,
        location: '',
        notes: ''
      },
      speciesChoice: [
        { text: 'Cat', value: 'cats' },
        { text: 'Dog', value: 'dogs' }
      ],
      genderChoice: [
        { text: 'Female', value: 'female' },
        { text: 'Male', value: 'male' }
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
      const { name, breed, gender, age, color, weight, location, notes, species } = this.pet
      const payload = {
        species,
        pet: {
          name,
          breed,
          gender,
          age,
          color,
          weight,
          location,
          notes
        }
      }
      this.addPet(payload)
      this.pet.name = '',
      this.pet.breed = '',
      this.pet.species = '',
      this.pet.gender = '',
      this.pet.age = null,
      this.pet.color = '',
      this.pet.weight = null,
      this.pet.location = '',
      this.pet.notes = ''
      this.showPetForm = false
    }
  }
}
</script>
