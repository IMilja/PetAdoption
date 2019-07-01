<template>
  <div>
    <h2>Cats for adoption</h2>
    <b-table striped hover :items="cats">
      <template slot="name" slot-scope="cats">
        <a :href="`/pets/cats/${cats.index}`">{{ cats.value }}</a>
      </template>
    </b-table>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'Cat',
  data () {
    return {}
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
