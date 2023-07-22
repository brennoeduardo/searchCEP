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
