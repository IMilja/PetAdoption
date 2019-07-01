<template>
  <div>
    <h2>Dogs for adoption</h2>
    <b-table striped hover :items="dogs">
      <template slot="name" slot-scope="dogs">
        <a :href="`/pets/dogs/${dogs.index}`">{{ dogs.value }}</a>
      </template>
    </b-table>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'Dog',
  data () {
    return {}
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
