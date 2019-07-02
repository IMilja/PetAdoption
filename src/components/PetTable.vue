<template>
  <div id="pet-table">
    <b-table striped hover :items="animals">
      <template slot="name" slot-scope="animals">
        <a :href="`/pets/dogs/${animals.index}`">{{ animals.value }}</a>
      </template>
    </b-table>
  </div>
</template>
<script>

export default {
  name: 'PetTable',
  props: {
    animals: []
  }
}
</script>

<style lang="scss">

</style>
