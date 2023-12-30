<template>
  <v-app>
    <v-main>
      <CEP/>
    </v-main>
  </v-app>
</template>

<script>
import CEP from './components/CEP.vue'

export default {
  name: 'App',

  components: {
    CEP
  },

  data: () => ({
    //
  }),
}
</script>

<style scoped>

* {
  background: url('./assets/city2.jpg') no-repeat center center fixed;
  background-size: cover;
}

</style>