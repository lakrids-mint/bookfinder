<template>
  <v-app>
      <router-view></router-view>
   
  </v-app>
</template>

<script>
import Book from './components/Book'

export default {
  name: 'App',
  components: {
    Book
  },
  data () {
    return {
      //
    }
  }
}
</script>
