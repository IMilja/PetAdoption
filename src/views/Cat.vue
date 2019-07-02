<template>
  <div>
    <h2>Cats for adoption</h2>
    <PetTable
    v-bind:animals="cats"
    />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import PetTable from '@/components/PetTable'

export default {
  name: 'Cat',
  data () {
    return {}
  },
  components: {
    PetTable
  },
  computed: {
    ...mapState([
      'cats'
    ])
  }
}
</script>

<style scoped>
</style>
