<template>
  <div>
    <h2>{{ animal.name }} ({{ $route.params.species }})</h2>
    <p>Is {{ animal.age }} years old</p>
    <p>Gender: {{ animal.gender }}</p>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'Pet',
  data () {
    return {
      animal: {}
    }
  },
  computed: {
    ...mapState([
      'cats',
      'dogs'
    ])
  },
  mounted () {
    /*
      this[this.$route.params.species][this.$route.params.id]
      this.species['id'] example: this.cats['0'] => return cat from cats with id 0
    */
    this.animal = this[this.$route.params.species][this.$route.params.id]
  }
}
</script>

<style scoped>

</style>
