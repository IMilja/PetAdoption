<template>
  <div>
    <h2>Dogs for adoption</h2>
    <PetTable
    v-bind:animals="dogs"
    />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import PetTable from '@/components/PetTable'

export default {
  name: 'Dog',
  data () {
    return {}
  },
  components: {
    PetTable
  },
  computed: {
    ...mapState([
      'dogs'
    ])
  }
}
</script>

<style scoped>
</style>
