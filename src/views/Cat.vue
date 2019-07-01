<template>
  <div>
    <h2>Cats for adoption</h2>
    <b-table striped hover :items="cats">
      <template slot="name" slot-scope="cats">
        <a :href="`/pets/${cats.index}`">{{ cats.value }}</a>
      </template>
    </b-table>
  </div>
</template>

<script>
import cats from '@/data/cats.js'

export default {
  name: 'Cat',
  data () {
    return {
      cats
    }
  }
}
</script>

<style scoped>
</style>
